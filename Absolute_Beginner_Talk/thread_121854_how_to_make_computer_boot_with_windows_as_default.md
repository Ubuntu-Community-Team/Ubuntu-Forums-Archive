---
title: "how to make computer boot with windows as default?"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by sallam on 2006-01-26
From where can I change the default OS that the computer boots up with?

---

### Post by fcendejas on 2006-01-26
are you using grub as your boot loader?  if so, you can, as a superuser, get to the /boot/grub folder, and edit menu.lst.  

you can read the formatting directions, but you can actually copy and paste the new order you want.

---

### Post by sallam on 2006-01-26
no tool/interface to use for editing the boot loader?
when I try editing files, it usually refuse saying I'm not the owner (I guess because ubuntu makes no one the owner during its install)
can you give me the code to copy in terminal for this?

---

### Post by frodon on 2006-01-26
Open the file with the "sudo" command : ```
sudo gedit /boot/grub/menu.lst
```

---

### Post by MJN on 2006-01-26
...and the directive you want to change/add is **default <number>** where <number> is the menu entry that you want to boot starting at 0. For example, to boot the top menu item you'd use **default 0**, for the 3rd item down you'd use **default 2** etc. Note that a 'seperator' item is often included in the list and this counts as a valid place (thus include it when counting the items).
 
After you've changed the config reinstall grub with **sudo grub-install /dev/hda** (assuming your HDD is the first master drive on the primary channel) then reboot (**sudo shutdown -r now** if you're not familiar)!
 
Mathew
 
P.S. You'll soon know if you've used the wrong <number> as Grub, by default, won't boot the OS straight away but will highlight the intended menu item to be booted whilst waiting...

---

### Post by sallam on 2006-02-26
re-install grub? why? I only edited the the number next to 'default' in the menu.lst file, and it worked. My computer now, if un-attended, will boot in windows as default. is there a reason why I should have re-installed grub?

btw, instead of the usual 3 ubuntu boot options, I have 6, with 2 different dates. What did that? and is it ok if I delete the older 3 from the menu.lst?

---

### Post by aysiu on 2006-02-26
[http://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](http://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

---

### Post by MJN on 2006-02-26
[quote=sallam]re-install grub? why? I only edited the the number next to 'default' in the menu.lst file, and it worked. My computer now, if un-attended, will boot in windows as default. is there a reason why I should have re-installed grub?[/quote]

Sorry, probably nothing more than habit from my LILO days when any config changes had to be followed by a reinstall (not as drastic as it sounds).

Mathew

---

### Post by sallam on 2006-02-26
Oh, thats ok then :)

aysiu,
Thanks for the link. But I was asking about removing the extra 3 entries that was not there before. I guess I'll have to try and see, lol. If you didn't notice me here anymore, you'll know it failed :)

---

### Post by aysiu on 2006-02-26
Just remove them.
You can also use Synaptic to uninstall extra kernels. Do a name search for *linux-image*.

---

### Post by deemp on 2006-02-26
Guys, I know it's a bit off topic in this board, but how can I uninstall Ubuntu?  It doesn't meet my requirements for business use and now I can't find a way to uninstall it from my network!

---

