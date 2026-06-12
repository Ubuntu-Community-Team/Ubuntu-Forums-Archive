---
title: "Problems regarding Network Printer"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by Kenas on 2006-02-17
Hi,
I am trying to configure a hpLaserJ 1100 wich is connected to my office LAN (Under Windows 2000 sever)
I have succesfully configured my SMB in Ubuntu (or that is wht i think so).
I can browse all shared folders from the Computer where the printer is installed.
Printer is sucessfully shared because other Windows users access to them normally.
My problems comes when I try to print something with my Ubuntu.
I have tried simple configurations such as Administration > Printers > New Printer > Printer in LAN > Windows (SMB) Printer > (it asks me for password *but it always gives me an error) and if i finish configuration with no success.

Can someone help me ?

---

### Post by Mellon on 2006-02-17
when it ask you for a password just hit cancel and wait a moment, after that look for  the windows PC that have the printer, it should be listened in the host space, the printer must appear in the print space.

---

### Post by patrick295767 on 2006-02-17
I havent yet finished too with installing everthg with network printing :-( 

but btw would someone by the way know to add a quota on the printing ? (like 30 pages a month)

thank you very much,

Pat'

---

### Post by Kenas on 2006-02-17
PASO 1 DE 2:

# Tipo de impresora:
Impresora en red -> Impresora Windows (SMB)

# Host:
barebone (o el nombre de vuestro equipo windows en la red *Name of the Server in Windows. Eg : \\Administrador)

# Impresora:
HPLaserj (o el nombre de recurso compartido que hayais elegido para vuestra impresora*Name of the printer that appears in shared document in Windows)

# Usuario:
ESTO ES IMPORTANTE, puesto que en mi caso Windows me denegaba el acceso a la impresora, no sé porque... ¬_¬ . Debemos escribir: Guest

# Contraseña:
Dejamos este campo en blanco.
NOTA: No hace falta tener activada la cuenta Guest de Windows XP.

This is exactly what i did. (Sorry for transalation)

WBR
Kenas

---

### Post by Kenas on 2006-02-17
"Unable to connect to SAMBA host, will retry in 60 seconds...ERROR: Connection failed with error NT_STATUS_LOGON_FAILURE"

---

### Post by Kenas on 2006-02-20
Can anyone Help me regarding this Problem ???

---

