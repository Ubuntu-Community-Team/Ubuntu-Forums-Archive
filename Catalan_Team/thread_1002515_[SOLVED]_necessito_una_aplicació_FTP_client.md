---
title: "[SOLVED] necessito una aplicació FTP client"
date: 2008-12-05
forum: Catalan Team
---

### Post by jinglada on 2008-12-05
Necessito una aplicació FTP client. Quina o quines recomaneu?

---

### Post by jinglada on 2008-12-05
He instal·lat el gFTP. si n'hi ha cap de millor ja m'ho direu.
Gràcies.

---

### Post by CarlesOriol on 2008-12-06
El nautilus fa perfectament la feina, i el konqueror/dolphin també.

(escriu a la barra d'adreça [ftp://.](ftp://.).. )

---

### Post by open-pitu on 2008-12-06
Ostres! No sabia que el nautilus el poguéssim connectar ftp.Ara ho he provat i si si, va perfecte! Endarrera pot quedar el gFTP...

---

### Post by jinglada on 2008-12-09
Doncs a mi no em funciona; em diu "No s'ha pogut mostrar "ftp.xxx.com" El Nautilus no pot gestionar aquest tipus d'ubicacions.

Amb el Konkeror ha funcionat a la primera. Ara provo quin em va millor.

---

### Post by CarlesOriol on 2008-12-09
> **jinglada said:**
> El Nautilus no pot gestionar aquest tipus d'ubicacions.

Sí, sí que pot.

---

### Post by jinglada on 2008-12-10
> **CarlesOriol said:**
> Sí, sí que pot.

No sé per què no pot amb un servidor però si que he connectat amb altres. En canvi amb Konkeror i gFTP he connectat amb tots.
El que no havia vist és que s'havia de fer des de "Llocs -> Connecta al servidor", pel que fa al *Nautilus* de l'*Intrepid*
Gràcies.

---

### Post by papapep on 2008-12-10
> El que no havia vist és que s'havia de fer des de "Llocs -> Connecta al servidor", pel que fa al Nautilus de l'Intrepid

No, no cal anar allà. Des de la barra d'adreces del Nautilus amb:

```
ftp://ftp.elservidor.com
```

funciona perfectament.
Potser sigui qüestió de la configuració del servidor al que intentes accedir que estigui en mode passiu o actiu i el Nautilus no ho sàpiga manegar.

---

### Post by jinglada on 2008-12-11
D'acord papapep, en tinc varis i em funcionen com tu dius, però el de ftp.fortunecity.com, al qual hi entro amb el gFTP i amb el Konkeror, amb el Nautilus diu: "No s'ha pogut mostrar els continguts de la carpeta. No s'han pogut visualitzar tots els continguts de «/ a ftp.fortunecity.com»: No s'ha pogut connectar amb l'ordinador"

en el gFTP dóna aquesta informació (he canviat el que m'ha semblat identificatiu):

'està cercant ftp.fortunecity.com
S'està intentant amb ftp.fortunecity.com:21
S'ha connectat a ftp.fortunecity.com:21
220 server ready. Enter Username.
USER el_meu_usuari

331 Welcome 'el meu usuari', enter password to login.
PASS xxxx
230-Welcome to FortuneCity.Com.
    
    Your quota is n0Kb.
    You have used n1Kb.
    
    If you have trouble downloading please try 
    using Passive(PASV) Mode.
    
230 User 'el meu usuari' login successful.
SYST

215 UNIX Type: L8
TYPE I

200 TYPE is now BINARY.
PWD

257 "/" is the current directory.
S'està carregant el llistat del directori / del servidor (elquesigui)
PASV

227 Entering Passive Mode (números)
LIST -aL

150 Starting ASCII transfer for file listing.
226 Transfer done. 28721 bytes transferred.

---

