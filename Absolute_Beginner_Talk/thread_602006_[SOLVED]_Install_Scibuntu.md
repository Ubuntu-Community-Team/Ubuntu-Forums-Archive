---
title: "[SOLVED] Install Scibuntu"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by PacoCrespo on 2007-11-03
I have just leave behind windows and landed on ubuntu and I need to make Scibuntu works. I have run the script but it dosen't work, I tried with:

sudo chmod a+x scibuntu041-beta
sudo ./scibuntu041-beta

but I've obtain:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by Maestro23 on 2007-11-03
> **PacoCrespo said:**
> I have just leave behind windows and landed on ubuntu and I need to make Scibuntu works. I have run the script but it dosen't work, I tried with:

sudo chmod a+x scibuntu041-beta
sudo ./scibuntu041-beta

but I've obtain:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Run:

> sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgrade

Try your install again.

---

### Post by overdrank on 2007-11-03
> **PacoCrespo said:**
> I have just leave behind windows and landed on ubuntu and I need to make Scibuntu works. I have run the script but it dosen't work, I tried with:

sudo chmod a+x scibuntu041-beta
sudo ./scibuntu041-beta

but I've obtain:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Hi and welcome, In the terminal located under applications, accessories, terminal   enter the command ```
sudo dpkg --configure -a
``` And you should be good to go. Good luck!
Edit beaten by the Maestro23 :)

---

### Post by PacoCrespo on 2007-11-03
I've tried with 

elisa@elisa-laptop:~/Desktop$ sudo dpkg --configure -a
elisa@elisa-laptop:~/Desktop$ sudo apt-get update && sudo apt-get upgrade
elisa@elisa-laptop:~/Desktop$ sudo chmod a+x scibuntu041-beta
elisa@elisa-laptop:~/Desktop$ sudo ./scibuntu041-beta

and then the same 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I can't believe it dosen't work please excuse me this is my very first time with ubuntu

---

### Post by overdrank on 2007-11-03
> **PacoCrespo said:**
> I've tried with 

elisa@elisa-laptop:~/Desktop$ sudo dpkg --configure -a
elisa@elisa-laptop:~/Desktop$ sudo apt-get update && sudo apt-get upgrade
elisa@elisa-laptop:~/Desktop$ sudo chmod a+x scibuntu041-beta
elisa@elisa-laptop:~/Desktop$ sudo ./scibuntu041-beta

and then the same 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I can't believe it dosen't work please excuse me this is my very first time with ubuntu

Try ```
sudo apt-get install -f
```

---

### Post by PacoCrespo on 2007-11-04
I've tried 

elisa@elisa-laptop:~/Desktop$ sudo apt-get install -f

Obtaining

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

but it seems nothing happends, and then the same again

elisa@elisa-laptop:~/Desktop$ sudo chmod a+x scibuntu041-beta
elisa@elisa-laptop:~/Desktop$ sudo ./scibuntu041-beta
math|publ
E: Sub-process /usr/bin/dpkg exited unexpectedly
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
:confused:

---

### Post by PacoCrespo on 2007-11-05
Finally I tried with an alpha version and everything turned out ok, I think that something is wrong with the beta one, thank you for your help

---

### Post by Maestro23 on 2007-11-05
> **PacoCrespo said:**
> Finally I tried with an alpha version and everything turned out ok, I think that something is wrong with the beta one, thank you for your help

Good deal.  Please mark this SOLVED using the Thread Tools.

Thanks.:)

---

