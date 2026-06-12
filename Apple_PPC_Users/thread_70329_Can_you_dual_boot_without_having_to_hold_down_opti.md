---
title: "Can you dual boot without having to hold down option key on startup?"
date: 2005-09-29
forum: Apple PPC Users
---

### Post by Flaystus on 2005-09-29
So far holding option key is the only way.

Is there a way to fix this? And will I have to reformat again to do so.

I hope to know before I install a bunch of stuff.

While I'm at it. I take it ubuntu cannot read my OSX partition? So now I can't access my files there? (OH NOES my music!)

---

### Post by domesticatewhat on 2005-09-29
edit /etc/yaboot.conf add macosx=/dev/whateveryourdrivenumber then run ybin -v

if you want the dafult choice to be macosx then add defaultos=macosx to the end of yaboot. Don't forget to run ybin at the end.


You can share your mac drive by

"sudo mkdir /media/macosx"
"sudo mount -t hfsplus /dev/whateveryourdrivenumber /media/macosx"

You could also edit fstab to make this automatic.

---

### Post by Flaystus on 2005-09-29
I'll try the first part. What command lets you edit? Or can you do it from the GUI? While I'm at it how do I find the drive number OSX is on?

Warned you I'm very new.

update: i can't make changes to the yaboot.conf

---

### Post by aysiu on 2005-09-29
[QUOTE=Flaystus]I'll try the first part. What command lets you edit? Or can you do it from the GUI?[/QUOTE] ```
sudo gedit /etc/yaboot.conf
``` or ```
 sudo nano /etc/yaboot.conf
``` >  While I'm at it how do I find the drive number OSX is on?

Warned you I'm very new. ```
sudo fdisk -l
```

---

### Post by Flaystus on 2005-09-29
Thanks both of you. On it now.

THANK YOU!! :p

---

### Post by Flaystus on 2005-09-29
Tried the fdisk command. It doesn't see the mac partition that I can tell.

edit: nevermind. was just hard to read until I increased the terminal size and ran the command again.

If I can find the fstab I think I'm done.

edit edit: found fstab, no clue what to do in there

edit edit edit: under control I winged it and it worked. Thanks for all the assistance.

---

### Post by Ptero-4 on 2005-09-30
You can also do this if you want to use the "option" bootloader without having to press option. Go to the openfirmware (Can only be accessed at boot time, by pressing apple+option+o+f), and type: setenv boot-command multi-boot and then type shut-down.
Turn on your Mac and you'll see the "option" multiboot screen right away. To undo that go into the openfirmware and type: reset-nvram , reset-all and then shut-down. And turn on your Mac, you'll see the folder with a blinking "Finder" face for some time and then yaboot will kick in.

---

