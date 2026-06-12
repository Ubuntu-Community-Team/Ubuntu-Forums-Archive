---
title: "No puc iniciar sessió despres de actualitzar a 17.04"
date: 2018-06-01
forum: Catalan Team
---

### Post by Contaboy on 2018-06-01
Avui he actualitzat de la 16.10 a la 17.04
Ho he fet des de consola de la següent manera.
sudo apt-get update&&upgrade
sudo do-release-upgrade

Ha estat una estona actualitzant i al final m'ha demanat reiniciar

Quan reinicia es queda amb la nova pantalla de inici però el teclat ( conectat per PS2) no fa res malgrat que sembla estar tot bé (puc activar/desactivar Bloq num. per exemple) 
He provat diferents combinacins de tecles però sota cap respon. Ni tan sols si li faig Alt puc anar a les icones superiors.
El ratolí (conectat per USB) està mort.

PEr tant no puc iniciar sessió

En consola de recuperació he comprobat paquets i revisat instal·lacio

Consola en root no em permet fer res sobre el SO ja que tots els paquets estan en lectura.

L'arrancada en versions anteriors des de la GRUB dona error i es para

QUe puc fer? Gràcies anticipades per la vostra col·laboracio

---

### Post by wgarcia on 2018-06-02
Entenc que arrenca, arribes a la pantalla d'inici per entrar la contrasenya, inicia l'escriptori (quin escriptori fas servir?) i aquí queda congelat?

---

### Post by Contaboy on 2018-06-02
No puc entrar la contrasenya ja que el teclat i el ratolí estan congelats. 
Per tant no arribo mai a l'escriptori.  No puc passar de la pantalla de inici que veig que ha canviat de la que tenia en el 16.10
L'actualització la vaig fer des de la versió 16.10 LTS que funcionava sense problemes i on treballava amb l'escriptori per defecte i Unity.
LA versió antiga tampoc arriba a arrencar. Al mig de l'arrencada el teclat comença a parpadejar.

---

### Post by wgarcia on 2018-06-03
Crec que el que veus és degut al canvi que es va fer de la versió 16.10 que tenia l'escriptori Unity a la versió 17.04 que porta l'escriptori GNOME.  A més la pantalla d'inici va canviar del sistema LightDM al sistema GDM. Ja he vist que segons quines targes gràfiques. el sistema GDM queda congelat com ho descrius. Per arreglar-ho, es pot tornar a habilitat el sistema LightDM. Primer es pot provar si es pot fer entrant en mode recuperació, obrint una consola "root", i entrant l'ordre següent:

```
dpkg-reconfigure lightdm
```

Et preguntará quin sistema d'inici vols usar, i has d'escollir "lightdm". Un cop que puguis reiniciar es pot investigar una mica més perquè el GDM no funciona i intentar solucionar-ho.

Si no es pot reconfigurar des de la consola root de recuperació, hi ha una altra manera der fer-ho amb un USB d'instal·lació, però com és més complicad (tot i que no excessivament), primer es pot provar la solució de dalt a veure si funciona.

---

### Post by Contaboy on 2018-06-03
Amb aquesta solució torno a veure la pantalla d'entrada antiga però continuen sense funcionar teclat ni ratolí.

Per si és d'ajuda la tarja gràfica que tinc és una Nvidia GTX1050

Vaig investigant i he llegit un article sobre un que tenia un teclat Logitech com el meu amb problemes amb el paquet fwupd però no sembla ser el meu cas ja que aquest si que pot logejar.

Per si serveix he canviat el teclat que tinc Logitech SR34 que tinc en PS2 per un teclat Genius amb connexió per PS2.

Tampoc em deixa logejar i a més el Genius queda tan mort que ni tan sol engeja llums quan li activo/desactivo tecles numèriques

Podria haver una incompatibilitat de drivers teclat/ratoli?

El ratoli que utilitzo es el logitech bàsix RX250

---

### Post by wgarcia on 2018-06-03
Doncs sí, pot ser un problema de controladors de la targeta. El primer que es pot provar es veure si des de la sessió de recuperació es poden actualitzar els controladors. Et caldrà tenir activada la xarxa, hi ha una opció per activar-la. Un cop a la consola es pot mirar si les ordres següents actualitzen els controladors:

```
sudo apt purge nvidia*
sudo apt update
sudo ubuntu-drivers autoinstall
sudo apt full-upgrade
```

Si no funciona es pot provar l'altre procediment de fer-ho des d'un USB d'instal·lació com comentava abans.

---

### Post by Contaboy on 2018-06-03
No ha funcionat. 
Estic per fer el que feia temps que tenia planejat. 
Ara tinc un SSD amb el windows per jugar i un disc de 3TB on tinc la particio de linux i una per arxius de jocs.
Estic per muntar un nou disc petit on possar sola la partició de linux ja que és le que m'agrada per navegar i fer les meves coses i així faria neteja ja que crec que hi ha alguna incompatibilitat entre els nous drivers i programari antic.

---

### Post by wgarcia on 2018-06-04
Quin error dóna? Acaba d'instal·lar-se, però continua congelant-se la pantalla?

---

### Post by Contaboy on 2018-06-04
Errors detectats.
QUan activa xarxa dona error ja que no troba el iftxer /etc/ resolv.conf.

Eliminar al final diu que troba problemes en releases, Tranlation i DEP-11 a etc/aptsources

No actualitza bé ja que no pot resoldre la baixada d'arxius de [http://es,arxiu.ubuntu.com](http://es,arxiu.ubuntu.com)

També he provat de tornar a ggnome sense èxit

---

### Post by wgarcia on 2018-06-04
D'acord, llavors és que no tens xarxa a la sessió de recuperació.

Et passo les instruccions per intentar fer-ho des d'un USB autònom. És a dir, et cal un USB d'instal·lació, arrencar l'ordinador des de l'USB, i entrar a la sessió de prova. Un cop que estàs a la sessió de prova, i amb connexió a la xarxa per cable o per wifi, cal obrir una terminal i entrar les ordres següents:

```
sudo mount /dev/sda1 /mnt
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /dev/pts /mnt/dev/pts
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /sys /mnt/sys
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
sudo apt purge nvidia*
sudo apt update
sudo ubuntu-drivers autoinstall
sudo apt full-upgrade
```

Quan acabes, pots tancar la terminal i reiniciar el sistema a veure si hi ha hagut sort (si no ha donat errors).

Això el que farà és que iniciarà la sessió que tens instal·lada en un contenidor root, i actualitzarà el sistema amb els controladors si tot va bé.

---

### Post by Contaboy on 2018-06-04
lubuntu@lubuntu:~$ sudo mount /dev/sda1 /mnt
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

---

### Post by Contaboy on 2018-06-04
He acoseguit instal·lar drivers però al final fa el mateix. 

Resulta que des de el Live em dona l'error anterior i jo continuo provant coses. Em dona per tornar a canviar a gnome i enlloc d'entrar la pantalla em queda negra.
Provo d'obrir una consola i faig logging. 
Llavors he provat a repetir la seqûència i no ha fet res per treure els drivers nadius de Nvidia ja que els havia tret però en canvi he instal·lat els nadius de ubuntu i he fet upgrade sense cap problema. 

La llàstima es que quan reinicio torno a veure la pantalla d'entrada inicial però continua sense funcionar el teclat i el ratolí

---

### Post by wgarcia on 2018-06-05
Probablement /dev/sda1 no és el dispositiu on està instal·lat l'Ubuntu que vols arreglar, sinó un altre volum potser l'USB mateix del "life". Primer s'hauria d'esbrinar on és l'Ubuntu amb 

```
sudo fdisk -l
```

---

### Post by Contaboy on 2018-06-06
He seguit les instruccions i identificat el disc.
He realitzat tot el procediment sense que hi hagues cap error. 
La llàstima es que al reiniciar ara ha desaparegut el punter del ratoli i continua sense funcionar. 
He estat examinant les linees d'ordres de càrrega que es veuen quan entres en mode recovery i no veig l'error. 
Inicialment em reconeix el teclat i el ratolí.
Després diu que es carrega el Unbuntu 17.04 i surt un missatge que diu missing drivers on no especifica que falta. 
Just abans de mostrar la consola de recuperació sembla com si instal·les el mouse i el teclat de nou. 
Costa de veure perque va a tota fava.

A menys que a algú se li acudeixi alguna cosa nova per provar. 

Suposo que aprofitaré per desmuntar el grub. Faré el upgrade de windos que tinc pedent i faré una istal·lacio nova de ubuntu 18 en un disc petit nou i aixi tindre els dos SO en discos diferents i un tercer per dades.

Moltes gràcies per l'ajuda i l'interés.

---

### Post by wgarcia on 2018-06-06
En aquesta pàgina sembla que proposen algunes solucions per al teu problema:

[https://charlienewey.github.io/getting-nvidia-drivers-working-on-ubuntu-17-10/](https://charlienewey.github.io/getting-nvidia-drivers-working-on-ubuntu-17-10/)

---

### Post by Contaboy on 2018-06-06
Ho provaré des de el cd live només cal que combini les dues propostes. 

Gràcies.

---

### Post by Contaboy on 2018-06-06
No sé que he liat però ha funcionat.

He combinat les dues formules i les he executat des de un live. 

La sessió no arrancava ja que deia que hi havia problemes amb fitxers i blocs. 

He arrencat en mode recovery i li he executat la ordre dpkg per tal que reparés els paquets reinstal·lant 14 paquets trencats.

Quan he reiniciat ho he fet sense pantalla de inici i llavors he obert una consola. 

He fet update, upgrade i tornat a possar l'escriptori en gnome. 

He reiniciat i entra perfecte i tot funciona perfectament. 

M'ha llençat l'actualitzacio a la versió 18.04 LTS. Espero que aquesta vegada sense incidències.

Com dic sempre el millor de ubuntu és la seva comunitat.

Gràcies per la vostra ajuda.

---

