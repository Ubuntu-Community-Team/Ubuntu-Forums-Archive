---
title: "Problem changing firestarter config"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Amplidude on 2007-07-13
Firestarter won't start because it says eth2 is not ready, but there is no eth2. I have two NIC's (eth0 & eth1). When I look at firestarter's config, it says 
> # --(Internal Interface--)
# Name of internal network interface
INIF="eth2"
If I try to change the eth2 to eth1, the machine tells me that I cannot modify the file because the disk is write protected.

Is there a solution other than uninstalling and reinstalling Firestarter?

Please help.

---

### Post by felicity on 2007-07-13
If it says the disk is write protected it probably means you need to edit the file with superuser privileges. Try opening that file and editing it with sudo. (like sudo gedit <location and name of file>)

---

### Post by overdrank on 2007-07-13
> **Amplidude said:**
> Firestarter won't start because it says eth2 is not ready, but there is no eth2. I have two NIC's (eth0 & eth1). When I look at firestarter's config, it says 

If I try to change the eth2 to eth1, the machine tells me that I cannot modify the file because the disk is write protected.

Is there a solution other than uninstalling and reinstalling Firestarter?

Please help.

HI have you tried to run the wizard on firestarter. It is located under firewall, wizard. It is funny to me to edit from command line on a program to give you a gui to configure. That is just me!:guitar:

---

### Post by Amplidude on 2007-07-13
> **felicity said:**
> If it says the disk is write protected it probably means you need to edit the file with superuser privileges. Try opening that file and editing it with sudo. (like sudo gedit <location and name of file>)

Hi felicity. I tried that: didn't work.

> HI have you tried to run the wizard on firestarter. It is located under firewall, wizard. It is funny to me to edit from command line on a program to give you a gui to configure. That is just me!

Nope, tried that too. It only shows two options to select from (eth0 & eth2)

Thanks.  Any other ideas?

---

### Post by Amplidude on 2007-07-13
> **Amplidude said:**
> Firestarter won't start because it says eth2 is not ready, but there is no eth2. I have two NIC's (eth0 & eth1). When I look at firestarter's config, it says 

If I try to change the eth2 to eth1, the machine tells me that I cannot modify the file because the disk is write protected.

Is there a solution other than uninstalling and reinstalling Firestarter?

Please help.

Another interesting aspect: how did Firestarter get eth2 into the setup in the first place???

Any ideas?

---

### Post by Amplidude on 2007-07-13
> HI have you tried to run the wizard on firestarter. It is located under firewall, wizard. It is funny to me to edit from command line on a program to give you a gui to configure. That is just me!

Duh! I was looking at the setup not the wizard. The wizard ran and fixed the problem. :redface:

Thanks Overdrank and Felicity for your help.

---

