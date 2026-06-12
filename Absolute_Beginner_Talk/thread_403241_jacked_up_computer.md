---
title: "jacked up computer"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by metzy85 on 2007-04-06
i deleted the partion ubuntu was on through windows and the drive showed up in mycomputer but for some reson when i go and load my computer is says grub loading then some error 17 so i need to know how to fix this

---

### Post by jhenager on 2007-04-06
You are going to need to reinstall Ubuntu.

---

### Post by metzy85 on 2007-04-06
is this going to mess up my windows is there a way not to reinstall it

---

### Post by pissedoffdude on 2007-04-06
> **metzy85 said:**
> i deleted the partion ubuntu was on through windows and the drive showed up in mycomputer but for some reson when i go and load my computer is says grub loading then some error 17 so i need to know how to fix this

Do you have your windows cd? If so then put it in ur cd drive reboot then go to the recovery mode and type ```
FIXMBR
``` followed by the command ```
FIXBOOT
```

---

### Post by JustBrowsing on 2007-04-06
Download: [http://forjamari.linex.org/frs/download.php/533/sgd_0.9588.iso.gz]("http://forjamari.linex.org/frs/download.php/533/sgd_0.9588.iso.gz")

It's a zipped .iso image file with Super Grub Disk on it. This will allow you to restore your Windows MBR (Master Boot Record)

---

### Post by kinematic on 2007-04-06
you don't need to reinstall ubuntu,just the windows bootloader.
boot from your windows install disk and go to the recovery console...then type fixboot or fixmbr(not sure wich one).
that should reinstall the windows bootloader.

---

### Post by metzy85 on 2007-04-06
ok so i don't have a windows cd i have a dell and the cd restore stuff is kept on there 

and to the link u have on there is not good so fix that please

so now wut do i need to do i would like to get this working cause i hate not having my laptop

---

### Post by metzy85 on 2007-04-06
i really need help i can not figure this out i have no xp cd and i have this grub error wut do i need to do to make my laptop work again before i go crazy

---

### Post by medad on 2007-04-06
Try this link.  [http://sgd.howto-linux.de/]("http://sgd.howto-linux.de/").  It should let you download either the archived version or the iso version.

Does the installation CD give you any options when you boot with it?

---

### Post by metzy85 on 2007-04-06
ok so i burn to disk from power iso that does not even work and the only thing i can do on my laptop right now is but linux of the live cd I am pissed i messed this up 

and that link well most the readme's where is spanish and right now i would like my laptop working before easter i do not feel like messing with ghandi when i call dell for xp cd will they even do that right now i am screwed i need to be able to boot to windows and well how can i do this

---

### Post by Maestro23 on 2007-04-06
> **metzy85 said:**
> ahhh yeah if u mean the linux cd yes i can boot to that through live cd but like i said i have no xp cd

might i ask wut i do with this iso burn to disk and put that in on start up and will this fix the problem of the mbr

Looks like he wants you to d/l SuperGrub.  Here is the webpage so you will know what it does.
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by metzy85 on 2007-04-06
this seems to be the thing i think i thank you very much i will still use my live cd often to boot linux but i am a bit to stupid to figure it out thank you for ur time and interest in helping me i will tell u if it works

---

### Post by Maestro23 on 2007-04-06
> **metzy85 said:**
> this seems to be the thing i think i thank you very much i will still use my live cd often to boot linux but i am a bit to stupid to figure it out thank you for ur time and interest in helping me i will tell u if it works

No prob man. Good luck.

---

### Post by metzy85 on 2007-04-07
ummmm i don't know if this is it it does not seem to have anything to fix the mbr and if it does well i am not seeing and need some guide on where it would be located

---

### Post by metzy85 on 2007-04-10
k i got a windows cd and when i go to recovery mode it ask for passwrod wut is the password

---

