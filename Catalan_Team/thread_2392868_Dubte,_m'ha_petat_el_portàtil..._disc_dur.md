---
title: "Dubte, m'ha petat el portàtil... disc dur ?"
date: 2018-05-26
forum: Catalan Team
---

### Post by Txaume on 2018-05-26
Bones.

M'ha petat el portàtil, suposo que és el disc dur....

He pogut entrar al grub, però no passo d'allà, diría que haig de canviar el disc dur,..

Què en penseu ? 
[IMG]https://imageshack.com/i/pocpJnyZj[/IMG]

---

### Post by wgarcia on 2018-05-27
Si és sols un sector danyat, encara es pot fer servir l'ordinador. Pel missatge que tens sembla com si hi hagi hagut la mala sort que el sector danyat estigui justament en el lloc on estan instal·lats els fitxers d'arrencada. Si fos en un altre lloc, el sistema arrencaria i es podria executar una netejada de disc.

En tot cas, pots provar el següent:

1) Arrenca el sistema amb un USB autònom ("life").

2) Inicia l'Ubuntu en mode de prova ("Try Ubuntu")

3) Instal·la i inicia l'aplicació "testdisk":

```

sudo apt-get update

sudo apt-get install -y testdisk && sudo testdisk

```

4) Fes servir el testdisk:
 
Navega al menú "[No log", tria el disc amb la partició danyada, tria "[Proceed]", tria el tipus de partició (en general "[Intel]"), després "[Advanced]", i després selecciona la partició trencada amb "[Boot]"

```

 [  List  ]  [Backup BS]  [Rebuild BS]  [  Dump  ]

```

Mira que hi hagi "Status ok" a sota de "Backup boot sector" i tria "[Backup BS]".


Font: [https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)

---

### Post by Txaume on 2018-05-27
He probat amb un USB amb Ubuntu i tampoc arranca, em surt la mateixa pantalla...

---

### Post by wgarcia on 2018-05-28
Estàs segur que està arrencant des de l'USB? Té tota la pinta de continuar arrencant des del disc dur.

---

### Post by Txaume on 2018-05-29
Hola, al final a arrencat amb el USB, però no troba el testdisk...

[IMG]https://imageshack.com/a/img921/4086/8mZv7J.jpg[/IMG]

En l'aplicació que porta ja hem diu que el disc està cascat : 
[IMG]https://imageshack.com/a/img921/6748/q2ENTR.jpg[/IMG]

Miraré si trobo una altra aplicació per reparar el disc, si no serà el moment de canviar-lo per un ssd...

Gracies per tot company !!

---

### Post by wgarcia on 2018-05-30
Perdona, m'he oblidat que a la sessió autònoma (life) no està habilitat el dipòsit "universe" on hi és el "testdisk". Per habilitar aquest dipòsit, simplement entra l'ordre següent:

```
sudo add-apt-repository universe
```

---

