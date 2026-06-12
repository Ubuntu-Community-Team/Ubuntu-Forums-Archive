---
title: "Versió linux x86??què aconselleu?"
date: 2016-03-22
forum: Catalan Team
---

### Post by pserra on 2016-03-22
Bona nit,
tinc un portàtil de 7 anys que té un processador de 32 bits.
La darrera versió de ubuntu que tinc instal·lada és la de 14.10... veig que la 15.10 no hi ha la versió de 32bits.
El cas és que no estic gaire content amb el rendiment del 14.10 (va lent....) ja quan em carrega em surt error intern..
aconselleu alguna altre versió de linux per poder anar ràpit amb el meu vell portàtil?(linux mint...)
GRÀCIES

---

### Post by pserra on 2016-03-22
O potser baixar la versió "mate" 15.04?  què aconselleu els experts?

Gràcies

---

### Post by wgarcia on 2016-03-23
Sí que hi ha versió de 32 bits de la 15.10:

[http://releases.ubuntu.com/15.10/ubuntu-15.10-desktop-i386.iso](http://releases.ubuntu.com/15.10/ubuntu-15.10-desktop-i386.iso)

Ara bé, algunes observacions:

1) No pots passar directament de la 14.10 a las 15.10, has de primer actualitzar a la 15.04.
2) Si vols una imatge lleugera dins de la família de sabors Ubuntu, la recomanable és Lubuntu. Si has de fer instal·lació de zero jo li posaria Lubuntu 14.04, i quan surti la 16.04 m'actualitzaria a aquesta versió. 
3) Ubuntu Mate no és una versió "lleugera", és a dir per equips antics. És més que res una versió d'escriptori per als que els agrada el "paradigma" d'escriptori basat en menús, panell inferior, etc.
4) Si vols distribucions lleugeres fora de la família Ubuntu, hi ha un munt, per exemple Puppy Linux, Simplicity, i d'altres. Ara bé, Lubuntu va molt bé a equips antics i en la meva opinió està molt ben dissenyada. També tens l'opció de Linkat, que és una Lubuntu modificada pel Departament d'Ensenyament de la Generalitat de Catalunya per als centres educatius.

---

### Post by pserra on 2016-03-23
Merci,
donc provaré el lubuntu...
Perdona per aquesta pregunta de 'novell'... 
hi ha alguna manera de actualització automàtica a lubuntu o només puc descarregar la ISO i instal·lar  manualment des de 0?
Merci per els teus savis consells... una  altre vegada wgarcia.

---

### Post by pserra on 2016-03-23
ara he intentat acutalitzar dintre el ubuntu...
però tinc problemes amb els pàquets... potser per això em va més lent....




[SIZE=1]
peter@pere-PC:~$ sudo apt-get update && sudo apt-get dist-upgrade
[sudo] password for peter: 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security InRelease                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates InRelease                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security Release                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed InRelease                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic Release.gpg                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates Release.gpg                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports Release.gpg               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed Release.gpg                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic Release                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates Release                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports Release                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed Release                    
Err [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main Sources              
  404  Not Found [IP: 91.189.88.152 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe Sources          
  404  Not Found [IP: 91.189.88.152 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/multiverse Sources        
  404  Not Found [IP: 91.189.88.152 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted Sources        
  404  Not Found [IP: 91.189.88.152 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main i386 Packages        
  404  Not Found [IP: 91.189.88.152 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe i386 Packages    
  404  Not Found [IP: 91.189.88.152 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/multiverse i386 Packages  
  404  Not Found [IP: 91.189.88.152 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted i386 Packages  
  404  Not Found [IP: 91.189.88.152 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main Translation-ca_ES    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main Translation-ca       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main Translation-en       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/multiverse Translation-ca_ES
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/multiverse Translation-ca 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/multiverse Translation-en 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted Translation-ca_ES
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted Translation-ca 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted Translation-en 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe Translation-ca_ES
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe Translation-ca         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe Translation-en         
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/main Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/universe Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/multiverse Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/restricted Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/main i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/universe i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/restricted i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/main Translation-ca_ES
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/main Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/multiverse Translation-ca_ES
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/multiverse Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/restricted Translation-ca_ES
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/restricted Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/universe Translation-ca_ES
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/universe Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/universe Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/main Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/universe Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/multiverse Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/restricted Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/main i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/universe i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/main Translation-ca_ES
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/main Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/multiverse Translation-ca_ES
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/multiverse Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/restricted Translation-ca_ES
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/restricted Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/universe Translation-ca_ES
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/universe Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/universe Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/main Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/universe Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/multiverse Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/restricted Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/main i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/universe i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/main Translation-ca_ES
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/main Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/multiverse Translation-ca_ES
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/multiverse Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/restricted Translation-ca_ES
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/restricted Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/universe Translation-ca_ES
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/universe Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/universe Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed/universe Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed/main Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed/multiverse Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed/restricted Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed/universe i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed/main i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed/restricted i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed/main Translation-ca_ES
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed/main Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed/multiverse Translation-ca_ES
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed/multiverse Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed/restricted Translation-ca_ES
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed/restricted Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed/universe Translation-ca_ES
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed/universe Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-proposed/universe Translation-en
W: No s'ha pogut obtenir [http://security.ubuntu.com/ubuntu/dists/utopic-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/utopic-security/main/source/Sources)  404  Not Found [IP: 91.189.88.152 80]

W: No s'ha pogut obtenir [http://security.ubuntu.com/ubuntu/dists/utopic-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/utopic-security/universe/source/Sources)  404  Not Found [IP: 91.189.88.152 80]

W: No s'ha pogut obtenir [http://security.ubuntu.com/ubuntu/dists/utopic-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/utopic-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.88.152 80]

W: No s'ha pogut obtenir [http://security.ubuntu.com/ubuntu/dists/utopic-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/utopic-security/restricted/source/Sources)  404  Not Found [IP: 91.189.88.152 80]

W: No s'ha pogut obtenir [http://security.ubuntu.com/ubuntu/dists/utopic-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/utopic-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.152 80]

W: No s'ha pogut obtenir [http://security.ubuntu.com/ubuntu/dists/utopic-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/utopic-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.152 80]

W: No s'ha pogut obtenir [http://security.ubuntu.com/ubuntu/dists/utopic-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/utopic-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.88.152 80]

W: No s'ha pogut obtenir [http://security.ubuntu.com/ubuntu/dists/utopic-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/utopic-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.88.152 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic/main/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic/universe/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic/restricted/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-updates/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic-updates/main/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-updates/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic-updates/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-updates/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic-updates/restricted/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-updates/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-backports/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic-backports/main/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-backports/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic-backports/universe/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-backports/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-backports/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-backports/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-backports/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-backports/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-backports/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/universe/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/main/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/restricted/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: No s'ha pogut obtenir [http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

E: Alguns índex no s'han pogut baixar. S'han descartat, o en el seu lloc s'han emprat els antics.
peter@pere-PC:~$ 

[/SIZE]

Com ho pùc arreglar?

---

### Post by wgarcia on 2016-03-24
Sembla com si no tinguessis connexió a Internet. Hi ha connexió per a altres aplicacions?

---

### Post by pserra on 2016-03-24
Hola..
merci wgarcia...
NO SÉ QUE EM PASSAVA AMB EL UBUNTU... PERÒ TENIA PROBLEMA AL ACTUALITZAR PAQUETS..... I EM FEIA BAIXAR RENDIMENT...
ara ja m'he passat a LUBUNTU.. (quan surti la16.04 m'hi passaré)....
Ara ja em va superràpit l'internet.... i tot... La interfície un cop t'hi acostumes.....

GRÀCIES PER EL SUPORT....

---

