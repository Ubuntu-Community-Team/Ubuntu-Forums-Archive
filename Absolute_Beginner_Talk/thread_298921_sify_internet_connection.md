---
title: "sify internet connection"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by libran_devil on 2006-11-13
im fed up with the installation of sify internet connection. for last five days im trying to install it but failing. im an absolute beginner and i wanna connect to internet from ubuntu so that i can avoid logging to windows. i hav downloaded their internet connection software which is [http://210.18.11.199:81/bbandclient/sifyconnect-1.3-bin.tar.gz](http://210.18.11.199:81/bbandclient/sifyconnect-1.3-bin.tar.gz). 
 now i can acces this file but dont kno what to do. plz help me. i dont kno how to install it for i think it can be done y double clicking it. plz help me im in deep trouble

---

### Post by lionelxp on 2007-03-03
Hey,

Well download the file to ur desktop, n extract the contents

now go to the acessories menu and pen terminal. Ovr there type the following
> 
cd Desktop

cd sify*

sudo ./install.sh

Now ur dialer has been installed. Everytime you wanna use it, jus open a terminal and type 

sifyd

sifyconnect -l                   "THis is to login"
sifyconnect -o                  "This is to logout"


sifyd has to be run everytime you start ur machine, its similar to the pcalert thing that runs in the background in windows

---

