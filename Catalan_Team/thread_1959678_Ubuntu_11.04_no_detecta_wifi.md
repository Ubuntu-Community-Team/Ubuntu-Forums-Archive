---
title: "Ubuntu 11.04 no detecta wifi"
date: 2012-04-16
forum: Catalan Team
---

### Post by aniues on 2012-04-16
Molt bones,

sóc novell absoluta en aquest sistema operatiu, i amb  poca experiència en informàtica en general. Per tant, perdoneu si no  m'expresso amb la precissió requerida.

Ja fa una setmana vaig instal·lar ubuntu 11.04 al meu portàtil HP Compaq Presario c700.
La  instal·lació va anar bé, tot correcte, però quan vaig intentar  connectar-me a la Xarxa, no va ser capaç de trobar la wifi. Detecta  totes les wifis del veïnat, excepte la meva.
Vaig pensar que era  perquè potser estava oculta, i vaig provar de connectar-me amb el meu  mòbil i amb l'Ipad del meu company; en tots dos dispositius la va  detectar a la primera, i s'hi va connectar correctament. 
L'he dut a la feina (tenim wifi) i la detecta i s'hi connecta sense problemes.
He consultat amb un company de feina (usuari d'ubuntu de fa anys), i ell m'ha donat pistes sobre el que podia fallar: 
-  he mirat si el driver propietari era el causant de tot (el vaig  desactivar, no detectava res, el vaig activar un altre cop.) (Control de  propietat STA d'adaptador de xarxa sense fil de Broadcom)
- he actualitzat tot el que s'ha d'atualitzar

No entenc que pot passar. He cercat a d'altres fils, i no n'he trobat cap que tracti alguna cosa semblant a la que em passa.
em podeu tirar un cop de mà?
Gràcies

---

### Post by wgarcia on 2012-04-16
Potser el primer pas és saber exactament quina tarja inalàmbrica té el teu sistema. 

Per això obre una terminal (Tecla súper -> escriu: terminal) i aquí escrius 

```
lspci -nn | grep -i broadcom
```

i enganxa el que surt.

---

### Post by akyra on 2012-04-16
Si detecta altres wifis des de Ubuntu no sembla que sigui la tarja.

Que et puguis connectar des del teu mòbil o altre dispositiu si ja ho havies fet abans et permetria connectar-te encara que estigui oculta.

L'altre cosa que pot ser es que tinguis filtre per MAC, a les hores hauries d'afegir la MAC del teu portatil.

Quin tipus d'encriptació tens habilitada?

Salutacions.

---

### Post by aniues on 2012-04-16
@[wgarcia]("http://ubuntuforums.org/member.php?u=242060"): 

Broadcom Corp. BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)

---

### Post by aniues on 2012-04-16
@akyra

**WPA-PSK**

---

### Post by akyra on 2012-04-16
Has mirat el filtre MAC i la no visibilitat conectant-te per cable?
Per la encriptació no hauria d'haver problema.

Adeu

---

### Post by aniues on 2012-04-16
Hola,
com puc mirar aixo del filtre de la mac? 
Tampoc em puc connectar per cable...
Adeu.

---

### Post by albandy on 2012-04-16
Abans de continuar, jo miraria de connectar-me amb un dispositiu que no s'hagi connectat mai a la teva wifi.

Si funciona segurament és un problema del driver amb la forma que treballa el teu router.
Si no funciona, ja saps que és un problema del router amb lo que hauràs de descartar el que ja t'han dit:

- Bloqueig per MAC
- Xarxa oculta
- canviar canal wifi

De totes formes: [http://ubuntuforums.org/showthread.php?t=1785881](http://ubuntuforums.org/showthread.php?t=1785881)
encara que en aquest cas, no li funcionava cap xarxa.

---

### Post by akyra on 2012-04-16
Connectarte per cable hauries de poder, no té sentit no poder-se connectar.

Has probat simplement en treure l'alimentació del router, deixar pasar 30s i tornar a donar alimentació?

Salutacions

---

### Post by aniues on 2012-04-16
Albandy,
 
He connectat un altre dispositiu sense cap problema. 


 Ara estic a la biblioteca, connectada al wifi. Pel que sembla el problema és amb la meva.
 Ara que puc, provaré el mètode que m'has recomanat, a veure què. Gràcies!
 

 Akyra,
 

 Sí, hauria de poder connectar-me per cable. Però no. I l'Iplus, que es connecta per cable, funciona correctament: vull dir que es connecta sense problemes.
 
I, ehem, sí: el primer que vaig fer va ser fer servir el sentit comú... apagar i tornar a encendre.;)
Crec que deu ser el has suggerit de la MAC.


A reveure,

---

### Post by wgarcia on 2012-04-16
És estrany que l'únic punt d'accés que no detecti sigui el teu. Quina versió d'Ubuntu tens? A l'Ubuntu 11.04 hi havia un problema amb el controlador STA, que se solucionava instal·lant el controlador b43. Però el problema feia que no es veiés cap xarxa. 

De totes maneres si vols provar a veure si és aquest el problema, hauries d'aconseguir connectar-te per cable de xarxa (perquè si et quedes sense cap connexió a Internet serà més difícil després arreglar les coses), i aquí pots provar obrir una terminal i entrar:

sudo apt-get install b43-fwcutter firmware-b43-installer

No sé si et desinstal·larà el STA o et demanarà que ho facis, després hauries de reiniciar i comprovar si ara es veu el punt d'accés WIFI o no.

---

### Post by aniues on 2012-04-16
He seguit les passes del fil que m'ha suggerit Albandyl, i ara ja em puc connectar sense problemes: m'ha detectat la wifi en encendre l'ordinador.
Moltes gràcies!

---

