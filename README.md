Die Lösung des dritten Rätsels entspricht den Buchstaben **ab** in den Koordinaten unserer Unterkunft:  
Breitengrad: ab° cd' ef.g''  
Längengrad: hi° jk' lm.n''
 
# 🕵️ Rätsel 3 
 
Auf dem Weg zur Sternfrucht müsst ihr eine Seilbrücke überqueren. Die Seilbrücke knarrt, wenn man sie überquert. Du bist dir nicht sicher, wie alt sie ist, oder ob sie überhaupt dein Gewicht tragen kann. Die Elfen scheint sie jedoch gut zu tragen. Du machst einen vorsichtigen Schritt, dabei dehnen und verdrehen sich die Seile. Du beschließt, dich abzulenken, indem du die Seilphysik nachstellst - vielleicht kannst du sogar herausfinden, wo du nicht hintreten solltest.
 
Stell dir ein Seil mit einem Knoten an jedem Ende vor. Diese Knoten markieren den Anfang (Head) und das Ende (Tail) des Seils. Wenn sich der Anfangsknoten weit genug vom Endknoten entfernt, wird der Endknoten zum Kopfknoten gezogen. Deine Aufgabe ist es nun die Positionen der Knoten auf einem zweidimensionalen Gitter zu modellieren. Indem du eine hypothetische Reihe von Bewegungen für den Head-Knoten verfolgen, kannst du bestimmen, wie sich der Tail-Knoten bewegen wird.
 
Das Seil ist recht kurz. Head-Knoten (H) und Tail-Knoten (T) müssen sich immer berühren (diagonal nebeneinander liegende und sogar überlappende Knoten gelten als berührend):

```
....
.TH.
....

....
.H..
..T.
....

...
.H. (H überdeckt T)
...
```

Im letzten Beispiel liegt der Head-Knoten über dem Tail-Knoten.
 
Wenn der Head-Knoten immer zwei Schritte direkt nach oben, unten, links oder rechts vom Tail-Knoten entfernt ist, muss sich der Tail-Knoten auch einen Schritt in diese Richtung bewegen, damit er nah genug bleibt:
```
.....      .....      .....
.TH..  ->  .T.H.  ->  ..TH.
.....      .....      .....

...         ...        ...
.T.         .T.        ...
.H.   ->    ...   ->   .T.
...         .H.        .H.
...         ...        ...
```


Andernfalls, wenn Head-Knoten und Tail-Knoten sich nicht berühren und nicht in der gleichen Zeile oder Spalte sind, bewegt sich der Tail-Knoten immer einen Schritt diagonal, um Schritt zu halten:
```
.....      .....      .....
.....      ..H..      ..H..
..H..  ->  .....  ->  ..T..
.T...      .T...      .....
.....      .....      .....
                          
.....      .....      .....
.....      .....      .....
..H..  ->  ...H.  ->  ..TH.
.T...      .T...      .....
.....      .....      .....
```

Du musst herausfinden, wohin der Tail-Knoten geht, wenn der Head-Knoten einer Reihe von Bewegungen folgt. Gehe davon aus, dass Head und Tail an der gleichen Stelle beginnen und sich überlappen.
 
Zum Beispiel:
 ```
R 4
U 4
L 3
D 1
R 4
D 1
```

Diese Bewegungsfolge bewegt den Head-Knoten vier Schritte nach rechts (R), dann vier Schritte nach oben (U), dann drei Schritte nach links (L), dann einen Schritt nach unten (D) und so weiter. Nach jedem Schritt musst du die Position des Tail-Knotens aktualisieren, wenn der Schritt bedeutet, dass der Kopf-Knoten nicht mehr neben dem Tail-Knoten liegt. Optisch sehen diese Bewegungen wie folgt aus (s markiert die Ausgangsposition als Referenzpunkt):


```
==== Ausgangszustand ====

......
......
......
......
H.....  (H überdeckt T und s)

==== R 4 ====

......
......
......
......
TH....  (T überdeckt s)

......
......
......
......
sTH...

......
......
......
......
s.TH..

......
......
......
......
s..TH.

==== U 4 ====

......
......
......
....H.
s..T..

......
......
....H.
....T.
s.....

......
....H.
....T.
......
s.....

....H.
....T.
......
......
s.....

==== L 3 ====

...H..
....T.
......
......
s.....

..HT..
......
......
......
s.....

.HT...
......
......
......
s.....

==== D 1 ====

..T...
.H....
......
......
s.....

==== R 4 ====

..T...
..H...
......
......
s.....

..T...
...H..
......
......
s.....

......
...TH.
......
......
s.....

......
....TH
......
......
s.....

==== D 1 ====

......
....T.
.....H
......
s.....

==== L 5 ====

......
....T.
....H.
......
s.....

......
....T.
...H..
......
s.....

......
......
..HT..
......
s.....

......
......
.HT...
......
s.....

......
......
HT....
......
s.....

==== R 2 ====

......
......
.H....  (H überdeckt T)
......
s.....

......
......
.TH...
......
s.....
```


Nachdem du das Seil simuliert hast, kannst du alle Positionen aufzählen, die der Tail-Knoten mindestens einmal besucht hat. In diesem Diagramm markiert s wieder die Startposition (die der Tail-Knoten auch besucht hat) und # markiert andere Positionen, die der Tail-Knoten besucht hat:

```
..##..
...##.
.####.
....#.
s###..
```

Es gibt also 13 Positionen, die der Tail-Knoten mindestens einmal besucht hat.
