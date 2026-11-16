# Notatki

## notatki z wprowadzenia

`dde27` -- delayed differential equation. da się z tego skożystać, ale wg prowadząceog to nie jest najlepsze rozwiązanie. wg prowadzącego najlepiej zaimplementować swoją metodę numeryczną sięgając do wczesniejszych elementów wektora
[matlab help center](https://www.mathworks.com/help/matlab/ref/dde23.html)

### Optymalizacja

Przykład w matlabie

```matlab
clearvars
% fminseach -- szuka jakiegoś minimum

f = @(x) cos(x);
fminsearch(f, 1) % szuka jakieś minimum wzgledme punktu startowego

f = @(x) cos(x(1)) + cos(x(2) - 0.4);
fminsearch(f, [1, 1])
fminsearch(f, 1); % szuka jakieś minimum wzgledme punktu startowego
```

```matlab
clearvars

x = linspace(0, 2, 20);
y - exp(-2 * x);

figure(1)
plot(x, y, "-o");

f @(x, a) exp(a * x);

J = @(a) sum( (f(x, a)) - y).^2);

interp -- matlabowa funkcja do interpolacji

% dla ode45 można też tak, bez staraty dokładności
% w środku jest to jakoś interpolowane

t = lisnspace(0, 2, 300);
[~, y] = ode45(f, t, y0);

fminsearch( )
```

Jeśli dopasowanie na oko jest w miarę mizerne, to trzeba znaleźć najlepsze
dopasowanie, dobrze opsiać i może będą jakieś punkty. Zanim jednak się
załamieny, warto jest najpierw zweryfikować dokładność metody rozwiązywania równań.

### Skąd wziąć punkt startowy

- można zacząć od systematycznego przeszukiwania. Tworzymy siadkę punktów wybierając uprzednio rozsądne wartości. Warto zajrzeć do artykułów w źródłach i np na wikipedii aby wydedukować dobry zakres wartości. Potem po minimalizacji fminsearch.
- w każdym równaniu warto też spojrzeć na wartości rozsądne z perspektywy fizyki i zdrowego rozsądku (np tętno powinno być koło 1Hz).
- na podstawie jakiś otrzymanych danych można też napisać program który oszacuje na podstawie tych danych jakiś punkt startowy.

## Sprawy organizacyjne

- Projekt nie musi być robiony w matlabie, może być python (bo są też jakieś bibliotetki do numerycznych) (ej, robimy w ruscie? (albo chociaż w C)).
- Sprawozdania mają być na onedrive zespołowym [tutaj](https://outlook.cloud.microsoft/host/377c982d-9686-450e-9a7c-22aeaf1bc162/7211f19f-262a-42eb-a02e-289956491741).
- Za tydzień mamy przyjść omówić jakąś metodykę rozwiązania. W zespole po mału mamy określić jakiś zamysł. W razie czego możemy liczyć na naprowadzanie.
- Za dwa tygodnie przyjść mamy z wynikami (mogą być wstępne, najlepiej wszystkie).
- Za dwa tygodnie + eps trzeba wstawić rozwiązanie.
- Sprawozdanie najlepiej w LaTeX (biorę to na siebie hihi).
- Godziny konsulatacji są dostępne [tutaj](https://wutwaw.sharepoint.com/:x:/r/sites/5968E722-5E40-4270-BE20-551A1ECBF1B7.teams_d54462/_layouts/15/doc2.aspx?action=edit&sourcedoc=%7B3b0f49df-5409-460d-981f-ab4743882542%7D&wdExp=TEAMS-TREATMENT&web=1).

### Jak dbać w matlabie o spójność symboli?

```matlab
xlabel('t1', FontSize24)
xlabel('t_1', FontSize24)
xlabel('{\iit}t1', FontSize24)
% albo nawet lepiej!
xlabel('$t_1$', FontSize24, Interpreter='latex')

```
