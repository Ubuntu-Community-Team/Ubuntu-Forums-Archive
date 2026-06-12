---
title: "Configurar el Thunderbird."
date: 2007-10-30
forum: Catalan Team
---

### Post by lo gambusí on 2007-10-30
Salut!!

Estic configurant el correu del Thunderbird, amb un compte de lamalla.net i un de gmail.com.

Rebo lo correu perfectament, però a l'hora d'enviar-lo no me l'envia, es queda connectant. 

He posat de servidor SMTP smtp.gmail.com perquè me diu que puc posar un de comú per als dos comptes. Canviant-ho per correu.lamalla.net tampoc me funciona.

Alguna idea?

Gràcies!:)

---

### Post by papapep on 2007-10-30
Has marcat que el servidor SMTP faci servir TLS?

---

### Post by lo gambusí on 2007-10-30
No ho havia marcat perquè [aquí]("http://www.slackware.cl/?q=node/216") me dia de marcar lo 465.

igualment, ho he provat ara i seguix sense enviar-se'm.

---

### Post by papapep on 2007-10-30
Doncs a mi em funciona posant-li el port 25 i dient-li que faci servir TLS si està disponible.

---

### Post by lo gambusí on 2007-10-30
Pos a mi no :(

Pot tenir alguna relació en lo fet que mescle correu de La Malla i Gmail?

---

### Post by papapep on 2007-10-30
No ho sé. Prova a no barrejar-ho i sortiràs de dubtes.

---

### Post by lo gambusí on 2007-10-30
Igual...

---

### Post by rajoar on 2007-11-01
Edita el SMTP i posa-hi el nom del compte!

---

### Post by lo gambusí on 2007-11-01
Com? :P

---

### Post by patrickfromspain on 2007-11-02
Al thunderbird: Edita -> Parametres del comptes. Alla ves abaix de tot i selecciona Servidor de sortida (SMTP). Selecciona del del gmail i Edita. Alla hi ha de posar:

Descripció: el que vulguis.
Nom del servidor smtp.gmail.com
Port: 587
Marca Utilitza el nom i la contrasenya i despres:
Nom d'usuari: el teu mail sense @gmail.com. Per explemple: pepito.palotes
Utilitza una connexió segura: TLS

Aixo ha de funcionar. Es com ho tinc jo i hem funciona a les 1000 maravelles.

EDITO: la font es aqui [http://mail.google.com/support/bin/answer.py?answer=38343&topic=12567](http://mail.google.com/support/bin/answer.py?answer=38343&topic=12567)

---

### Post by pserra on 2007-11-03
Doncs jo també tinc problemes amb el coi de thunderbird...
hi tinc 2 comptes, el de la dona i el meu... i el de la dona no em va costar gens d'instalar-lo i el meu no hi ha manera... ho he repassat varies vegades i sempre em surt el missatge al cap d'uns segons  :  

                       L'ordre pass no ha tingut éxit........
                       Reautentification failure........

I ho comprovo i ho tinc tot igual menys els noms i contrasenyes....
A algú li passa el mateix?

---

### Post by lo gambusí on 2007-11-04
gràcies, però lamalla.cat seguix sense anar-me...

---

### Post by lo gambusí on 2007-11-09
Vaig enviar un correu a lamalla.net a vore si me deien res fa una setmana i encara no sé res...

---

### Post by patrickfromspain on 2007-11-10
A lamalla.cat pots rebre correu des de el thunderbird, o això no et funciona?

T'ho dic perque si això et funciona, de servidor de sortida nomes en pots tenir UN: no pots fer servir d'SMTP smtp.lamalla.cat (per exemple) i stmp.gmail.com, només en pots configurar un.

Salut!

---

### Post by lo gambusí on 2007-11-10
Puc rebre'n però no enviar-ne.

Ara mateix sols tinc la malla, he tret lo gmail. Tinc tot configurat com me diuen a la web i no me dixa enviar-ne. :(

---

