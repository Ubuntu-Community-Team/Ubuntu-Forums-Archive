---
title: "How do I install Kubuntu via Boot Options?"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by Jibbly Wibbly on 2006-04-26
Hi I'm new to linux but Ubuntu/Kubuntu is just like windows without all the rubbish, bugs, viruses, mad system requirements, crashes. So I'll feel right at home using it.

However after fooling around with the live cd part of the new beta disc on my fancy shmancy pc, I have decided to take my dads old manky laptop and turn it into something useful with Kubuntu. I thought that this would be piece of cake until I realised the laptop is only powerful enough to run Kubuntu on the HDD but not from the CD. It runs at a stable state but its too laggy to make it though the install process. Is there a way of using the F6 function to type in some command that will make it install without booting up Kubuntu first?

Thanks in advance!

---

### Post by alan_daniel on 2006-04-26
You can always install only the base system from an Ubuntu ISO CD and then log into your new terminal and install Kubuntu with this command:

$sudo apt-get install kubuntu-desktop

After that, a reboot will boot you into KDE

---

### Post by aysiu on 2006-04-26
Are you using Dapper? I think Dapper is both a live CD and installer CD.

Any previous release of Ubuntu (Breezy, Hoary, or Warty) has a separate live and installer CD. The installer CD should not load up Kubuntu before installing.

---

### Post by Jibbly Wibbly on 2006-04-26
Thanks Alan i'll try that!

---

### Post by aysiu on 2006-04-26
If you have a Breezy installer CD, you can do it. I don't have a single Dapper CD, and I have Dapper installed on both my computers.

Do a server Breezy install. Then ```
sudo apt-get update
sudo apt-get install base-config passwd
``` Then ```
sudo cp /etc/apt/sources.list /etc/apt/sources_breezy.list
sudo nano /etc/apt/sources.list
``` Every time you see the word *breezy*, replace it with *dapper* and then ```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install kubuntu-desktop
```

---

