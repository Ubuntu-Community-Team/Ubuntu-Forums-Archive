---
title: "ubuntu vista networking"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Sushubh on 2007-06-20
i have a ubuntu machine with two network cards.

one of these cards is connected to the modem which enables the net on this machine.

i have attached a vista machine using a crosswire network cable.

now i can run net on vista using my machine from xp using internet connection sharing feature... how to do that with ubuntu?

---

### Post by Skrynesaver on 2007-06-20
Try this thread 
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by Sushubh on 2007-06-20
so a GUI version is not developed yet? :(

---

### Post by Zzl1xndd on 2007-06-20
> **Sushubh said:**
> so a GUI version is not developed yet? :(

Well for the most part it is not a common request do to how cheap a router is.

---

### Post by Sushubh on 2007-06-20
:)

i guess i will get a 20 dollar switch and use samba (i think that's the one used for file sharing! right?)

---

### Post by Zzl1xndd on 2007-06-20
> **Sushubh said:**
> :)

i guess i will get a 20 dollar switch and use samba (i think that's the one used for file sharing! right?)

If you wanna do Internet Sharing a Router for the Internet and Samba for the File sharing, A switch is fine if your ISP provides you with more then 1 IP if not get a router.

---

### Post by Sushubh on 2007-06-20
umm i think the modem my ISP has given me works like a router... its a beetle 220bx model (chinese made) and we have used a switch to successfully share internet using a single line...

---

### Post by Zzl1xndd on 2007-06-20
> **Sushubh said:**
> umm i think the modem my ISP has given me works like a router... its a beetle 220bx model (chinese made) and we have used a switch to successfully share internet using a single line...

Just checked it out online it does look like that model functions as a router so a switch should do it.

---

### Post by Austin_KW on 2007-06-20
> **Sushubh said:**
> so a GUI version is not developed yet? :(

For a GUI
sudo apt-get install firestarter

when you start firestarter it will run a wizard and allow you to set up ICS similar to windows. Choose the dhcp option and it will allocate ip addresses to the client PCs. It you want to run samba on the connection, I think you have to setup firewall rules for the samba connection. Just check the log and enable the samba connections if it blocks them,

---

### Post by Sushubh on 2007-06-20
awesome! i will check it out. thx.

---

