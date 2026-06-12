---
title: "[SOLVED] .metacity"
date: 2007-08-18
forum: Catalan Team
---

### Post by grundt on 2007-08-18
Ostres, he esborrat la carpeta .metacity al voler esborrar aquelles carpetes de programes que ja no faig servir (sabeu, les que estan ocultes).
Ara al iniciar , després de posar nom i contrassenya no es veu res,
bé es veu tot del color crema de l'ubuntu.
Tinc el disc dur particionat xp per un costat i ubuntu per l'altre.
Hi ha alguna manera de recuperar-lo??
Ho puc fer desde l'xp?
Ho puc fer dese la terminal?

---

### Post by papapep on 2007-08-18
Si l'has esborrat des de l'entorn gràfic potser el tinguis a la paperera. Si ho has fet des d'el terminal....ja l'has vist prou.

---

### Post by CarlesOriol on 2007-08-18
Prova d'entrar per linia de comandes ctr+alt+f1 i crear un altre usuari adduser.
Tornes al mode gràfix (gdm) ctrl+alt+f7
I entrant amb aquest segur que et serà més fàcil recuperar l'anterior.

---

### Post by grundt on 2007-08-18
Hey, merci

Ho vaig esborrar desde la paperera.

He provat de fer alt+ctrl+f1
però em diu que només el superusuari pot crear un usuari nou.

---

### Post by papapep on 2007-08-18
Això et passa perquè intentes fer tasques administratives sense prous drets. Un dels punts forts de linux és la seva estructura i funcionament a nivell de seguretat.
Per a tenir, temporalment, drets d'administrador, tecleja en un terminal:

```
sudo useradd -m nom_del_nou_usuari
```

I, per cert, si el vas enviar a la paperera, has de tenir la carpeta .metacity dins el directori /home/teu_usuari/.Trash

Si el treus d'allà i la tornes a posar al seu lloc:

```
sudo mv /home/teu_usuari/.Trash/.metacity/   /home/teu_usuari
```

en teoria l'hauries de recuperar.

---

### Post by grundt on 2007-08-18
Ok,

com engego la terminal?

---

### Post by papapep on 2007-08-18
El que et surt a Ctrl+Alt+F1 ja n'és un. En tens a totes les tecles de funció fins F6.

---

### Post by grundt on 2007-08-18
Hola de nou,
he teclejat les ordres per moure-ho de lloc pero diu que no ho troba,
Diu algo com: cannot stat.. existing file or directory

Com ho puc fer per veure que hi ha a la carpeta .Thrash?

He creat un nou user, amb la mateixa contrasenya, i a l'hora d'entrar em diu que son incorrectes...

---

### Post by papapep on 2007-08-18
Hi ha dues opcions:

1) No tecleges exactament el que cal (tranquil, això ens ha passat a tots).

2) La carpeta ja no és a la paperera (directori .Trash) i, per tant, no el troba.

En tot cas, per a poder-te ajudar ens has de posar **exactament** què has posat tu i, també, **exactament **què et contesta l'ordinador. Sinó podem estar perdent el temps vílment per algun missatge que per a tu pot no significar res, però a nosaltres ens donaria pistes valuoses.

Per entendre algunes coses, crec que et seria interessant fer-li un cop d'ull a un petit tutorial de l'intèrpret d'ordres que tenim aquí: [http://tinyurl.com/3drv2e](http://tinyurl.com/3drv2e)

---

### Post by grundt on 2007-08-18
Bé, jo he posat 
l'ordre per moure la carpeta

sudo mv /home/el meu usuari/.Trash/.metacity/   /home/el meu usuari

i em diu

mv:ha fallat stat() [COLOR="Black"]sobreUN SIGNE COM AQUEST PERO VERTICAL[/COLOR]¬/home/el meu usuari/.Thrash/.metacity [COLOR="black"]UN SIGNE COM AQUEST PERO VERTICAL I COM UNA F[/COLOR]¬ :No such file or directory

---

### Post by papapep on 2007-08-19
Bé doncs, lamento dir-te que la carpeta que vas esborrar no és a la paperera.

Si fas un :

```
ls -la  /home/el_teu_usuari/.Trash/
```

Veuràs com no t'hi sortirà la carpeta ".metacity".

---

### Post by grundt on 2007-08-19
Doncs és veritat.

Que puc fer??

Torno a instalar l'Ubuntu?

---

### Post by CarlesOriol on 2007-08-19
fes el que t'he comentat.

(canviant adduser -> useradd . mea culpa)

---

### Post by grundt on 2007-08-19
Ok,
he entrat fent alt+ctrl+f1
i he escrit
sudo useradd -m nouusuari
si torno a alt+ctrl+f7 des d'allà segueixo sense poder fer res.

Lavors quan reinicio intento entrar amb el nom nou pero amb la contrasenya antiga , i em diu que son incorrectes o el nom o la contrassenya.

---

### Post by papapep on 2007-08-19
Un cop has creat un usuari li has d'assignar contrassenya, des d'un terminal:

```
sudo passwd nou_usuari
```

(Et demanarà dos cops la contrassenya)

Després, entres com aquest usuari a l'entorn gràfic i amb la contrassenya que li has dit t'ha de deixar entrar.

Per cert, per reiniciar el servidor gràfic (que et torni a demanar usuari i contrassenya sense haver de reiniciar tot l'ordinador) pots fer Ctrl+Alt+Backspace (la tecla que tens damunt l'Enter)

---

### Post by grundt on 2007-08-19
Vaja, doncs he pogut entrar com el nou usuari,
però segueixo veient-ho tot de color crema , el puntero del ratolí i ja està.

---

### Post by papapep on 2007-08-19
Això ha surtit alguna altra vegada i no tenim ben bé clar, al menys jo, quin és el problema.

Podries començar executant a un terminal:

```
gnome-panel &
```

Si no et funciona, prova això altre:

```
sudo apt-get install --reinstall gnome-panel
```

---

### Post by grundt on 2007-08-19
quan he teclejat 

gnome panel & 
m'ha dit:
-bash :gnome: command not found

quan li he teclejat
sudo apt-get install --reinstall gnome-panels
em diu:
llegint llista paquets -Fet
construint arbre dependencies -Fet
Reading state information -Fet
E: no s'ha pogut trobar el paquet panels
[1]+Ext 127    gnome panel

---

### Post by papapep on 2007-08-19
> quan he teclejat

gnome panel &
m'ha dit:
-bash :gnome: command not found

És que no has posat el guió entre gnome i panel. Les ordres són estrictes, un caràcter de més o de menys significa que funcionin o no.

Respecte la segona ordre que t'he indicat, sobra la "s" després de "panel", i, evidentment, també porta guió entre "gnome" i "panel".

---

### Post by grundt on 2007-08-20
he teclejat

gnome-panel &

i m'ha suggerit que escrigui 

sudo apt-get install gnome-panel

sembla que ha funcionat

despres he teclejat

sudo apt-get install  --reinstall gnome-panel

sembla que ha funcionat

Però estic amb lo mateix, reinicio i s'em queda tot color crema.

---

### Post by CarlesOriol on 2007-08-20
Em sembla que vas fer alguna cosa més seriosa que el sol fet que esborressis el .metacity. No entenc que no tinguis el gnome-panel instalat.

fes 

sudo apt-get install ubuntu-desktop

---

### Post by grundt on 2007-08-20
Això SI  m'ha funcionat,

merci sou uns cracks.

:guitar:

---

