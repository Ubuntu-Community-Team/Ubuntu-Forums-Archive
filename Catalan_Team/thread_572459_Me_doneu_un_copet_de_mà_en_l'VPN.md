---
title: "Me doneu un copet de mà en l'VPN?"
date: 2007-10-10
forum: Catalan Team
---

### Post by lo gambusí on 2007-10-10
Salut!!

Estic connectat des de la xarxa de la Universitat Autònoma, xarxa limitada amb uns ports tancats per a que la gent no se pose l'emule i tal.

Això no m'ha preocupat fins ara, ja que puc passar perfectament sense descarregar-me pel·lícules i això. Lo problema m'ha vingut ara, que estic donant un cop de mà a uns companys en una web, i que per entrar com a webmestre i modificar-la necessito obrir los ports estos. He preguntat i m'han dit que he de configurar la connexió VPN, com a diu a la web [http://www.uab.es/servlet/Satellite?cid=1096481812575&pagename=i-UAB%2FPage%2FTemplateGenericHeaderSite]("http://www.uab.es/servlet/Satellite?cid=1096481812575&pagename=i-UAB%2FPage%2FTemplateGenericHeaderSite") m'he posat a fer-ho seguint lo tutorial per a linux que hi ha  [http://www.uab.cat/servlet/Satellite?blobcol=urldocument&blobheader=application%2Fpdf&blobkey=id&blobtable=iDocument&blobwhere=1096481405178&ssbinary=true]("http://www.uab.cat/servlet/Satellite?blobcol=urldocument&blobheader=application%2Fpdf&blobkey=id&blobtable=iDocument&blobwhere=1096481405178&ssbinary=true")i arribo a un punt en que no m'aclarixo.

Estic just on diu Configuració del Client. Em demana de crear un arxiu (que ja tinc creat sense que l'haigue fet jo) anomenat  /etc/ppp/options.pptp i a partir d'aquí ja me perdo. Suposo que és qüestió de no saber interpretar les indicacions que me dóna, així que  us agraïria que m'expliquesseu pas per pas com s'interpreta, i així a la pròxima vegada ja ho sabré fer per mi mateix :)

moltes gràcies!^^

---

### Post by papapep on 2007-10-10
Si vols es pot fer per aquí, però el document que referencies és bastant clar i crec que seria molt més adeqüat que tu preguntessis en concret què no entens. 
Per a fer-ho sense convertir-ho en un via crucis la millor manera seria connectant-te al canal d'irc ubuntu-cat de freenode.org i seria molt més àgil, ja que aquesta via, el fòrum, no és precissament àgil per preguntes curtes i ràpides.

---

### Post by lo gambusí on 2007-10-10
Bé, quasi que preferixo dir-t'ho per aquí, perquè això de l'IRC no me va massa bé.

Me quedo penjat a partir d'aquí: 

[I][B]Configuració del client:
El directori de configuració del client pptp és: /etc/ppp/
Creem el fitxer /etc/ppp/options.pptp (contindrà opcions comunes
a tots els túnels que creem) amb el següent contingut:
lock noauth nobsdcomp nodeflate
Afegim la següent línia al fitxer /etc/ppp/chap-secrets que conté
usuaris i paraules clau:
NIU PPTP paraula_clau *[/B]
On diu NIU hem de posar el nostre NIU (el que fem servir per entrar
a les aplicacions corporatives com ara el correu electrònic) i on diu
paraula_clau hem de posar la nostra paraula clau associada al NIU.
Per acabar la línia posem l'asterisc.
Creem el fitxer /etc/ppp/peers/uab amb els paràmetres de
configuració del túnel:
pty "pptp vpngw.uab.es --nolaunchpppd"
name NIU
remotename PPTP
usepeerdns
defaultroute replacedefaultroute
file /etc/ppp/options.pptp
ipparam uab
connect "route add vpngw.uab.es gw `ip route |
grep default | cut -f3 -d' '`"
Com abans, on diu NIU hem de posar el nostre NIU, vpngw.uab.es és
el nom del servidor de VPN de la UAB i uab és el nom del túnel que
crearem.
Abans de donar la feina per acabada ens cal crear un parell d'scripts
que ens definiran les rutes per sortir a internet a través del túnel i les
esborraran quan l'aturem. També ens assignaran els servidors de
noms de la UAB com a preferents. Aquests scripts no modifiquen ni
esborren cap ruta ja definida al nostre ordinador ni cap servidor de
nom assignat pel nostre proveïdor d'accés a Internet.
Creem el fitxer /etc/ppp/ip-up.d/uab amb el contingut següent:
#!/bin/sh
cat /etc/ppp/resolv.conf | resolvconf -a tun0
I li donem permís d'execució:
chmod +x /etc/ppp/ip-up.d/uab
Per acabar, creem el fitxer /etc/ppp/ip-down.d/uab amb el
contingut següent:
#!/bin/sh
route del vpngw.uab.es
resolvconf -d tun0
I també li donem permís d'execució:
chmod +x /etc/ppp/ip-down.d/uab
I ja ho tenim. Ara només cal engegar el túnel per sortir a Internet a
través de la xarxa privada virtual de la UAB:
pon uab
Després de posar en marxa el túnel, si fem ifconfig veurem una
interfície de xarxa nova amb el nom ppp0.
Per aturar el túnel, ho farem amb la comanda:
poff uab
Després d'aturar-lo, la interfície de xarxa ppp0 desapar
[/I]

No entenc tot això de crear arxius i posar codis i no sé què... no ho he fet mai, i me fa cosa fer-ho sense saber.

Gràcies :)

---

