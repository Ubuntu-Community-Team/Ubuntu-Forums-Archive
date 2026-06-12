---
title: "[SOLVED] Comapartir Ubuntu server amb WinXp"
date: 2008-12-16
forum: Catalan Team
---

### Post by carlesbm on 2008-12-16
Hola a tothom


   Us explico la meva història:
    Fa uns dies hem vaig posar a instal·lar en una maquina que tenia aparcada per casa el Ubuntu server, partint del tutorial que ha exposar al blog de [www.FORAT.info](www.FORAT.info) , be un cop vaig finalitzar la instal·lació vaig començar ha probar, que tal funcionava i tot semblava que funcionava correctament, fins que vaig probar de accedir a una carpeta que tinc compartida dins del servidor amb el portatil, on hi ha Win Xp, aquí hem vaig trobar que, a (Mis Sitios de Red ----- red MSwin ----- Grupo de trabajo "despatx" ) si que m'apareix Ubuntu server però quan he intentat accedir-hi hem demana un nom de usuari i la contrasenya, he probat amb les que utilitzo per als usuaris del server i res.

   Despres de dies de probar al final vaig crear un enllac atraves de internet [ftp://.](ftp://.)........ .net però no crec que aixó sigui lo més practic per un ordinador que estroba conectat en la mateixa xarxa local.

   Que es que no he fet be, que hem falta  per configurar?


   Gracies per ajudar-me altre cop

---

### Post by guillemsola on 2008-12-16
Hola, 

jo crec que ho hauries de fer configurant l'rxiu /etc/samba/smb.conf

Abans de res hauries de fer una còpia de seguretat per quan ho emboloquis tot molt.

Entenc que tens samba instalat, si no

sudo apt-get install samba

doncs bé edites el smb.conf i al final poses la info d'allò que vols compartir

> 
[nom_del_compartit]
path = /carpeta_a_compartir
available = yes
browsable = yes
public = yes
writable = yes


Una altra cosa que pots provar abans de res és comentar l'opció de seguretat securiy = user

> 
# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
;   security = user


això fa que no et demani la paraula de pas cada vegada.

També pots posar security = share, però crec que aleshores en definir el que vols compartir has d'afegir force user = usuari_autoritzat.

Al principi de l'arxiu hi ha el nom del grup de treball on has de posar el teu.

> 
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = DESPATX


L'arxiu té forces coses però tot bé comentant. Si no hi ha un munt de tutorials. Jo tot això ho he recitat una mica de memòria així que pot haver-hi alguna imprecisió però espero que et serveixi.

salut!

---

### Post by carlesbm on 2008-12-18
Ja ho he pogut solucionar gracies per tot, buscant per la red, he vist que no havia donat d'alta els usuaris i que hem faltava modificar els permisos per als usuaris

---

