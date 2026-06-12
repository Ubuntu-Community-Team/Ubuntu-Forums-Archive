---
title: "Installing Drivers"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Ammaro on 2007-10-14
ALright is there a command line to run .run files as admin?
I know its going to start with sudo but whats the rest?

Btw im trying to install new ATI drivers so I can increase my resolution.

---

### Post by overdrank on 2007-10-14
> **Ammaro said:**
> ALright is there a command line to run .run files as admin?
I know its going to start with sudo but whats the rest?

Btw im trying to install new ATI drivers so I can increase my resolution.

Hi and what is the model of the card and which version are you using  Feisty, Gutsy?

---

### Post by Ammaro on 2007-10-14
> **overdrank said:**
> Hi and what is the model of the card and which version are you using  Feisty, Gutsy?

Im using Gusty, and its an ATI mobility radeon X1400.
I have the driver on my flash drive and I just want to run it.

---

### Post by overdrank on 2007-10-14
> **Ammaro said:**
> Im using Gusty, and its an ATI mobility radeon X1400.
I have the driver on my flash drive and I just want to run it.

Ok I am not familiar with Gutsy but have you tried to enable the restricted drivers located under system, administration, restricted driver manager?
And this may help you add resolutions
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by defrex on 2007-10-14
Where did you get the driver? Is it a Windows driver? 'Cause that won't work. The restricted driver manager is your best bet.

---

### Post by Pumalite on 2007-10-14
ATI x1400:

Re: Feisty and Gutsy not working with ATI X1400
This is a solution from [http://www.mikesplanet.net/2007/04/i...4-ati-x-cards/](http://www.mikesplanet.net/2007/04/i...4-ati-x-cards/)
and I listed it on [http://kubuntuforums.net/forums/index.php?topic=3086249](http://kubuntuforums.net/forums/index.php?topic=3086249)

Many people are having problems installing Ubuntu 7.04 (Feisty Fawn) on machine with ATI X**** series video cards. This is caused by this bug that unfortunately could not fixed before the release of Ubuntu 7.04.

This quick guide will get Feisty installed and X.org 7.2 up and running.

Boot using PC (Intel x86) alternate install CD for Ubuntu or Kubuntu.
Start text mode installer and install Ubuntu/Kubuntu.
Finish Install and reboot.
Update package list and upgrade any packages needed.
sudo apt-get update
sudo apt-get dist-upgrade
Install fglrx closed source driver for ATI video cards.
sudo apt-get install xorg-driver-fglrx
Update loaded modules.
sudo depmod -a
Configure /etc/X11/xorg.conf
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
Reboot
Ubuntu 7.04 should now boot into GDM/KDM.

Hope it helps.

---

### Post by Ammaro on 2007-10-14
No its a linuxdriver.

---

### Post by Frak on 2007-10-14
> **Ammaro said:**
> No its a linuxdriver.
Follow pumalite, he/she has a good suggestion.

---

### Post by Ammaro on 2007-10-14
Now it says 

The software source for the package

   xorg-driver-fglrx

 is not enabled.

What do I do?

---

### Post by Pumalite on 2007-10-14
He

---

### Post by Ammaro on 2007-10-14
Ive tried sudo apt-get install xorg-driver-fglrx
but ti doesnt work

---

### Post by Pumalite on 2007-10-14
Are you connected to the Internet?. (wired)

---

### Post by Frak on 2007-10-14
> **Ammaro said:**
> Ive tried sudo apt-get install xorg-driver-fglrx
but ti doesnt work
Did you try just using the restricted drivers dialog.

@Pumalite, just making sure ;)

---

