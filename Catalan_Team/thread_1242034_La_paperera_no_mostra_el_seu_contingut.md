---
title: "La paperera no mostra el seu contingut"
date: 2009-08-16
forum: Catalan Team
---

### Post by jinglada on 2009-08-16
Involuntàriament he mogut una quinzena de fitxers a la paperera. 

1) Obro la paperera per recuperar-los, triga una mica a obrir-se i no mostra cap fitxer. Poso el punter del ratolí damunt de la icona i diu "41 elements a la paperera" 

2) Obro les propietats clicant damunt del botó Paperera de la barra de direccions i diu: Contingut: 64 elements, de mida total 3,1 GB

3) Com a root vaig a /home/.Trash-0/files, selecciono tots els fitxers i diu: 11 carpetes seleccionades (contenen 77 elements), 115 altres elements seleccionats (30,2 MB). Però els 15 fitxers que volia recuperar no hi són.

Sembla estrany tot plegat.

---

### Post by papapep on 2009-08-16
La paperera d'un usuari és a /home/usuari/.local/share/Trash.
Aquí dins hi hauries de trobar dos directoris més, un de nom files, i un de nom info. Al primer tindràs els fitxers enviats a la paperera, i al segon, info, un fitxer per a cada fitxer esborrat amb la informació de quan es va esborrar i quina era la seva ubicació original.

---

### Post by jinglada on 2009-08-17
> **papapep said:**
> La paperera d'un usuari és a /home/usuari/.local/share/Trash.Aquí dins hi hauries de trobar dos directoris més, un de nom files, i un de nom info. Al primer tindràs els fitxers enviats a la paperera, i al segon, info, un fitxer per a cada fitxer esborrat amb la informació de quan es va esborrar i quina era la seva ubicació original.

Gràcies, ja he recuperat els fitxers perduts. Anant a l'adreça que dius, papapep, hi trobo els dos directoris que esmentes i un altre que s'anomena "expunged" que està buit. Al directori "files" efectivament, hi he trobat el contingut que jo deia en els punts 1) i 2), que són fitxers esborrats des del dia 10/8, com consta al directori "info", última vegada que vaig buidar la paperera clicant al damunt de la icona i obrit la paperera al navegador de fitxers, com sempre he fet. 

El que no entenc és que, des de fa 3 o 4 dies, clicant a la icona de la paperera, l'obra amb el navegador de fitxers, però no mostra cap contingut i a la barra de baix a l'esquerra diu "0 elements" quan realment n'hi ha 64, de mida total 3,1 GB. Clicant el "Quant a" de la icona amb el botó dret del ratolí diu: Miniaplicació de Paperera 2.26.1. Potser s'ha espatllat alguna cosa d'aquesta miniaplicació? Podria ser que no suportés aquesta mida tan gran de brossa?

Si vaig anar al directori /home/.Trash-0/files va ser perquè cercant "paperera" al fòrum vaig trobar aquesta adreça de directori d'una versió anterior de l'Ubuntu en un fil antic i vaig decidir mirar-ho. El que és estrany és que els fitxers que hi he trobat són esborrats el dia 5/8/2009. Com és que han anat a parar aquí i no a la paperera del Jaunty?

---

### Post by indiosincracia on 2009-08-17
És possible que els hagis borrat en mode superusuari?

---

### Post by jinglada on 2009-08-17
> **indiosincracia said:**
> És possible que els hagis borrat en mode superusuari?

El dia 5/8/09 és possible que operés amb el Nautilus, havent entrat amb Alt+F2 i "gksu nautilus", ja que estava copiant fitxers d'un disc extern procedent d'un ordinador antic del que no podia fer-me propietari.
Això voldria dir que en mode superusuari no utilitza la paperera habitual?

---

### Post by papapep on 2009-08-17
La teoria és molt simple i entenedora: seguretat.

Si el teu ordinador tingués 5 usuaris a més del root, a quina paperera haurien d'anar els fitxers esborrats per aquest? Fins i tot és possible que l'administrador que entra com a root no tingui un compte "normal" a l'ordinador. 
Davant del dubte, **cada** usuari té una paperera pròpia :)

---

### Post by jinglada on 2009-08-17
> **jinglada said:**
> El que no entenc és que, des de fa 3 o 4 dies, clicant a la icona de la paperera, l'obra amb el navegador de fitxers, però no mostra cap contingut i a la barra de baix a l'esquerra diu "0 elements" quan realment n'hi ha 64, de mida total 3,1 GB. Clicant el "Quant a" de la icona amb el botó dret del ratolí diu: Miniaplicació de Paperera 2.26.1. Potser s'ha espatllat alguna cosa d'aquesta miniaplicació? Podria ser que no suportés aquesta mida tan gran de brossa?

Clicant amb el botó dret damunt la icona de la paperera he seleccionat "Buida la paperera" i m'ha mostrat l'avís que podia esborrar parcialment (mentida, perquè no em permetia veure el directori). He tirat pel dret i m'ha buidat els 3,1 GB. 

Previament m'havia copiat el fitxer "files" de /home/usuari/.local/share/Trash. He anat esborrant parcialment el directori copiat per anar comprovant l'accés mitjançant la icona i ara amb els 3,1 Gb esborrats ja m'obre la paperera al navegador mitjançant la icona.

Misteris de la informàtica...???

---

