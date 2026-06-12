---
title: "Should Shut Down power down my computer?"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Relztrah on 2007-09-19
I successfully installed 7.04 on an old machine and played with it a while. Shut Down leaves the Ubuntu logo on the screen with power running. The on/off button doesn't power down the machine. I have to turn off power at the power strip. Is this normal?

---

### Post by ruibernardo on 2007-09-19
Depending on your motherboard, it might be. Try pressing the "power down" button for 8 seconds without releasing it.

---

### Post by sumguy231 on 2007-09-19
If it is an older computer (prior to or around 2000) then you can try the acpi=force boot option. Also check your BIOS settings - I had a computer which had a "Choose your OS" option and if it was set to "Windows" ACPI wouldn't work with Linux.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by dresman on 2007-09-19
whoa.wierd.a bit strange

---

### Post by harty83 on 2007-09-19
I just bought a brand new pc from HP and have the same problem.  Nothing I've tired works.

---

### Post by voided3 on 2007-09-19
I've had experience w/ something like this on two occasions. One was an HP that wouldn't shut down and it only ran XP. After I reformatted it, it shuts down normally.... Another was an Athlon comp on an IWILL ATX mobo and I could not get it to shut down normally with any OS or live CD and I never figured it out; it might have been a crappy power switch or something.

---

### Post by alienexplorers on 2007-09-19
My computer a 10year old work horse will not shut down if ACPI is turned off in BIOS.  Had to update BIOS to get this function, but it was worth it.

---

### Post by harty83 on 2007-09-19
MIne shuts down fine under winblows, but not linux.  I hear there is a bug somewhere out there in acpi that causes this issue but haven't found any specific documentation on it.  My BIOS sucks cause it doesn't give very many options at all.  I'm finding this with many new pcs...

---

### Post by jerrylamos on 2007-09-19
As of Feisty, Ubuntu 7.04 one of my computers no longer powers off as installed with Ubuntu, Kubuntu, Xubuntu.  Poking around looks like they picked up some Debian power off code which is not as good as Edgy 6.10 or Dapper 6.06.  Doesn't look to me like they have any intentions of fixing it.

In my post 
[http://ubuntuforums.org/showthread.php?t=424225&highlight=workarounds](http://ubuntuforums.org/showthread.php?t=424225&highlight=workarounds)
there's a patch:

"Shutdown" doesn't
This system powers off with Edgy, Dapper, Knoppix, ... but not Feisty 7.04 or Gutsy 7.10. If I select Shutdown after a while nothing's happening, there's no message on the screen, and the keyboard and mouse are dead. Someone on some forum (where?) suggested:
Do: 
sudo gedit /etc/modules
Add the following line, then save:
apm power_off=1
Do: 
sudo gedit /boot/grub/menu.lst (where the l is a lower case L)
Find the line that start with "kernel" and add this onto the end, no carriage return, all on the same line which probably wraps over:
acpi=off apm=power_off
then save. Restart and on "Shutdown" it should. Mine did on Feisty and Gutsy.
Usual cautions apply when changing system files.....
Jerry

---

### Post by harty83 on 2007-09-19
Well I be, the "apm power_off=1" in /etc/modules and "apm=power_off" in menu.lst did the trick for me.  I have read multiple threads that did similar things and none worked.  But this did it!  Thanks!  My computer now powers off.

---

### Post by Relztrah on 2007-09-20
> **harty83 said:**
> Well I be, the "apm power_off=1" in /etc/modules and "apm=power_off" in menu.lst did the trick for me.  

Sorry, but this means nothing to me.

---

### Post by Sayers on 2007-09-20
Yeah that happened on my older computer.

---

### Post by harty83 on 2007-09-20
> **Relztrah said:**
> Sorry, but this means nothing to me.

refer to post # 9

---

### Post by Relztrah on 2007-09-20
How do I open the Sudo file?

---

### Post by quirks on 2007-09-26
OMG! I love you!!! I've got a really old machine and I have been looking for this for ages (and had already got used to unplugging my PC after shutting it down). The trick with apm power_off=1 in /etc/modules and apm=power_off in /boot/grub/menu.lst did it for me. (However I didn't need acpi=off.)

quirks

---

