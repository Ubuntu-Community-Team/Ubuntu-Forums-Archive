---
title: "[SOLVED] Connexió PC-TV"
date: 2007-08-31
forum: Catalan Team
---

### Post by prostata on 2007-08-31
Bon dia....

Vull connectar  el meu PC sota ubuntu, (amb windows ja funciona), a la TV.

Com deia sota windows no hi ha problema, però sota Ubuntu no en tinc ni idea i com que la major part de temps treballo sota aquest entorn, voldria no haver de sortir a l'altre i fer-ho des de aquí.

Podeu ajudar-me una miqueta, ????

Gràcies

---

### Post by papapep on 2007-09-01
Cal que ens expliquis el que pretens fer exactament per a poder-te ajudar. Què vols, veure les pel·licules que tens al pc a la televisió?? Què tens, un fix o un portàtil. Ens has de donar base per raonar.

---

### Post by prostata on 2007-09-01
> **papapep said:**
> Cal que ens expliquis el que pretens fer exactament per a poder-te ajudar. Què vols, veure les pel·licules que tens al pc a la televisió?? Què tens, un fix o un portàtil. Ens has de donar base per raonar.


Doncs tinc un PC de sobre taula i una TV LCD, ja tinc fetes les connexions de video i audio, i amb entorn windows la cosa funciona, però en entorn Ubuntu no en tinc ni idea. Si et fa falta més info. demana si us plau...gràcies...i i si vull veure les pelis dels Hd a la TV

---

### Post by papapep on 2007-09-01
> i amb entorn windows la cosa funciona, però en entorn Ubuntu no en tinc ni idea

Ho has provat i no va en Linux? o encara no ho has provat? En tot cas, la placa de video és integrada a la placa mare o és una pci o agp? Quin model és??

---

### Post by prostata on 2007-09-01
> **papapep said:**
> Ho has provat i no va en Linux? o encara no ho has provat? En tot cas, la placa de video és integrada a la placa mare o és una pci o agp? Quin model és??

La placa de viedo es Nvida gforce FX 5200 (pci), segons l'info de sistemes

Vaig provar ahir però no anava, vaig pasar de sesió WXP a Ubuntu per provar però  a la TV no es veia res de res, demá tornaré a provar avui tinc altres coses ;-)

---

### Post by ChAoS.ct on 2007-09-01
Si fas servir el driver propietari de nvidia, crec que hi ha un programa anomenat nvidia-config o algo així (ara no ho recordo bé) que et permet configurar les X al vol, detectant els monitors en calent i que va molt bé.
Ah el programa ve de sèrie amb el driver crec.

---

### Post by prostata on 2007-09-02
He fet el següent:

He conectat el PC a la TV, sempre sota Ubuntu.
I el resultat es.

La pantalla de la Tv em diu Sense Senyal :(

I....ara què????? ;-)

---

### Post by CarlesOriol on 2007-09-02
Prova-ho amb un altre cable.

Aquesta gràfica (i gforces anteriors) conectat SOL a la tv hauria d'anar sense tocar res de res.

---

### Post by guillemsola on 2007-09-02
Jo tinc un portàtil amb una nvidia amb  el driver propietari. 

Com que tampoc em funcionava la tv-out de sortida he provat el programa nvidia-settings que suposo és el que deia Chaos.ct.

He aconseguit mostrar l'imatge per la tv però el que no he aconseguit era clonar l'escriptori sino que el que tenia a la TV era una extensió de l'escriptori del portàtil.

Salut!

---

### Post by CarlesOriol on 2007-09-02
Prova l'nvidia settings amb sudo

---

### Post by prostata on 2007-09-02
> **CarlesOriol said:**
> Prova l'nvidia settings amb sudo

Company: 
perdona la pregunta de primer, però tinc un problema amb la terminal, quan escric su, i li fico la contrasenya de sempre em respon, 

josep@josep-desktop:~$ su
Password: 
su: Authentication failure

he estat i estic força desconectat, per la canicula però ara aquesta resposta em deixa fora de joc...una petita ajuda..
gràcies

---

### Post by prostata on 2007-09-02
> **CarlesOriol said:**
> Prova l'nvidia settings amb sudo

Epp!!! aixó el que em diu desprès de escriu-re bé:

josep@josep-desktop:~$ sudo nvidia settings
Password:
sudo: nvidia: command not found
josep@josep-desktop:~$

---

### Post by guillemsola on 2007-09-02
prova amb "sudo nvidia-settings". Per això et diu que no troba l'ordre.

Recorda que tabulador completa l'ordre així sempre saps que aquella ordre existeix.

Salut

---

### Post by prostata on 2007-09-02
> **angrychai said:**
> prova amb "sudo nvidia-settings". Per això et diu que no troba l'ordre.

Recorda que tabulador completa l'ordre així sempre saps que aquella ordre existeix.

Salut

Gràcies, ara funciona la pantalleta de les propitats de Nvidia. Però que és el que haig de considerar dins aquesta pantalla.....

salut

PD,  Gràcies a tots per les vostres respostes, son molt interessants per a mi, però avui mateix començaré la segona tanda de les meves vacances i estaré fora un petit temps, així que de seguida que torni, llegiré les vostres respostes i em posaré a fer feina..Gràcies!!!!!!

---

### Post by guillemsola on 2007-09-02
Primer has de conectar el portàtil a la TV i aleshores pitxar on diu detectar pantalles. 

Aleshores detecta que té una segon dispositiu de sortida que pots seleccionar i configurar

salut

---

### Post by prostata on 2007-09-09
> **angrychai said:**
> Primer has de conectar el portàtil a la TV i aleshores pitxar on diu detectar pantalles. 

Aleshores detecta que té una segon dispositiu de sortida que pots seleccionar i configurar

salut

bon dia, ja soc aquí...!!!

Primer de res, gràcies per la teva ajuda. He fet el que m'has dit, i finalment i desprè de més d'una prova, les possibilitat de configuració son interessants he pogut veure una peli per la TV, bé una petita part de mostra. A l'apartat de Xserver display configuration i dins de Configuration exactament apreixen tres possibilitats:

Disable (que no es "prudent" ;-)
Separate X screen
TwinView

He fet proves amb les dues últimes i més o menys he vist que anava, però a l'partat resol-lució  surt 1024x760 si mal no recordo. Voldria posar la resolució a 1280X1024 però no em deixa, hi ha alguna forma de fer-lo??

He observat que a la pantalla de l'ordinador es veu tot el plá de la peli però a la TV es talla una mica l'imatge per la part de sota, ¿saps alguna solució perquè surti tot el plá tant per l'ordinador com per la TV? es dir que es vegi a la TV tal com es veu per la pantalla del PC?? En una de les opcions he activat clone però ni amb aquesta...

Gràcies

---

