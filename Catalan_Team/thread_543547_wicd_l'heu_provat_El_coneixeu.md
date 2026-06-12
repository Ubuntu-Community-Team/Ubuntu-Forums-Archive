---
title: "wicd: l'heu provat? El coneixeu?"
date: 2007-09-05
forum: Catalan Team
---

### Post by patrickfromspain on 2007-09-05
Hola gent!

Aquests dies estic probat un substitut del network-manager: wicd. NM no m'ha agradat mai.. aixo d'haver de posar el password cada cop hem posa del nervis. Si, se que es pot desactivar, pero la veritat... no tinc ganas de buscar com es fa, i no tinc la certesa de que això funcioni després d'algun update.

Doncs he trobat un programeta que m'agrada molt: [wicd]("http://wicd.sourceforge.net/")

Igual no es tan automatic com el NM, però la veritat es que esta bastante bé.

Sobretot per als que feu servir un portatil us resultarà molt útil. Si el probeu, digueu que tal!

Salut!

---

### Post by papapep on 2007-09-05
Avui mateix el provaré, perquè pitjor que el network manager no em pot anar. 

Gràcies per la referència.

EDICIÓ: Ja l'he instal·lat i, per ara, em funciona perfecte. "Fins i tot" he reiniciat dos cops l'ordinador i m'ha conservat la configuració de xarxa cada cop, increïble!!! :-D

---

### Post by CarlesOriol on 2007-09-05
He....

Jo tinc fet un script com el de baix però és molt interessant el programet despres el provo.

IFACE="eth1"
IFCONFIG="/sbin/ifconfig"
IWLIST="/sbin/iwlist"

RESULT=""

RES2=""



ifdown $IFACE
rm /etc/resolv.conf

#ifup $IFACE

APOINTS=$($IWLIST $IFACE scan)

#echo $APOINTS

if echo $APOINTS | grep -i "No scan results" >/dev/null >/dev/null;then 
	echo "No es troben punts d'accés"
	exit 1
fi

echo $APOINTS | grep -i 00:30:bd:96:dd:8f >/dev/null
if [ $? = 0 ] ; then
	echo "La xarxa X"
	
	iwconfig $IFACE essid xarxax mode Managed rate auto key restricted 1234567890	
	ifconfig $IFACE up
	dhclient $IFACE

fi

... n xarxes




#cerquem un ordinador d'una xarxa
ping -c1 -w2 192.168.5.1 > /dev/null

if [ $? = 0 ] ; then
	echo "Estem xarxa X"
	... fes totes les porqueries que vulguis com muntar unitats, canviar dns etc...
fi

---

### Post by Ferri on 2007-09-06
Jo tampoc sóc un entusiasta del network-manager i fa poc vaig provar-lo. En principi semblava que tenia força possibilitats però no vaig aconseguir que em connectés a la meva wifi (tampoc m'hi vaig passar massa estona, però).
L'altre defecte important que li vaig veure és que no et permetia configurar una VPN, si no em falla la memòria.

---

### Post by patrickfromspain on 2007-09-06
sols en papapep diu que va be? xD

els demes que? no el probeu? no us agrada? no us funciona? ja el feu servir?

salut!

PD: jo el faig servir al portatil, es una maravella, i la meva novia n'esta molt contenta tambe, molt millor que wifi-radar.

---

### Post by abuch on 2007-09-08
Hola,

fins ara feia servir el wifi-radar. Després de provar el wicd em sembla que seguiré amb ell. M'ha semblat molt més ràpid a l'hora de connectar amb diferents wifis.

Aleix

---

### Post by patrickfromspain on 2007-09-08
be.. nomes dirvos que, per primera vegada, he sigut capaç de conectar-me a una red encriptada amb wpa-psk tkip. Sense tocar wpa-supplicant ni res, nomes possant la meva contrasenya! Alucinant :)

salut!

---

### Post by ernestux on 2007-09-09
No està disponible en cap repositori amb synaptic ?

Jo tinc el wifi radar i amb el portàtil trobo que va força bé. 

Salut

---

### Post by papapep on 2007-09-09
Ernestux: Has d'afegir aquesta línia al /etc/apt/sources.list:

deb [http://wicd.longren.org](http://wicd.longren.org) feisty extras

i ja els tindràs disponibles.

---

### Post by ernestux on 2007-09-09
Ja el tinc disponible. 
Només un problema:  en marcar-lo per instal·lar-lo diu que eliminarà Network-Manager  i el Wifi-Radar  !!!

Val la pena?  I si després no puc connectar-me?

---

### Post by papapep on 2007-09-09
> Només un problema: en marcar-lo per instal·lar-lo diu que eliminarà Network-Manager i el Wifi-Radar !!!

Doncs tu mateix, si no tens altra manera de connectar a internet i tens por de quedar-te sense connexió doncs no ho facis. Però a mi em va perfecte. Prova-ho un dia que tinguis on connectar-te amb cable per si falla.

---

### Post by patrickfromspain on 2007-09-09
ves a packages.ubuntu.com i baixa't el .deb del wifi-radar. Despres insta&#320;la el wicd i ja esta. Si no et va, desinsta&#320;les el wicd i insta&#320;les el wifi-radar que t'has baixat manualment.

salut!

PD: proba'l, segur que et va molt be.. si et funciona el wifi-radar, aquest no hauria de ser diferent.

---

### Post by ernestux on 2007-09-25
Hola a tots,

Finalment el vaig instal·lar amb synaptic (esborrant wifi radar ..) i funciona tot correctament  !    Jo tinc marcat "automatically connect " a les xarxes que m'interessen (ja que notinc adsl) , però no sé si hi ha alguna opció que faci que es conecti a la xarxa que arriba amb més potència....

Records

---

### Post by patrickfromspain on 2007-09-25
Abans d'ahi vaig pujar la traduccio al catala. A veure si a la següent versió podem tenir-la ^^

---

### Post by Tomàs M. on 2007-10-02
> **patrickfromspain said:**
> sols en papapep diu que va be? xD

els demes que? no el probeu? no us agrada? no us funciona? ja el feu servir?


L'acabo de provar i de moment he tornat al NM: no hi ha hagut manera de connectar a cap de les dues xarxes protegides de casa, i m'ha deixat  el sistema totalment bloquejat. Ni reiniciant arrencava. Al final amb les opcions que surten a la pantalla de loguin he pogut entrar, i connectant amb la xarxa oberta que tinc de FON he tornat a instal·lar el NM. 
Quan pugui miraré el wifi-radar; l'únic que m'interessa és el tema de tenir wifi després d'hibernar.

Tomàs.

---

