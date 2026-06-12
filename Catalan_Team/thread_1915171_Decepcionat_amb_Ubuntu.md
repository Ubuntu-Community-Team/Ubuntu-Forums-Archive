---
title: "Decepcionat amb Ubuntu"
date: 2012-01-25
forum: Catalan Team
---

### Post by xaviman on 2012-01-25
Hola a tothom,

Soc nou amb el mon Ubuntu, però vaig començar amb molta il·lusió i se m'han passat una mica (forces!). M'explico.
Sempre  havia volgut ficar-me amb Linux (sempre he estat usuari de Windows) i  lleguim-vos em vaig comprar un notebook PackardBell DOT amb un Athlon de  64 bits i ATI Radeon 1250. 
Em vaig posar el 10.10 i de tant en tant es penjava. Al sortir el 11.10 me'l vaig instal·lar.
Però ves per on.... tot son ratlles a la pantalla horitzontals, com si fos el antic canal +, no veig res de res.
He carregat varis cops tant el 10.10, i s'empenya com el 11.10 que no veig res.
Alguna idea :frown::frown::frown::frown:

---

### Post by wgarcia on 2012-01-26
A vegades les qüestions gràfiques són ben frustrants com dius. Linux no té acords tipus els acords OEM entre Microsoft i els productors de maquinari (bé, hi ha alguns acords entre Canonical i alguns fabricants però de moment són pocs). Això provoca que a vegades els fabricants de maquinari no proveeixin els controladors perquè tot funcioni bé. 

Però a veure si es pot millorar el que veus. El primer que es podria fer és obrir una terminal i entrar

lspci -nn | grep -i vga

per veure exactament quin model de targeta gràfica tens.

---

### Post by xaviman on 2012-01-26
OK, però com obro un terminal, si tota la pantalla es plena de ratlles?
Es pot entrar amb algun "Mode a prova d'errors" del Windows?
Us envio la foto :(

---

### Post by xaviman on 2012-01-26
EPPPPPPPPP!!
Ho he trobat :P
Posa:
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]

---

### Post by Lalaith on 2012-01-26
hola i benvingut al món linux!

per obrir un terminal pel teclat: ctrl + alt + T. 

jo també sóc ben nova de fa poquet, i també em vaig frustar quan em vaig comprar el nou portàtil i em vaig tirar de cap a l'ubuntu. Ara m'ho prenc amb més filosofia i disfruto molt aprenent i anar fent passets... molts ànims!

---

### Post by xaviman on 2012-01-26
Se m'ha oblidat, perquè la pantalla on se'm demana la contrasenya es veu perfecte.

---

### Post by akyra on 2012-01-26
Hola Xaviman,

Jo també tinc una gràfica ATI i en la versió 11.10 d'Ubuntu he hagut d'utilitzar els drivers lliures. Amb els drivers privatius he tingut problemes.

T'aconsello que deshabilitis els drivers privatius, bé suposant que els tinguis habilitats.

Pots fer la prova amb el liveCD d'instal·lació d'Ubuntu, si es veu bé, et funcionarà bé amb drivers lliures.

El camí per Ubuntu no és tan senzill com amb una màquina que ja té un sistema operatiu instal·lat de fàbrica, però et puc assegurar que si no et desesperes i vas fent passos poc a poc, et preguntaràs com has pogut estar tan de temps utilitzant windows.
Ara, requereix una mica d'esforç de consultar forums i anar-la "cagant"

Salutacions.

---

### Post by wgarcia on 2012-01-27
Com et deien abans, és possible que la teva targeta no estigui ben suportada pels controladors d'ATI. Les comandes que pots donar per remoure el controlador propietari i instal·lar els controladors lliures són:

```
  
sudo apt-get remove --purge xorg-driver-fglrx fglrx*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases
sudo dpkg-reconfigure xserver-xorg

```

A veure si hi ha sort.

---

### Post by xaviman on 2012-01-28
Bueno senyors, moltes gracies!!
Us escric des de el meu netbook 11.10, ho he aconseguit ;)
Tan sols un detall per si li passa a algú i li val la meva experiència:

Al escriure: 
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases 

Em va dir que no tenia aquest paquet i vaig tenir que posar:

sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-updates

I em va anar perfecte.

Moltes gracies!!

---

### Post by wgarcia on 2012-01-29
Me n'alegro que funcioni. Podràs tornar el favor a la comunitat si canvies el títol a "Deceptionat amb ubuntu (la gràfica ATI no funciona)" o quelcom semblant, i uses el menú del fòrum "Thread tools" de dalt del tot per marcar "Solved".

---

### Post by akyra on 2012-01-30
Bé, espero que s'hagi curat una decepció.

Salut

---

