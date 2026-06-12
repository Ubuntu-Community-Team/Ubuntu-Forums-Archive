---
title: "[ydpdict] &quot;Nie mo na otworzy pliku indeksowego&quot; error message"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-04-02
Hi, 
  
(sorry for few words non english)
   
I followed the procedure to install the program.
but get this  "Nie mo na otworzy pliku indeksowego" error message
  
Someone knows how to fix it ??

thank you veyr much

Dzienki

Patrick

procedure:[http://www.linux.sky.pl/teksty/ydp.html](http://www.linux.sky.pl/teksty/ydp.html)
> Konfiguracja

Zanim uruchomimy s&#322;ownik musimy go skonfigurowa&#263; oraz przegra&#263; bazy danych z windowsowej wersji S&#322;ownika YDP. Tworzymy dowolny katalog np. /opt/ydp/database i kopiujemy do niego pliki z partycji windowsowej o nazwach dict*.dat i dict*.idx. Gwiazdka oznacza, &#380;e jest wiele plików *.dat i *.idx (w tym wypadku po dwa). Wydajemy polecenia:
	cp /dos/WinProg/Ydp/database/dict*.dat /opt/ydp/database
cp /dos/WinProg/Ydp/database/dict*.idx /opt/ydp/database

# Oczywi&#347;cie dopasowujemy w&#322;asne &#347;cie&#380;ki. 	

Mo&#380;na omin&#261;&#263; poprzedni punkt i poda&#263; &#347;cie&#380;k&#281; do baz danych na partycji windowsowej, ale wtedy dost&#281;p do nich b&#281;dzie kilkakrotnie wolniejszy ni&#380; do partycji ext2 je&#380;eli nadal pracujemy na j&#261;drach serii 2.0.X!

Warto doda&#263;, &#380;e przy instalacji pakietu rpm pojawia si&#281; program ydpdict-setup, który próbuje znale&#378;&#263; orginalne pliki s&#322;ownika na dost&#281;pnych w systemie partycjach. Aby go wywo&#322;a&#263; wydaj polecenie:
	ydpdict-setup 	

Je&#347;li instalowali&#347;my program z rpm`a to plikiem konfiguracyjnym jest /etc/ydpdict.conf, je&#347;li ze &#380;róde&#322;ek to ydpdict.conf znajduj&#261;cy si&#281; w tym samym katalogu co binaria programu. Oto opcje tego pliku:
	# &#346;cie&#380;ka, w której znajduj&#261; si&#281; pliki s&#322;ownika.
Path /opt/ydp/database

# &#346;cie&#380;ka, gdzie znajduje si&#281; podmontowany CD-ROM ze s&#322;ownikiem.
# U&#380;ywane do odtwarzania próbek d&#378;wi&#281;kowych.
CDPath /mnt/cdrom

# Zestaw znaków, z którego korzysta program: None (bez polskich
# liter), ISO-8859-2 (polskie litery), Unicode (polskie litery
# i transkrypcja fonetyczna przy odpowiedniej czcionce). Mo&#380;na te&#380;
# u&#380;y&#263; parametru UnicodeSet, a wtedy program sam prze&#322;&#261;czy konsol&#281;
# w tryb UTF-8.
Charset ISO-8859-2

# Wprawdzie program potrafi wykrywac czy terminal obsluguje kolory
# czy nie, to jednak mozna wymusic ich wyswietlanie lub ich brak.
UseColor On

# By zmieni&#263; kolory wy&#347;wietlanego tekstu nale&#380;y zmieni&#263; poni&#380;sze
# warto&#347;ci na jedne z nast&#281;puj&#261;cych: Black, Red, Green, Brown, Blue,
# Magenta, Cyan, White, Gray, LightRed, LightGreen, Yellow, LightBlue,
# LightMagenta, LightCyan, LightWhite. Nale&#380;y zwrócic uwag&#281;, &#380;e dla
# kolorów z przedrostkiem "Light" pogrubienie tekstu nie b&#281;dzie widoczne.

# Kolor tekstu
Color White

# Kolor definicji
DefinitionColor LightCyan

# Kolor drugiego wyroznienia (np. czesc mowy, rodzaj)
InformationColor LightGreen

	

Gdy ustawimy poprawnie plik konfiguracyjny mo&#380;emy wywo&#322;a&#263; program poleceniem
	ydpdict
# wtedy dostaniemy s&#322;ownik angielsko-polski

ydpdict -p
# gdy zapodamy powy&#380;sze, uruchomimy s&#322;ownik polsko-angielski

	



---

### Post by patrick295767 on 2006-04-08
Found with some help that I thank a lot : 
  
the problem was that the files have to be lowercase and you should have then: 
```
/opt/ydp/database$ ls -la
total 11960
drwxr-xr-x  2 root root    4096 2006-04-08 21:44 .
drwxr-xr-x  3 root root    4096 2006-04-02 19:45 ..
-rwxr-xr-x  1 root root 6389018 2006-04-02 19:46 dict100.dat
-rwxr-xr-x  1 root root  465714 2006-04-02 19:46 dict100.idx
-rwxr-xr-x  1 root root 4876978 2006-04-02 19:46 dict101.dat
-rwxr-xr-x  1 root root  470984 2006-04-02 19:46 dict101.idx
```

Greetz 

Solved !!

---

### Post by patrick295767 on 2006-04-08
my config of /etc/ydpdict.conf
  
```

# cieka prowadzca do plik&#65533; sownika. Uwaga: dost&#65533; do plik&#65533;
# umieszczonych na partycji FAT lub VFAT jest w wypadku jder 2.0.x znacznie
# wolniejszy ni do plik&#65533; na partycji EXT2.

#Path /usr/local/share/ydpdict

Path /opt/ydp/database

# cieka prowadzca do katalog&#65533; z pr&#65533;kami dwi&#65533;owymi.

CDPath /mnt/cdrom

# cieka do programu odtwarzajcego pr&#65533;ki dwi&#65533;owe (play lub mpg321).
# Jeeli nie jest ustawiona, program pr&#65533;uje sam odtworzy&#65533;pr&#65533;ki.

#Player play
#Player mpg321

# Zestaw znak&#65533;, z kt&#65533;ego korzysta program: None (bez polskich liter),
# ISO-8859-2 (polskie litery), Unicode (polskie litery i transkrypcja
# fonetyczna przy odpowiedniej czcionce). Mona te uy&#65533;parametru UnicodeSet,
# a wtedy program sam przeczy konsol&#65533;w tryb UTF-8.

Charset ISO-8859-2

# Wprawdzie program potrafi wykrywa&#65533; czy terminal obsuguje kolory czy nie,
# to jednak mona wymusi&#65533;ich wywietlanie lub ich brak.

UseColor On

# Tryb z przezroczystym tem lub bez

UseTransparent On

# By zmieni&#65533;kolory wywietlanego tekstu naley zmieni&#65533;ponisze wartoci
# na jedne z nast&#65533;ujcych: Black, Red, Green, Brown, Blue, Magenta, Cyan,
# White, Gray, Yellow, LightRed, LightGreen, LightBlue, LightMagenta,
# LightCyan, LightWhite. Uwaga: dla kolor&#65533; z przedrostkiem "Light"
# pogrubienie tekstu nie b&#65533;zie widoczne.

# Kolor tekstu

Color White

# Kolor definicji

DefinitionColor LightCyan

# Kolor drugiego wyr&#65533;ienia (np. cz&#65533; mowy, rodzaj)

InformationColor LightGreen
winwood@tower05:/etc$ cat /etc/ydpdict.conf
# cieka prowadzca do plik&#65533; sownika. Uwaga: dost&#65533; do plik&#65533;
# umieszczonych na partycji FAT lub VFAT jest w wypadku jder 2.0.x znacznie
# wolniejszy ni do plik&#65533; na partycji EXT2.

#Path /usr/local/share/ydpdict
#Path /home/nfs_work/sharedwindowsapps/YDPDict/Database
Path /opt/ydp/database

# cieka prowadzca do katalog&#65533; z pr&#65533;kami dwi&#65533;owymi.

CDPath /mnt/cdrom

# cieka do programu odtwarzajcego pr&#65533;ki dwi&#65533;owe (play lub mpg321).
# Jeeli nie jest ustawiona, program pr&#65533;uje sam odtworzy&#65533;pr&#65533;ki.

#Player play
#Player mpg321

# Zestaw znak&#65533;, z kt&#65533;ego korzysta program: None (bez polskich liter),
# ISO-8859-2 (polskie litery), Unicode (polskie litery i transkrypcja
# fonetyczna przy odpowiedniej czcionce). Mona te uy&#65533;parametru UnicodeSet,
# a wtedy program sam przeczy konsol&#65533;w tryb UTF-8.

Charset ISO-8859-2

# Wprawdzie program potrafi wykrywa&#65533; czy terminal obsuguje kolory czy nie,
# to jednak mona wymusi&#65533;ich wywietlanie lub ich brak.

UseColor On

# Tryb z przezroczystym tem lub bez

UseTransparent On

# By zmieni&#65533;kolory wywietlanego tekstu naley zmieni&#65533;ponisze wartoci
# na jedne z nast&#65533;ujcych: Black, Red, Green, Brown, Blue, Magenta, Cyan,
# White, Gray, Yellow, LightRed, LightGreen, LightBlue, LightMagenta,
# LightCyan, LightWhite. Uwaga: dla kolor&#65533; z przedrostkiem "Light"
# pogrubienie tekstu nie b&#65533;zie widoczne.

# Kolor tekstu

Color White

# Kolor definicji

DefinitionColor LightCyan

# Kolor drugiego wyr&#65533;ienia (np. cz&#65533; mowy, rodzaj)

InformationColor LightGreen

```

---

### Post by patrick295767 on 2006-04-08
```
 luit -encoding iso-8859-2 ydpdict
Warning: couldn't find charset data for locale en_US.UTF-8; using ISO 8859-1.

[1]+  Stopped                 luit -encoding iso-8859-2 ydpdict
```
  


killall -9 -e ydpdict
killall -9 -e luit
  
then,
start a fresh konsole : 
konsole & 
and type : 
      luit -encoding iso-8859-2 ydpdict
 
should be working ... !!

Great program !!

---

### Post by patrick295767 on 2006-04-09
It's working !!
  
I made a how to there : [http://www.ubuntuforums.org/showthread.php?p=904385#post904385](http://www.ubuntuforums.org/showthread.php?p=904385#post904385)

Greetz

---

