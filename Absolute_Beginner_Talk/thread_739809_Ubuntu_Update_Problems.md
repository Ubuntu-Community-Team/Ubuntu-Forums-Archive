---
title: "Ubuntu Update Problems"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by dogdog on 2008-03-30
I am running Ubuntu v 7.10 on Dell desktop PC.
On start up, the applet on the system tray shows that updates are available but when I click on applet, go to Update Manager and click on install updates the system just hangs and I have to reboot.
If, on start up, I go to Terminal and use “sudo apt-get update” I get the message “unable to lock administration directory (/var/lib/dpkg/)”.
I have then tried:
sudo  rm /var/lib/dpkg/lock    followed by
sudo apt-get update
and some of updates seem to install but not all and basic problem of Update Manager hanging remains.
The other symptom is that the PC seems “active” – flashing light indicating HD activity – even though nothing is being done by me and the PC is slow to respond to mouse movements/commands.

Any suggestions??

---

### Post by paydaydaddy on 2008-03-30
Have you tried this? Open a terminal and type in or cut and paste the following command. Then close the terminal and try synaptic again.
```

sudo dpkg --configure -a
```

---

### Post by taavikko on 2008-03-30
```
sudo dpkg --configure -a
```
```
sudo apt-get -f install
```
repeat till no more errors.
```
sudo apt-get update && sudo apt-get upgrade
```

Remember, only one package-manager open at a time

---

### Post by c-ron on 2008-03-30
Nice.

---

### Post by dogdog on 2008-03-30
It would be helpful to know what you think is going wrong??

What is dpkg??

What do following instructions do:

sudo dpkg --configure -a

sudo apt-get -f install

---

### Post by taavikko on 2008-03-30
sudo dpkg --configure -a
Tries to like it says configure all packages, for any errors

sudo apt-get -f install
trys to fix dependencies.

 dpkg - package manager for Debian

---

### Post by dogdog on 2008-03-30
ran: sudo dpkg --configure -a            nothing reported
ran: sudo apt-get -f install
   0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded

ran: sudo apt-get update                 seemed to run ok

BUT: 1 update still outstanding
         PC continues to "whir" for no reason
         problem remains

any other thoughts??

---

### Post by dogdog on 2008-03-30
I thoght that I would use Synaptic Package Manager to reinstall Update Manager.

But Synatptic Package Manager will not open?? 
       via System-Administration-Synaptic Package Manager

---

### Post by taavikko on 2008-03-30
```
sudo apt-get update && sudo apt-get dist-upgrade
```

whats the output of this command
cat /etc/hosts /etc/hostname

What is your graphic-card?
and driver used?

---

### Post by dogdog on 2008-03-30
Synaptic Package Manager did open but after very long delay

---

### Post by dogdog on 2008-03-30
Updates now seem to have installed ok.

BUT PC is still "whirring" for no apparent reason.
Any suggestions how to resolve this as it is slowing down the PC - all thoughts much appreciated.

---

