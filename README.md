# INF.04 Aplikacje konsolowe

❗ | Więcej informacji na https://zawodowe.it 

## Lista snippetów

| Snippet              | Opis                             |
| ---------------------| -------------------------------- |
| `inf04-bubblesort`   | Sortowanie bąbelkowe             |
| `inf04-countingsort` | Sortowanie przez zliczanie       |
| `inf04-mergesort`    | Sortowanie przez scalanie        |
| `inf04-insertionsort`| Sortowanie przez wstawianie      |
| `inf04-quicksort`    | Szybkie sortowanie               |
| `inf04-binarysearch` | Wyszukiwanie binarne             |
| `inf04-nwd`          | Największy wspólny dzielnik      |
| `inf04-nww`          | Najmniejsza wspólna wielokrotność|
| `inf04-silnia`       | Silnia                           |
| `inf04-potega`       | Potęga                           |
| `inf04-pierwsza`     | Czy liczba jest pierwsza         |

> Uwaga: Każdy z podanych snippetów zwraca wartość.

Przykładowe użycie snippeta:
```py
print(wyszukaj_binarnie([1,2,3,4,5,6], 3))      # 2
print(sortowanie_babelkowe([4,6,1,2]))          # [1, 2, 4, 6]
print(sortowanie_przez_wstawianie([4,6,1,2]))   # [1, 2, 4, 6]
print(sortowanie_przez_zliczanie([4,6,1,2]))    # [1, 2, 4, 6]
print(sortowanie_szybkie([4,6,1,2]))            # [1, 2, 4, 6]
print(nwd(10, 5))                               # 5
print(nww(25, 10))                              # 50
print(czy_pierwsza(23))                         # True
print(potega(4, 3))                             # 64
```
## Przykładowe zadania


<details>
<summary> Przeszukiwanie tablicy z wartownikiesm</summary>

```py
import random # Importowanie modułu "random"

tablica = [] # Zdefiniowanie pustej tablicy

print("Program dodaje do tablicy 50 losowych liczb w zakresie 1-100 i sprawdza czy liczba podana przez użytkownika znajduję się w tablicy")

def wypelnijTablice(): # Funkcja wypełniająca tablice losowymi wartościami
    for i in range(50):
        tablica.append(random.randint(1, 100)) # Dodanie do tablicy losowej wartości z przedziału 1-100


# **************
# nazwa funkcji: szukaj
# argumenty: szukana - int
# typ zwracany: int
# informacja: funkcja sprawdza czy podana liczba znajduje się w tablicy
# autor: <numer zdającego>
# **************
def szukaj(szukana): # Funkcja szukająca podanej liczby w tablicy
    tablica.append(szukana)

    for index, wartosc in enumerate(tablica): # Pętla przechodząca przez wartości tabllicy
        print(wartosc)
        if wartosc == szukana:
            print(tablica)
            if index == len(tablica)-1:
                print("Nie znaleziono szukanej liczby w wylosowanej tablicy")
            else:
                print(f"Szukana liczbę znaleziono na indexie: {index}")
            return index

szukana = int(input("Podaj szukaną liczbę: ")) # Pobieranie od użytkownika wartości i konwertowanie jej na inta

wypelnijTablice()

szukaj(szukana)
```
</details>

---

<details>
<summary> Klasa "Osoba"</summary>

```py
class Osoba:
    licznik = 0 # pole statyczne

    def __init__(self, id = 0, imie = ""): # Konstruktor z dwoma parametrami, który przyjmuje domyślne wartości
        self.__id = id
        self.__imie = imie
        Osoba.licznik += 1 # inkrementacja licznika w momencie wywołania konstruktora

    # Metoda kopiująca dane z jednego obiektu do drugiego
    def kopiuj(self, obiekt):
        self.__id = obiekt.__id
        self.__imie = obiekt.__imie

    # Metoda wypisująca
    def wypisz(self, argument):
        if self.__imie == "":
            print("Brak danych")
        else:
            print(f"Cześć {argument}, mam na imie {self.__imie}")
```
Test klasy

```py
print(f"Liczba zarejestrowanych osób to: {Osoba.licznik}")

osoba1 = Osoba()
osoba2 = Osoba(1, "Dawid")
osoba3 = Osoba()
osoba3.kopiuj(osoba2)

osoba1.wypisz("Jan")
osoba2.wypisz("Jan")
osoba3.wypisz("Jan")

print(f"Liczba zarejestrowanych osób to: {Osoba.licznik}")
```
</details>

---

<details>
<summary>Sortowanie przez wybieranie</summary>

```py
class Sortowanie:

    def wczytaj_tablice(self):
        """Pyta użytkownika o 10 liczb całkowitych i zapisuje je do tablicy"""
        print("Wprowadz 10 liczb calkowitych:")
        self.tablica = [int(input()) for _ in range(10)]

    def szukaj_maksimum(self, start):
        """Znajduje indeks maksymalnej liczby w tablicy od pozycji 'start' do końca tablicy"""
        max_val = self.tablica[start]
        max_index = start
        for i in range(start + 1, len(self.tablica)):
            if self.tablica[i] > max_val:
                max_val = self.tablica[i]
                max_index = i
        return max_index

    def sortuj(self):
        """Sortuje tablicę metodą przez wybieranie. Dla każdego indeksu 'i' od 0 do 9, znajduje maksymalną liczbę w reszcie tablicy i zamienia ją z liczbą na pozycji 'i'"""
        for i in range(len(self.tablica) - 1):
            max_index = self.szukaj_maksimum(i)
            self.tablica[i], self.tablica[max_index] = self.tablica[max_index], self.tablica[i]

# tworzenie obiektu klasy Sortowanie
sort = Sortowanie()
# wczytanie tablicy od uzytkownika
sort.wczytaj_tablice()
# sortowanie tablicy
sort.sortuj()
# wyswietlenie posortowanej tablicy
print("Posortowana tablica: ", sort.tablica)
```
</details>