# Microsoft 365 & Entra ID Test Lab - Projekt Helpdesk

## Zarządzanie kontami użytkowników (Onboarding i Offboarding)

**Cel projektu:** Chciałem sprawdzić w praktyce, jak wygląda pełny cykl życia konta pracownika na Helpdesku – od momentu jego utworzenia, przez zabezpieczenie, aż po bezpieczne zablokowanie przy zwolnieniu (offboarding). Całość zrealizowałem w testowym środowisku Microsoft Entra ID oraz Exchange Online.

**Opis działań (Onboarding):** Utworzyłem nowe konto użytkownika (Jan Kowalski) w panelu Microsoft Entra ID. Zadbałem o poprawne wypełnienie danych (m.in. Stanowisko i Dział), żeby zachować porządek w strukturze (higiena Active Directory). Po przypisaniu lokalizacji (Usage Location - Polska), nadałem pracownikowi licencję Microsoft 365 Business Premium, dając mu dostęp do usług.

---

## Bezpieczeństwo i weryfikacja MFA

Aby zwiększyć bezpieczeństwo konta, wymusiłem dla tego użytkownika korzystanie z uwierzytelniania wieloskładnikowego (MFA). Następnie zalogowałem się na stworzone konto przez tryb Incognito, żeby przetestować z perspektywy pracownika, czy blokada działa poprawnie i czy system faktycznie prosi o dodatkową weryfikację.

---

## Bezpieczne zwolnienie pracownika (Offboarding)

Przeprowadziłem symulację zwolnienia pracownika, starając się trzymać dobrych praktyk pierwszej linii wsparcia. Skupiłem się na zabezpieczeniu danych firmy i zachowaniu dostępu do maili dla menedżera. Proces podzieliłem na 3 kroki:

1. Natychmiastowe zablokowanie logowania w Entra ID i wylogowanie ze wszystkich aktywnych sesji (Revoke sessions).
2. Przejście do Exchange Admin Center i konwersja zwykłej skrzynki na Skrzynkę Udostępnioną (Shared Mailbox). Następnie nadałem uprawnienia "Pełny dostęp" (Read and manage) dla konta menedżera, żeby zachować ciągłość kontaktu z klientami.
3. Usunięcie licencji M365 w Entra ID. Skrzynka udostępniona jej nie wymaga, więc dzięki temu firma nie płaci za niepotrzebną subskrypcję.

---

## Konfiguracja przestrzeni do pracy w Microsoft Teams

**Opis działań:** Stworzyłem od podstaw nowy, prywatny zespół o nazwie "Dział Marketingu Polska". Chciałem przećwiczyć zarządzanie uprawnieniami, więc podzieliłem go na odpowiednie kanały: zostawiłem domyślny kanał "Ogólny" do komunikacji całego działu, dodałem kanał standardowy ("Projekty Graficzne") oraz utworzyłem chroniony, prywatny kanał ("Zarząd") z przypisanym dostępem tylko dla konta dyrekcji (ochrona danych wrażliwych).

---

## Udostępnianie plików na zewnątrz (SharePoint)

**Opis działań:** Przetestowałem, jak bezpiecznie wysłać firmowy plik do kogoś spoza organizacji. Z poziomu połączonej z Teams witryny SharePoint użyłem opcji "Określone osoby", wpisując konkretny, zewnętrzny adres e-mail. Dzięki temu plik jest chroniony – nawet jeśli link trafi w niepowołane ręce, wymaga on zalogowania się dokładnie tym jednym, wskazanym adresem.

---

## Tworzenie prostej instrukcji dla użytkowników (Baza Wiedzy)

**Cel zadania:** Chciałem pokazać, że potrafię przygotować krótką i zrozumiałą instrukcję krok po kroku dla osoby nietechnicznej, co jest częstym zadaniem na pierwszej linii wsparcia.

**Scenariusz:** Załóżmy, że menedżer zgłasza się do IT z prośbą o dostęp do maili zwolnionego pracownika. Jako administrator nadałem mu już odpowiednie uprawnienia, a teraz wysyłam krótką instrukcję, jak ma samodzielnie dodać tę skrzynkę w swoim przeglądarkowym Outlooku.

### Instrukcja: Jak dodać skrzynkę udostępnioną w Outlook on the Web (OWA)

#### Krok 1: Logowanie i znalezienie opcji dodawania skrzynki
1. Zaloguj się do poczty firmowej w przeglądarce, wchodząc na stronę: `outlook.office.com`.
2. Spójrz na lewy panel nawigacyjny. Poszukaj głównego nagłówka swojej skrzynki (najczęściej to Twój adres e-mail lub imię i nazwisko, zaraz pod zakładką "Ulubione").
3. Kliknij ten nagłówek prawym przyciskiem myszy.
4. Z menu, które się rozwinie, wybierz **Dodaj udostępniony folder lub skrzynkę pocztową** (Add shared folder or mailbox).

![Menu kontekstowe w Outlooku z podświetloną opcją dodawania udostępnionej skrzynki](images/zrzut1.png)

#### Krok 2: Wyszukiwanie odpowiedniej skrzynki
1. Na ekranie pojawi się małe okienko wyszukiwania. Wpisz imię i nazwisko osoby, której skrzynkę chcesz dodać (np. Jan Kowalski) lub jej adres e-mail. 
2. Wybierz odpowiednią osobę z listy podpowiedzi i kliknij przycisk **Dodaj** (Add).

![Okienko wyszukiwania z wpisanym nazwiskiem Jan Kowalski](images/zrzut2.png)

#### Krok 3: Sprawdzenie dostępu
Gotowe! Skrzynka zwolnionego pracownika pojawi się na samym dole lewego panelu jako osobna pozycja. Możesz ją rozwinąć, klikając małą strzałkę obok nazwy, żeby zobaczyć wiadomości odebrane i wysłane z tego konta.

![Lewy panel Outlooka z podpiętą i rozwiniętą skrzynką Jana Kowalskiego](images/zrzut3.png)
