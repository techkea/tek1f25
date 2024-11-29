# ASCII, ISO-8859, Unicode

De tre begreber, **ASCII**, **ISO-8859** og **Unicode**, er alle tegnkodninger, der bruges til at repræsentere tekst i computere. Forskellen mellem dem ligger i deres omfang, struktur og anvendelse. 

---

### **ASCII (American Standard Code for Information Interchange)**
- **Definition**: ASCII er en af de tidligste tegnkodninger, udviklet i 1960'erne.
- **Omfang**: Kan kun repræsentere 128 tegn, hvilket inkluderer:
  - Engelsk alfabet (store og små bogstaver: A-Z og a-z).
  - Tal (0-9).
  - Nogle specialtegn (f.eks. `@`, `#`, `%`).
  - Kontroltegn (f.eks. `newline`, `tab`).
- **Begrænsning**: ASCII er begrænset til engelsk og kan ikke håndtere tegn fra andre sprog, som f.eks. danske bogstaver `æ`, `ø`, `å`.
- **Eksempel**: Tegnet "A" repræsenteres som tallet 65 i ASCII.

---

### **ISO-8859 (International Organization for Standardization - 8859)**
- **Definition**: ISO-8859 er en udvidelse af ASCII, udviklet for at understøtte flere sprog og tegn.
- **Omfang**:
  - ISO-8859-1 (også kaldet **Latin-1**) tilføjer yderligere 128 tegn (samlet 256 tegn).
  - Disse ekstra tegn inkluderer europæiske bogstaver som `æ`, `ø`, `å` og accenterede bogstaver som `é`, `è`.
  - Der findes andre varianter af ISO-8859 (f.eks. -2, -5), som understøtter forskellige regionale tegnsæt.
- **Begrænsning**: Kan stadig ikke repræsentere alle verdens sprog eller komplekse tegn som emoji.
- **Eksempel**: Tegnet "Æ" repræsenteres som 198 i ISO-8859-1.

---

### **Unicode**
- **Definition**: Unicode er et universelt tegnsæt, designet til at repræsentere alle verdens skriftsprog og specialtegn.
- **Omfang**:
  - Unicode kan repræsentere over 1,1 millioner tegn, herunder bogstaver, symboler, emojis og tegn fra sprog som kinesisk, arabisk, hindi, osv.
  - Unicode implementeres gennem forskellige kodningsformer som:
    - **UTF-8**: En variabel længde kodning, hvor almindelige tegn (som engelske bogstaver) bruger 1 byte, men komplekse tegn bruger flere bytes.
    - **UTF-16**: En anden kodning med 2 eller 4 bytes pr. tegn.
- **Fordel**: Unicode er den mest fleksible og standardiserede løsning i dag.
- **Eksempel**: Emoji "😀" har koden U+1F600 i Unicode.

---

### **Sammenligningstabel**

| **Egenskab**        | **ASCII**             | **ISO-8859**       | **Unicode**           |
|----------------------|-----------------------|--------------------|-----------------------|
| **Tegnsæt**         | 128 tegn             | 256 tegn          | 1.1 millioner tegn   |
| **Sprogunderstøttelse** | Kun engelsk         | Europæiske sprog   | Alle sprog           |
| **Kompleksitet**    | Simpel               | Udvidet ASCII      | Meget kompleks       |
| **Moderne brug**    | Sjældent             | Faldende          | Udbredt (standard)   |

---

**Konklusion**:
- Hvis du kun arbejder med engelsk tekst, er **ASCII** ofte tilstrækkeligt.
- Til europæiske sprog er **ISO-8859** bedre, men det er forældet i dag.
- **Unicode** er den moderne standard og den bedste løsning, fordi det understøtter alle sprog og specialtegn.

### **ASCII, ISO-8859 og Unicode i relation til binære tal**

Computere lagrer og behandler data som **binære tal** (sekvenser af 0'er og 1-taller). Tegnkodninger som **ASCII**, **ISO-8859** og **Unicode** fungerer som oversættelsestabeller, der konverterer tegn til binære værdier, som computeren kan forstå.

#### **ASCII**
- **Binær repræsentation**: Hvert tegn i ASCII er repræsenteret af et 7-bit binært tal.
  - F.eks.:
    - Tegnet `A` har ASCII-værdien 65, som i binær er `1000001`.
    - Tegnet `a` har ASCII-værdien 97, som i binær er `1100001`.
- ASCII kan kun bruge 7 bits, hvilket begrænser det til 128 tegn (2⁷ = 128).

---

#### **ISO-8859**
- **Binær repræsentation**: ISO-8859 bruger 8 bits (1 byte) pr. tegn, hvilket giver mulighed for 256 forskellige tegn (2⁸ = 256).
  - Dette ekstra bit giver plads til at repræsentere tegn fra europæiske sprog, som f.eks. `ø`, `å` og `é`.
  - F.eks.:
    - Tegnet `Æ` har ISO-8859-1-værdien 198, som i binær er `11000110`.

> **Bemærk**: Fordi ISO-8859 er en udvidelse af ASCII, har tegnene fra 0-127 i ISO-8859 de samme binære repræsentationer som i ASCII.

---

#### **Unicode**
- **Binær repræsentation**: Unicode er designet til at kunne repræsentere millioner af tegn. Det bruger forskellige kodningsformer (f.eks. UTF-8, UTF-16) til at oversætte tegn til binære værdier:
  - **UTF-8**:
    - Bruger en variabel længde, fra 1 til 4 bytes (8-32 bits).
    - F.eks.:
      - Tegnet `A` (almindeligt engelsk bogstav) bruger 1 byte: `01000001`.
      - Tegnet `æ` (dansk bogstav) bruger 2 bytes: `11000011 10100110`.
      - Emoji `😀` bruger 4 bytes: `11110000 10011111 10011000 10000000`.
  - **UTF-16**:
    - Bruger 2 eller 4 bytes pr. tegn (16-32 bits).
    - F.eks. emoji `😀` repræsenteres som `11011000 00000001 11011111 10000000`.

> Unicode bruger et **kodenummer** (code point), der repræsenteres som `U+XXXX` (hvor XXXX er en hexadecimaltal). Dette kodenummer oversættes derefter til binær i den valgte kodning (f.eks. UTF-8).

---

### **Relation til binær databehandling**
1. **Lagring i hukommelsen**:
   - Når tekst gemmes i RAM eller på persistent lager, lagres hver tegns binære værdi.
   - F.eks. teksten "Hej" (i UTF-8):
     - `H` → `01001000`
     - `e` → `01100101`
     - `j` → `01101010`

2. **Overførsel over netværk**:
   - Når data sendes over internettet, repræsenteres tegnene som binære strømme.
   - Unicode, især UTF-8, bruges ofte, fordi det er pladsbesparende for almindelig tekst.

3. **Fortolkning af data**:
   - Når binære data skal vises som tekst, bruger computeren den korrekte tegnsætoversættelse (f.eks. ASCII eller Unicode) for at konvertere binære værdier tilbage til læsbare tegn.

---

### **Konklusion**
- **ASCII**: Simpel og direkte binær oversættelse, 7 bits pr. tegn.
- **ISO-8859**: Udvider ASCII til 8 bits, så flere tegn kan repræsenteres.
- **Unicode**: En fleksibel og global løsning, der bruger variabel længde kodning for at repræsentere millioner af tegn i binær form.