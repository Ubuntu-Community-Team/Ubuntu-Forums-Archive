---
title: "Turning the Computer Off"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by drndrw on 2007-09-09
Hey guys. Whenever I go to shut down my computer, it shows the Xubuntu screen and does nothing.  I'm pretty sure this is not supposed to happen, so could someone tell me how to fix it? Thanks.

---

### Post by parvinder on 2007-09-09
try Reboot by pressing CTRL+ALT+BACKSPACE or push the power button, sometime even I found that when you press the restart/turn off button nothing happens... but then I press the power button on my notebook. It shuts down normally by pushing the power button once.

---

### Post by n3tfury on 2007-09-09
> **parvinder said:**
> try Reboot by pressing CTRL+ALT+BACKSPACE or push the power button, sometime even I found that when you press the restart/turn off button nothing happens... but then I press the power button on my notebook. It shuts down normally by pushing the power button once.

ctrl+alt+delete is reboot.  ctrl+alt+backspace kills x.

---

### Post by drndrw on 2007-09-09
Ah, okay. But the problem I'm having is is that the Xubuntu thing still shows up. But then I can go CLI with ctrl alt backspace?

---

### Post by SOULRiDER on 2007-09-09
When you boot edit the kernel line and remove "splash" and "silent", see if it spits any errors. To edit the kernel line, when selecting the kernel to boot press e to edit. When youre done press b to boot.

---

### Post by dondad on 2007-09-09
> **SOULRiDER said:**
> When you boot edit the kernel line and remove "splash" and "silent", see if it spits any errors. To edit the kernel line, when selecting the kernel to boot press e to edit. When you're done press b to boot.

What kind of a system are you running on? I had the same problem with mine (Dell xps410n), did a lot of playing and searching. The thing that I found that finally fixed it was to edit the grub menu and at the end of the line on the kernel that says quiet, add reboot=b. This forces the reboot to the bios and in my case, it fixed it. I am pretty sure this is the fix, because when I did a recent kernel upgrade, the problem came back because that command was not there. I added it back on the new kernel and everything was OK again.

---

### Post by drndrw on 2007-09-10
Ah, well I'm running a ten year old EMonster. Where do I go for that again?

---

### Post by dondad on 2007-09-10
> **drndrw said:**
> Ah, well I'm running a ten year old EMonster. Where do I go for that again?

Don't know if it will help yours, but here is one section of my Grub menu. The menu is located at /boot/grub/menu.lst. If you play with it, be sure to back it up first. ;-)

```

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b55f1958-1f0f-41b5-b097-aa9c0904a1db ro quiet splash [COLOR="Red"]reboot=b[/COLOR]
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```

---

### Post by jimrz on 2007-09-10
when you boot up do you get a message that your BIOS do not meet the cutoff date of 2000? If so, firtst back up you menu.lst
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-bak
```
then try adding 
```
acpi=force
```
as a kernel parameter in /boot/grub/menu.lst

I have an older ThinkPad 600x for which this solved the problem of it not shutting fully down via the regular gui process.

---

### Post by drndrw on 2007-09-10
Oh, okay. I'll have to give this a try. And I also think that there is some ACPI RSDP problem going on, so this might kill two birds with one stone. Thanks!

---

### Post by drndrw on 2007-09-13
Sorry for the double post, but I did try this and it did not work. I tried editing the menu.lst file, but nothing happened. I think I need to edit the kernel, but every time I try pressing "e" at the grub menu, nothing happens. Oh, and I also tried pressing escape. What can I do?

---

### Post by dondad on 2007-09-13
I did my edits using the text editor and doing it direct. It is in /boot/grub/menu.lst. If you do it this way, remember to back it up first (a typo will kill it ;-)) and to use gksudo for a graphical app.

---

### Post by drndrw on 2007-09-13
I did back it up, and I did do this, but it still didn't work. Does anyone know why? I did everything I was supposed to...

---

