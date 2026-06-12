---
title: "iMac 21.5 inch, no sound"
date: 2010-03-21
forum: Apple Hardware Users
---

### Post by fastop on 2010-03-21
Ive checked if anything was muted... But its all unmuted. Any help?

---

### Post by jamesey on 2010-03-21
try this
```
sudo apt-get install linux-backports-modules-alsa-karmic-generic
```

---

### Post by fastop on 2010-03-21
Thanks but it said it couldn't find the package! Is there any other ways of getting this?

---

### Post by fastop on 2010-03-21
I found the package on the ubuntu website and installed it from their instead. Still no sound...

---

### Post by linuxopjemac on 2010-03-22
can you give me the output of
```
sudo dmidecode -s system-product-name
```

---

### Post by ZeroLinux on 2010-03-22
You need to run Terminal and from there start alsamixer
Go to to Front Speaker and press "m" to unmute speaker

And to have backports you need to check all checkboxes in the first tab of repositories sources

BTW in Lucid sound works out of box but after unmuting front speaker in alsamixer
But Mic need to be boosted

---

### Post by fastop on 2010-03-22
When I do that it says: cannot open mixer: No such file or directory

---

### Post by linuxopjemac on 2010-03-22
in a terminal:
```
alsamixer
```

---

### Post by fastop on 2010-03-22
Oops sorry [linuxopjemac]("http://ubuntuforums.org/member.php?u=468914"), i did not see your post before :D. When i run "sudo dmidecode -s system-product-name" in terminal
It says "iMac10,1"
And when i do "alsamixer" in the terminal it says "cannot open mixer: No such file or directory"

---

### Post by linuxopjemac on 2010-03-22
```
sudo apt-get update
sudo apt-get install alsa-utils
alsamixer
```

---

### Post by fastop on 2010-03-22
"joe@joe-desktop:~$ sudo apt-get install alsa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded."

Tried running alsamixer again but still said no such file or directory..

---

### Post by linuxopjemac on 2010-03-22
you could try gnome-alsamixer, but I don't understand you don't have alsamixer, really strange.

```
sudo apt-get install gnome-alsamixer
```

---

### Post by fastop on 2010-03-22
Okay I downloaded and installed that, I open it fine, click "edit" and "sound card properties" and it crashed. Maybe it could be due to the fact im using 10.04? As there are still some bugs.

---

### Post by linuxopjemac on 2010-03-22
aha, yes, that's possible...I don't know about Lucid Lynx (yet).

---

### Post by fastop on 2010-03-22
I think I will try a clean downgrade, and see if that fixes the problem! Its a shame because i really like 10.04 so far... Oh well, i will just have to wait until April :P

Thank you for your help :)

---

### Post by ZeroLinux on 2010-03-22
No, In lucid 10.04 sound works well. Just [download]("http://releases.ubuntu.com/10.04/ubuntu-10.04-beta1-desktop-amd64.iso") and install it. Sound works even from LiveCD without installation (unmute Front Speaker before) You can test sound from Folder examples right on Desktop. It really works without installing any additional packages. I have iMac 10.1 21.5 and know it for sure. You can daownload and see for youself.

---

### Post by fastop on 2010-03-23
Okay I installed 9.10, installed alsamixer, run it in terminal, pressed m to unmute. Still no sound...

---

### Post by linuxopjemac on 2010-03-24
```
sudo apt-get install linux-backports-modules-alsa-karmic-generic
```

reboot, then unmute again (if needed)...hopefully you have sound then

---

### Post by xvila on 2010-03-24
> **linuxopjemac said:**
> ```
sudo apt-get install linux-backports-modules-alsa-karmic-generic
```

reboot, then unmute again (if needed)...hopefully you have sound then


Also, once the suggestions above have been followed, replace:


options snd-hda-intel power_save=10 power_save_controller=N

with

options snd-hda-intel model=imac27 power_save=10 power_save_controller=N

in the bottom line of the file

/etc/modprobe.d/alsa-base.conf

and reboot

It works in my new (March 10th) iMac 21.5

good luck

---

### Post by fastop on 2010-03-24
> **xvila said:**
> Also, once the suggestions above have been followed, replace:


options snd-hda-intel power_save=10 power_save_controller=N

with

options snd-hda-intel model=imac27 power_save=10 power_save_controller=N

in the bottom line of the file

/etc/modprobe.d/alsa-base.conf

and reboot

It works in my new (March 10th) iMac 21.5

good luck

Thankyou! This worked perfectly :)

---

### Post by linuxopjemac on 2010-03-24
great solution for the 10,1 imac...I will post it on my own website.

---

