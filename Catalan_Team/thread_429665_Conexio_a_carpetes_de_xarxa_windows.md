---
title: "Conexio a carpetes de xarxa windows"
date: 2007-05-01
forum: Catalan Team
---

### Post by boriffus on 2007-05-01
Porto uns dies barallant-m'hi i no me n'acabo de sortir, a veure si algú de vosaltres s' hi ha trobat mai o sap què pot estar fallant o què puc estar fent malament:
Vull que l' Ubuntu munti a l' iniciar, un parell de carpetes de xarxa que estan en un altre pc. Aquest pc té muntat un 2003 Server que no fa de controlador de domini ni tampoc hi ha cap domini actiu enlloc, és un grup de treball normal i corrent. Les carpetes compartides en qüestió es diuen "public" i "documents", estan compartides amb permisos totals per tothom i amb permisos de seguretat complets també per al compte que configuro des d' Ubuntu. La ip de la maquina amb 2003 server és 13.0.0.2.
El que jo he fet és el següent:
1. He creat un arxiu a /root/ que es diu .credentials i on hi ha guardades les dades de l' usuari amb què em vull conectar, de manera que .credentials conté:
username=nomusuari
password=password
2. He instal·lat smbfs, samba, samba-common y smbclient a Ubuntu.
3. He creat dues carpetes /media/public i /media/documents on vull muntar les carpetes de xarxa i els he canviat l' usuari i el grup propietari de root al meu usuari normal.
3. He modificat l' arxiu /etc/fstab i hi he afegit aquestes dues linies:
//13.0.0.2/public  /media/public  smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777	0	0
//13.0.0.2/documents  /media/documents  smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777	0	0
4. He donat permisos totals x tothom a /etc/fstab i a /usr/bin/smbmnt perquè puguin ser muntades per qualsevol usuari.

El problema és que quan Ubuntu arrenca es queda força estona "pensant" sense dir res, acaba d' iniciar però les carpetes no es munten del tot: si intento entrar-hi em diu alguna cosa aixi com "error E/S". Llavors, des del terminal, si faig un sudo umount /media/carpeta es queda pensant una estona fins que sembla les desmonta. I el més curiós és que llavors si faig un sudo mount -a les carpetes es munten i les puc fer servir correctament i tot.
Ja he probat de canviar smbfs per cifs i res de res.
La veritat és que ja no sé què més probar, això que a l'iniciar no es muntin del tot i que després ho facin quan li faig un mount -a em despista completament, a veure si algú em pot donar alguna "llum".
Gràcies!

---

