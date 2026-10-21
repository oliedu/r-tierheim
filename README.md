# r-tierheim

Hi Leute,

da Moodle für mich nicht erreichbar ist und ich weiter üben wollte, habe ich hier ein paar Übungsaufgaben erstellt. Bitte sagt mir Bescheid, falls etwas unklar ist oder falls ihr einen Fehler vermutet. Es ist nicht einfach, einen passenden Schwierigkeitsgrad zu finden, aber ich hoffe, es ist für alle etwas dabei.

## Aufgabe 1: Datensatz importieren

Lade die Datei `hunde.txt` [hier](https://drive.google.com/file/d/1SDusWl4yW4IuhA1tldsla80khNHlOV3D/view?usp=sharing) herunter und importiere sie anschließend über "Import Dataset" in RStudio.

<details>
  <summary>Lösung</summary>

1. Klicke auf `Import Dataset`
2. Wähle `From text (base)...` aus
3. Überprüfe im geöffneten Fenster, ob die Daten korrekt dargestellt werden. Die Vorschau sollte ungefähr so aussehen:
   ![Import Dataset](/assets/01_import_dataset.png 'Import Dataset')

4. Klicke auf `Import`

</details>

## Aufgabe 2: Namen

Gib alle Namen der Hunde aus. Verwende dafür einen passenden R-Befehl.

<details>
  <summary>Lösung</summary>

Befehl:

```
hunde$name
```

Ergebnis:

```
 [1] "Bella"     "Rocky"     "Luna"      "Benni"     "Maja"      "Buddy"     "Lilly"     "Balu"      "Nala"      "Sam"       "Emma"      "Max"       "Frieda"
[14] "Oskar"     "Hercules"  "Teddy"     "Amy"       "Kalle"     "Susi"      "Finn"      "Ronja"     "Willi"     "Lotte"     "Charly"    "Kira"      "Friedrich"
[27] "Daisy"     "Benno"     "Cookie"    "Anton"     "Zora"      "Henry"     "Paula"     "Benny"     "Flocke"    "Theo"      "Coco"      "Aron"      "Mimi"
[40] "Luna"      "Wilma"     "Fiete"     "Zuma"      "Moritz"    "Sally"     "Jack"      "Frida"     "Balou"     "Holly"     "Otto"
```

</details>

## Aufgabe 3: Anzahl Hunde

Wie viele Hunde leben im Tierheim? Versuche zunächst, die Anzahl direkt in der Benutzeroberfläche von RStudio zu finden.

Alternativ kannst du die Funktion `nrow()` verwenden. Falls du sie noch nicht kennst, kannst du dir mit `?nrow` die Dokumentation anzeigen lassen.

<details>
  <summary>Tipp</summary>

Option 1: Du kannst in RStudio im Reiter "Environment" rechts oben die Anzahl der Zeilen des Dataframes `hunde` sehen.

Option 2: Du kannst die Funktion `nrow()` verwenden und `hunde` als Argument an `nrow()` übergeben.

</details>

<details>
  <summary>Lösung</summary>

Option 1:
![Anzahl Hunde](/assets/02_rows_and_columns.png 'Anzahl Hunde')

Option 2:

Befehl:

```
nrow(hunde)
```

Ergebnis:

```
50
```

</details>

## Aufgabe 4: Größe im Durchschnitt und Median

Wie groß sind die Hunde im Durchschnitt und im Median?

Tipp: Benutze die Funktionen `mean()` und `median()`.

<details>
  <summary>Lösung</summary>

Befehl:

```
mean(hunde$groesse)
```

Ergebnis:

```
45.4
```

Befehl:

```
median(hunde$groesse)
```

Ergebnis:

```
47
```

</details>

## Aufgabe 5: Fehlende Rassenbezeichnung

Finde heraus, ob es Hunde gibt, bei denen die Spalte `rasse` einen fehlenden Wert hat.

Tipp: Verwende die Funktion `anyNA`.

<details>
  <summary>Lösung</summary>

Befehl:

```

anyNA(hunde$rasse)

```

Lösung:

```

TRUE

```

</details>

## Aufgabe 6: Namen der Junghunde

Alex möchte die Namen aller Junghunde im Tierheim wissen. Für diese Aufgabe gelten Hunde unter drei Jahren als Junghunde.

<details>
  <summary>Tipp</summary>

Wir verwenden sogenanntes _Subsetting_, um einen Teil des Dataframes `hunde` auszuwählen:

```

hunde[REIHEN, SPALTEN]

```

Ersetze REIHEN und SPALTEN durch passende Bedingungen oder Angaben, um die gewünschten Daten auszuwählen.

</details>

<details>
  <summary>Lösung</summary>

Befehl:

```

hunde[hunde$alter_jahre < 3, "name"]

```

Ergebnis:

```

[1] "Luna" "Buddy" "Sam" "Hercules" "Kalle" "Lotte" "Friedrich" "Henry" "Flocke" "Wilma" "Jack" "Holly"

```

</details>

## Aufgabe 7: Kinderfreundliche Hündinnen

Die Familie Adebayo möchte eine _Hündin_ adoptieren, die möglichst kinderfreundlich ist. Die Spalte `kinderfreundlichkeit` enthält Werte von 1 bis 3. Je höher der Wert, desto souveräner ist der Hund im Umgang mit Kindern.

Erstelle einen Befehl, der nur die _Hündinnen_ zurückgibt, die den Wert `3` bei der Spalte `kinderfreundlichkeit` haben.

<details>
  <summary>Tipp</summary>

Wir verwenden sogenanntes _Subsetting_, um einen Teil des Dataframes `hunde` auszuwählen:

```

hunde[REIHEN, SPALTEN]

```

Ersetze REIHEN und SPALTEN durch passende Bedingungen oder Angaben, um die gewünschten Daten auszuwählen.

Mit dem Operator `&` können logische Bedingungen verknüpft werden.

</details>

<details>
  <summary>Lösung</summary>

Befehl:

```

hunde[hunde$geschlecht == "w" & hunde$kinderfreundlichkeit == 3, ]

```

Ergebnis:

```

     name               rasse alter_jahre geschlecht kastriert groesse tage_im_tierheim bewegungsbedarf kinderfreundlichkeit hunde_vertraeglichkeit

1 Bella Labrador 4 w TRUE 55 23 3 3 3
3 Luna Mischling 2 w FALSE 38 12 2 3 3
5 Maja Dackel 9 w TRUE 25 104 2 3 2
7 Lilly Golden Retriever 6 w TRUE 53 31 2 3 3
9 Nala Beagle 8 w TRUE 36 73 2 3 3
11 Emma Pudel 5 w TRUE 32 14 2 3 3
17 Amy Labrador 7 w TRUE 56 64 2 3 3
19 Susi Dackel 11 w TRUE 24 183 1 3 2
21 Ronja Australian Shepherd 5 w TRUE 49 49 3 3 3
23 Lotte Beagle 2 w FALSE 34 11 2 3 3
27 Daisy Golden Retriever 9 w TRUE 54 141 2 3 3
29 Cookie Pudel 3 w FALSE 31 2 2 3 3
33 Paula <NA> 7 w TRUE 38 97 2 3 3
35 Flocke Malteser 1 w FALSE 22 7 2 3 2
37 Coco Mischling 10 w TRUE 35 132 1 3 2
40 Luna Labrador 8 w TRUE 50 110 2 3 3
41 Wilma Mischling 2 w FALSE 40 18 3 3 2
43 Zuma Golden Retriever 3 w FALSE 52 21 3 3 3
45 Sally Dackel 5 w TRUE 26 44 2 3 2
49 Holly Labrador 2 w FALSE 51 15 3 3 3

```

</details>

## Aufgabe 8: Neue Spalte: `ist_kinderfreundlich`

Für diese Aufgabe gelten Hunde mit einem Wert von mindestens `2` in der Spalte `kinderfreundlichkeit` als kinderfreundlich.

Erstelle eine neue Spalte namens `ist_kinderfreundlich`. Sie soll den Wert `"ja"` enthalten, wenn der Hund als kinderfreundlich gilt, und andernfalls den Wert `"nein"`.

Tipp: Verwende die Funktion `ifelse()`.

<details>
  <summary>Lösung</summary>

Befehl:

```

hunde$ist_kinderfreundlich <- ifelse(hunde$kinderfreundlichkeit >= 2, "ja", "nein")

```

Ergebnis:

Du kannst mit folgenden Befehlen überprüfen, ob die Spalte richtig erstellt wurde:

```

sum(hunde$ist_kinderfreundlich == "ja")

```

Dieser Befehl sollte `42` zurückgeben.

```

sum(hunde$ist_kinderfreundlich == "nein")

```

Dieser Befehl sollte `8` zurückgeben.

</details>
