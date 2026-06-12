---
title: "[SOLVED] EKIGA i comunicació per VoIP"
date: 2007-08-28
forum: Catalan Team
---

### Post by papapep on 2007-08-28
Aquesta tarda he estat mirant si podia parlar amb un company amb l'Ekiga i m'he quedat clavat sense trobar sortida al tema:

Ambdós tenim instal·lat el programari dels repositoris d'Ubuntu i hem verificat que la prova d'audio que incorpora el mateix Ekiga funciona correctament, amb el qual, en teoria, verifiquem que funciona correctament tant l'entrada com la sortida d'audio. A més, hem executat aquesta comanda:

```
arecord -D plughw:0,0 -c 1 -r 8000 -f S16_LE - | aplay -D plughw:0,0 -c 1 -r 8000 -f S16_LE -
```

que fa la mateixa prova, però fora de l'Ekiga, i funciona a la perfecció.

Ambdós tenim comptes a ekiga.net, i quan ens truquem tot va bé fins que el de l'altra banda despenja. A partir d'aquí, el programa comença a generar errors d'aquests:

```
2007/08/28 18:39:55.361   6:25.256          Media Patch:89e66d0 Opal    Expected payload type [pt=96], but received PCMU. Ignoring packet
```

dels quals no trobo cap mena de referència enlloc. Al tenir tots dos routers amb tallafocs, tenim activat l'STUN.
El resultat a la pràctica és que ni ell em sent ni jo a ell...

Algú té alguna idea al respecte?

---

### Post by muleta on 2007-08-28
Jo fa molts anys que utilitzo l'Skype sense problemes. L'he instal·lat a Ubuntu però encara no l'he provat. Ho faré quan me'n acabi de sortir d'altres temàtiques més urgents.

L'he utilitzat per parlar gratuïtament amb gent de tot el món que el tingui instal·lat, o a preu de trucada local, si no tenen Internet.

És una meravella i no em canso de recomanar-lo.

---

### Post by papapep on 2007-08-28
Programari propietari i de codi ultra-tancat....no gràcies. :-)

---

### Post by muleta on 2007-08-28
Aiiiiih...:( He fet res dolent?.

M'ho expliques?.

---

### Post by PellRoja on 2007-08-28
mira aixo mula

[http://www.kriptopolis.org/node/4808](http://www.kriptopolis.org/node/4808)

skype no és de fiar

jo et recomano [http://www.openwengo.org/](http://www.openwengo.org/) :guitar:

---

### Post by muleta on 2007-08-28
> **PellRoja said:**
> 

skype no és de fiar



Ondia!, que fort!!.

No havia llegit mai una crítica tan descarnada, només algún problema tècnic amb el sò,  en alguns forums, però el balanç era molt positiu. Tots els seus usuaris en semblen plenament satisfets.

I aquesta mala publicitat no pot haver estat promuguda pels seus detractors?. Fixeu-vos que tot són suposicions. Hi ha res demostrat?.

Em dona una mica l'impressió de que busquen una manera de desacreditar-lo. Ja sabem que no hi ha res segur del tot. Com a mostra d'inseguretat total comprovada i refermada: la línea telefònica.

---

### Post by papapep on 2007-08-28
> Tots els seus usuaris en semblen plenament satisfets.

Segur que són feliços usuaris d'aquell S.O. que fan a Redmond (Virginia).

Cadascú pot fer servir el que li sembli. Personalment, crec hi ha coses que cal evitar, i fer servir programari per a les comunicacions que no ofereix la més mínima garantia de seguretat ni privacitat, apart de ser privatiu i de codi ultra-mega-super secret, doncs passo.

A partir d'aquí, cadascú és lliure. Jo parlo per mi. :-)

---

### Post by pespin on 2007-08-28
Per si et serveix aqui hi han altres programes que he trobat:

asterisk -> [www.asterisk.org]("htp://www.asterisk.org")

llista de programes VoIP open source -> [http://www.voip-info.org/wiki-Open+Source+VOIP+Software]("http://www.voip-info.org/wiki-Open+Source+VOIP+Software")

---

### Post by papapep on 2007-08-28
Asterisk va bastant més enllà del que els comuns mortals volem per a comunicar-nos. Amb ell pots montar, p.ex.,  una centraleta corporativa amb mil·lers d'extensions i amb terminals tant analògics com digitals i, tot plegat, amanit amb gateways de veu per ip. Imagina't ;-)

Respecte la llista, gràcies, hi faré un cop d'ull.

---

### Post by CarlesOriol on 2007-08-29
> El resultat a la pràctica és que ni ell em sent ni jo a ell..

Heu provat els dos d'enregistrar audio sense l'ekiga?

---

### Post by papapep on 2007-08-29
Si Carles, és el que fan les comandes aquestes que he comentat.

---

### Post by YannickDefais on 2007-08-29
Hi,

Sorry I can't use your langage, but I mostly understand.

To me it seems you don't have the proper audio codec enable in Ekiga preferences.

Go to Edit -> Preferences -> Audio codecs and enable them all (The SIP protocol Ekiga uses, can negociate the codec you have in common with the peer you want to reach, the better is to have all codecs enabled (unless some of them cause trouble) and order them : the first one at the top list will be try first, etc.)

I wrote a documentation here especially for Ubuntu:
[https://help.ubuntu.com/community/Ekiga](https://help.ubuntu.com/community/Ekiga)

And a general one here:
[http://wiki.ekiga.org/](http://wiki.ekiga.org/)

Regards,
Yannick

---

### Post by CarlesOriol on 2007-08-29
> **papapep said:**
> Si Carles, és el que fan les comandes aquestes que he comentat.

Ja saps que soc de tecla fàcil...

Has comprovat el mesclador que hagis triat a l'ekiga que la seva font d'entrada correspongui amb la que tens activada al mesclador de so?

---

### Post by papapep on 2007-08-29
Ho he verificat tot, tot i tot....:-(
Tic dezeperat....

Provaré l'OpenWengo a veure si es comporta millor...
(Hem provat amb l'Skype, i ....merda....funciona perfectament. Però no, resistiré!!!)

---

### Post by muleta on 2007-08-29
> **papapep said:**
> 
(Hem provat amb l'Skype, i ....merda....funciona perfectament. Però no, resistiré!!!)

Em sap greu haver-te de dir que, abans de quedar-me amb l'Skype i enamorar-me d'ell, vaig investigar i provar tots els altres. Em van donar molts problemes: dialers, spam, spyware, s'havia de pagar per provar o pagar per utilitzar-lo (a tarifes reduïdes, això sí), etc.

Era comunicar i bé o no counicar i, com que havia de fer trucades diaries a Europa i Àsia, em vaig haver de decidir, fos o no fos ètic, esquinzeu-vos les vestidures, si voleu.

Sempre et quedarà l'alternativa d'utilitzar la linea convencional de Timofónica.:rolleyes:

---

### Post by papapep on 2007-08-29
Dialers....spyware.....de quina galaxia estàs parlant???? :-P

I tranquila, és qüestió de temps, però ho trobaré...!!! . ](*,)

---

### Post by papapep on 2007-08-30
YannickDefais: I have tried what you told, actually everything was already correctly setup, and we continue having the same problem.... I think I will give a try to openwengo.

Thanks for your comment (alltough you don't "speak" catalan ;-)) Have you ever thought in learning it?? Here you would have a very good chance! :-D

---

### Post by papapep on 2007-08-30
Bé, finalment l'OpenWengo i jo ens adoptat mútuament. iinterfície clara, m'integra VOiP i Jabber, què més vull...

OpenSource i funciona de conya, la qüalitat del so és igual o millor que amb l'Skype. Qui dóna més?? :-D

---

