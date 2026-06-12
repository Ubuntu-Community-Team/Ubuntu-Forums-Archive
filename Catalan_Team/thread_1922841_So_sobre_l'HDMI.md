---
title: "So sobre l'HDMI"
date: 2012-02-09
forum: Catalan Team
---

### Post by rrubi on 2012-02-09
Hola, ubuntaires!

Aquest és el meu primer post, i després d'haver-me empapat totes les advertències i demés, encara no estic segur d'haver-lo penjat al lloc adequat...


Estic utilitzant l'Ubuntu 11.10 i tinc el PC connectat a una pantalla de televisió a través del port HDMI.
El problema és que no trobo la manera d'obtenir so a través dels altaveus de la pantalla.

Puc veure que l'Ubuntu reconeix la tarja (GF106 High Definition Audio Controller), però només puc escoltar a través dels auriculars connectats a un jack (que sembla estar en una altra tarja - Internal Audio).


Salut!

---

### Post by wgarcia on 2012-02-10
Has mirat si pots canviar a la targeta de so que vol clicant sobre la icona de so al plafó superior -> Paràmetres de so -> Maquinari?

---

### Post by rrubi on 2012-02-10
Si vaig allà on m'indiques, hi puc veure dues targes de so (t'adjunto la captura).

A cada una de les targes em deixa escollir diferents opcions, ja les he provat i no n'hi ha cap que faci funcionar el so per l'HDMI.

No se si te res a veure, però potser el problema està més en la tarja de vídeo (on hi ha l'HDMI) que no pas en la de so... 

(Nova Edició)
Efectivament, he estat remenant i als Paràmetres del Sistema trobo que no té els drivers de la tarja de Video.

Ara doncs, si aquesta és una possible raó, com ho soluciono?

(Nova Edició)
Vaig aprenent; he picat la comanda lscpi a terminal i obtinc això per la taja de vídeo i la de so:

01:00.0 VGA compatible controller: nVidia Corporation Device 0dc6 (rev a1)
01:00.1 Audio device: nVidia Corporation GF106 High Definition Audio Controller (rev a1)

Encara no entenc un borrall de tot això dels drivers i companyia, però he trobat això en un altre post:
> **prostata said:**
> He trobat aquesta pàgina i he fet el següent:

Terminal
Sudo lspci -n
El resultat ho pegat a la pàgina
Comprovar

I el resultat ha estat que: 10de0a65        nVidia Corporation    GT218  [GeForce 210] aquest dispositiu no en te controlador ni kernel....

La pàgina és [http://kmuto.jp/debian/hcl/index.rhtmlx](http://kmuto.jp/debian/hcl/index.rhtmlx)

I el resultat que obtinc és nul. No em dóna cap resposta sobre la tarja gràfica. Com si no existís...

---

### Post by wgarcia on 2012-02-10
Sí que troba la targeta de vídeo, segons el que enganxes del resultat de "lspci". 

Ara hauries de comprovar si tens instal·lat el controlador propietari de Nvidia per la teva targeta. Mira a "Paràmetres de sistema" (opció del menú que trobes a l'última icona del plafó superior), secció "Maquinari", opció "Controladors addicionals", i mira si tens disponible el controlador propietari i si està instal·lat i funcionant.

---

### Post by rrubi on 2012-02-10
Ho acabo de mirar. A controladors addicionals no troba res.

(Edito de nou)
He estat remenant i he trobat els drivers a la web de Nvidia. 
Quan els he baixat em trobo que tenen l'extensió .run; he trobat en algun forum que cal executa-los des de terminal amb l'ordre:
$ sudo sh ./<archivo>.run

Quan ho faig em retorna un error. Diu que es troba un X server funcionant i que l'haig d'aturar.
Les instrucions que he trobat per negociar amb l'X server em superen per molt.

He rebuscat també pel Centre de Software i em trobo que qualsevol paquet que contingui 'nvidia' no el puc instal·lar perque no el troba entre les meves fonts de software.


Com haig de continuar?


(Editant de nou)
[FONT=Arial Narrow][SIZE=1]
[SIZE=2]Bé, doncs, finalment la cosa s'ha acabat solucionant:

[/SIZE][/SIZE][/FONT]  [FONT=Arial Narrow][SIZE=2]He trobat aquestes comandes per pode[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]r afegir la font de paquets i instal·lar el driver: ([en aquesta web]("http://konsciencon.blogspot.com/2010/11/ubuntu-drivers-nvidia-v2601921.html"))[/SIZE][/FONT][INDENT]**sudo add-apt-repository ppa:ubuntu-x-swat/x-updates**[/INDENT][INDENT]**sudo apt-get update**[/INDENT][INDENT][B]sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
[FONT=Arial]
[/FONT][/B][/INDENT][FONT=Arial Narrow][SIZE=2]En reiniciar l'ordinador ja m'apareix el driver als 'Controladors Addicionals', però no a la opció de Grafics dels 'Paràmetres del Sistema/Informació del Sistema'.
[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2] De tota manera, ja puc escoltar a la pantalla a través de l'HDMI!![/SIZE][/FONT]
[FONT=Ubuntu] 
[FONT=Arial Narrow][SIZE=2]Bé, doncs, gràcies a wgarcia i a la resta d'usuaris que fan útils aquests fòrums! [/SIZE][/FONT]
[/FONT][INDENT][FONT=Ubuntu] 
[/FONT][/INDENT]

---

