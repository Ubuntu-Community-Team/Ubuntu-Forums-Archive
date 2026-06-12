---
title: "Ok...me again vmware install error"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by silentjudas on 2007-05-20
ok what do i do...nothing works, and i tried doing what it says but it doenst make any sense where to put it, and console doesnt work

---

### Post by silentjudas on 2007-05-20
anyone know?

---

### Post by hanzomon4 on 2007-05-20
You need to uninstall a previous vmware install. Try ```
sudo vmware-uninstall.pl
``` If you previously installed vmware from the repos try ```
sudo apt-get remove --purge vmware-server vmware-player
```

---

### Post by silentjudas on 2007-05-20
rrrrr

okay i did the first one
like i said, nothing
second one worked but told me i needed to use sudo apt-get autoremove, which i did earlier
i did it and i looked like it did it right
so i go back to synaptic
install vmserver

and the same dang error pops up...

---

### Post by silentjudas on 2007-05-20
i guess y'all are as stumped as i am....

---

### Post by zvacet on 2007-05-20
> second one worked but told me i needed to use sudo apt-get autoremove, which i did earlier

When?Run that command and see what is going to happend.if that don´t solve your problem then

```
cd /etc
```

Find vmware folder and delete it.

---

### Post by Psicolonia on 2007-05-20
how about forgetting vmware and sticking with virtual box. search virtual box in google and download the debian / ubuntu package. Install and BINGO. it's faster too and network connections inside the virtual box works great. It has guest additions too!

---

### Post by silentjudas on 2007-05-20
found the folder buuuuuuuuuuuuuuuuuut

"Cannot move "/etc/vmware" to the trash because you do not have permissions to change it or its parent folder."

---

### Post by silentjudas on 2007-05-20
> **Psicolonia said:**
> how about forgetting vmware and sticking with virtual box. search virtual box in google and download the debian / ubuntu package. Install and BINGO. it's faster too and network connections inside the virtual box works great. It has guest additions too!

oh? hmm i'll have to check it

---

### Post by silentjudas on 2007-05-20
ok v-box is pretty nice, except this always comes up no matter what i try

---

### Post by silentjudas on 2007-05-20
things i am using
windows xp student edition cd
the same, but as an iso (i tried both)

neither will make it boot...and whenever i press f12 like it tells me to on the loading thing, a search thingy pops up, which makes no sense cause i took that shortcut off in ubuntu....this computer just loves to tick me off

---

### Post by hanzomon4 on 2007-05-21
```
sudo rm -r /etc/{the offending vmware file spawn of satan}
```

---

### Post by silentjudas on 2007-05-21
thank you. that;'s gone. now anyone know how to fix vbox??

---

### Post by veloce on 2007-05-21
> **silentjudas said:**
> found the folder buuuuuuuuuuuuuuuuuut

"Cannot move "/etc/vmware" to the trash because you do not have permissions to change it or its parent folder."

Of course you need root permissions to do this.  Use the command:

sudo rm -r /etc/vmware

Were you not using sudo for the other commands?

---

### Post by hanzomon4 on 2007-05-22
> **silentjudas said:**
> thank you. that;'s gone. now anyone know how to fix vbox??

```
sudo usermod -aG vboxusers "your user name"
``` Then ```
VirtualBox shutdow
```

---

### Post by silentjudas on 2007-05-23
nope. i did that, still a boot device w/e error. wont recognize the windows cd in the cd drive, or the image i copied of the cd to test it. nope.

---

### Post by burt_57 on 2007-05-23
> **hanzomon4 said:**
> You need to uninstall a previous vmware install. Try ```
sudo vmware-uninstall.pl
``` If you previously installed vmware from the repos try ```
sudo apt-get remove --purge vmware-server vmware-player
```
Hey thank I had that program...and tried to unistall but did not know how .
But what you daid just work fine.

---

### Post by silentjudas on 2007-05-24
does anyone know how to fix this....?

---

### Post by joselin on 2007-05-24
Try [this]("http://ubuntuforums.org/showpost.php?p=2255029&postcount=42"), at least in my case works.

Regards,
Jose

---

### Post by veloce on 2007-05-24
> **silentjudas said:**
> does anyone know how to fix this....?

It's actually becoming unclear what problem you are still trying to fix.  The last thing I saw was something about vbox.  If so, it's no wonder you're not getting help posting in a vmware thread.

---

