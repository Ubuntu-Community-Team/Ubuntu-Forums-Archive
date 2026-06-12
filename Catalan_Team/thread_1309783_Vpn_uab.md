---
title: "Vpn uab"
date: 2009-11-01
forum: Catalan Team
---

### Post by acrocephalus on 2009-11-01
Hola!
Estic intentant crear una connexió vpn per a connectar-me a la Universitat Autònoma de Barcelona amb Ubuntu Jaunty 9.04, però no m'en surto. He seguit les instruccions que es dónen a [http://www.uab.es/iDocument/configuracio_vpn_DebianLinux.pdf]("http://www.uab.es/iDocument/configuracio_vpn_DebianLinux.pdf"), però no em funciona. Algú em podria donar un cop de mà?
Salut!
Dani

---

### Post by akyra on 2009-11-02
Hola Dani.
Jo em connecto a la feina a través d'una VPN i m'he barallat una mica.
Què és el que no et funciona, a on estàs parat? 
Entenc que els paquets els has instal·lat sense problema.

Ho has probat amb el network-manager? És bastant senzill i hauria de funcionar.
Tens algun fitxer de configuraciÓ?

---

### Post by acrocephalus on 2009-11-02
Hola
No és que em quedi encallat en lloc. Teòricament, ho instal·lo tot i creo els arxius sense cap problema, però quan executo ```
sudo pon uab
``` no veig la interfície ppp0 quan executo ifconfig. També he provat el network-manager, però em diu que falla en connectar-se, tot i que diria que els paràmetres són els correctes.

Dani

---

### Post by akyra on 2009-11-02
Així ni idea,
jo ara també m'estic barallant amb el kvpn i tampoc em surto.
Ho sento.

---

### Post by acrocephalus on 2009-11-02
Ja ho he arreglat :p. En el meu cas, en el fitxer /etc/ppp/options.pptp calia comentar les línies que contenien refuse-pap i refuse-chap, ja que així ho requereix la connexió a la UAB. Ara, he hagut de fer un remix de les intruccions per a Debian i per a Ubuntu Gibson per esbrinar-ho. Amb el network manager no hi ha hagut manera.
Salut!

Dani

---

### Post by papapep on 2009-11-02
acrocephalus, estaria bé que detallessis al màxim la configuració i accions que t'han funcionat, de cara a que quedi reflectit per si algú altre darrera teu té el mateix problema ;)

---

### Post by akyra on 2009-11-03
M'alegro de que s'hagi solucionat
Adeu

---

### Post by acrocephalus on 2009-11-03
Hola,
Intentaré detallar-ho una mica més. Bàsicament he seguit les instruccions descrites a [http://www.uab.es/iDocument/configuracio_vpn_DebianLinux.pdf]("http://www.uab.es/iDocument/configuracio_vpn_DebianLinux.pdf") Ara bé, quan s'edita el fitxer ```
/etc/ppp/options.pptp
``` cal que la secció que conté els paràmetres d'autenticació estigui com mostro a continuació, és a dir comentant les línies refuse-pap i refuse-chap.

```
# Authentication
# We don't need the tunnel server to authenticate itself
noauth

# We won't do PAP, EAP, CHAP, or MSCHAP, but we will accept MSCHAP-V2
# (you may need to remove these refusals if the server is not using MPPE)
#refuse-pap
refuse-eap
#refuse-chap
refuse-mschap
```

Aleshores hauria de funcionar sense problema. De totes maneres passaré la info al servei d'informàtica de la UAB per tal que arreglin les instruccions de configuració.

Espero que pugui ser d'utilitat!

Dani

---

### Post by papapep on 2009-11-03
Moltes gràcies, Dani!

---

### Post by okekarito on 2009-11-09
Hola, jo amb l'Intrepid i les instruccions que hi ha al servei d'informàtica de la universitat no havia tingut problemes amb el network manager, però he canviat d'ordinador i m'he passat al Karmic i no hi ha manera. El nou network manager té un munt d'opcions i no me'n surto. He provat amb l'arxiu per a debian que ha penjat l'acrocephalus...però res!  Si algú té alguna idea o a aconseguit fer-lo funcionar, doncs estaria molt agraït.

---

### Post by acrocephalus on 2009-11-09
Has descomentat les línies refuse-pap i refuse-chap? Si és així i continua sense funcionar, no et puc ajudar.
Sort!

Dani

---

### Post by okekarito on 2009-11-09
Tema resolt. El cas és que ho he fet amb el network manager com fins ara, però remenant les opcions.

Gràcies per l'ajuda.

Explico com ha quedat la configuració del network-manager per si és útil per a algú.

Parámetres IPv4 --> automàtic
VPN avançat --> totes les caselles desmarcades excepte el "CHAP"

---

### Post by tanreb20 on 2009-11-09
Ei!

Jo també vaig a la UAB!

Quina passarela has posat per conectar-te?

L'usuari i el password són el niu i la contrasenya del CV oi?

---

### Post by acrocephalus on 2009-11-11
Hola!
La passarela és vpnwg.uab.es, i l'usuari i la contrassenya són, efectivament, el NIU i el teu pwd per accedir al webmail.

Dani

---

### Post by okekarito on 2009-11-13
Si algú encara té dubtes, a la plana del Servei d'Informàtica ([www.uab.cat/si](www.uab.cat/si)) han actualitzat la informació per al Karmic koala.

Salut

---

### Post by antoniu on 2011-02-01
No me'n surto, ni seguint la guia per linux ni amb el network manager...amb el network manager seria només:
Gateway: vpngw.uab.es
user: niu
password: contrassenya uab
nt domain=?

a advanced si faig tot desmarcat menys chap i res

---

