---
title: "gparted problem"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-06-06
When I reboot the PC with the gparted live cd it loads all the info and when it gets to the part where [I think] the interface is supposed to open, it doesn't. It tells me that it can't automatically open the proper video drivers and suggests that I use the "Forcevideo script" and enter VESA at 1024x763.

Could someone clue me in to the Forcevideo script please. I need to increase the partition size as I keep getting a popup saying that I've used 95% of the disc space allocated. It suggests that I delete unused programs or increase the partition size.

Many thanks.

Jon

PS: When I use the Add/Delete prog does that remove the prog and free up space or just hide it from view?

---

### Post by FleetAdmiral74 on 2007-06-06
That will add free space, but it techically is just hiding it from veiw  :)

As far as you are concerned, it is free space though, so if you see stuff you do not need removing it will free up space. Cant help you with the driver thing atm though, maybe try using gparted from a live cd, which might better detect drivers?

edit: 
[http://www.linuxquestions.org/questions/showthread.php?t=556879](http://www.linuxquestions.org/questions/showthread.php?t=556879) 
might help, seems to be same forcevideo problem, and he seems to have solved it, so check it out.

---

### Post by Romin-1 on 2007-06-06
Thanks for the reply, FleetAdmiral74;

I am trying to use the gparted Live CD but don't know the proper syntax for the Forcevideo it's asking for.

Ain't one thing, 'tis another,,,

Jon

---

### Post by zvacet on 2007-06-07
When Gparted boot up you will see option **force vesa driver**.Choose that option with down arrow key and hit enter.

---

### Post by Romin-1 on 2007-06-07
I tried your suggetion zvacet and still got this:

> X,ORG: You need graphical environment to start gparted. The graphical environment configuration should have been done automatically. Unfortunately it did not, since you are back to bash!

So please run **Forcevideo** script and you will be asked for **Video Driver** and resolution.

**VESA** driver should always work, and 1024x768 resolution too. If needed, you can kill X by using ctrl+alt+backspace combination.

Then it just sits there, with cursor blinking, waiting for a command.

I have tried the first 4 or 5 choices on boot with the same results.

Aside from disc space running out everything is working fine.

Thanks again fellas,

Jon

---

### Post by notquitemichael on 2007-06-07
if you get the option to change the boot perameters you may be able to add vesa768 or forcevesa or something to the line.

also, why not try a ubuntu live cd (as presumably it's worked before.) from there you can install gparted using synaptic and then do whatever you must.

---

### Post by Seisen on 2007-06-07
You can also do what I had to do. Let it go to command line and type this

```
vim /etc/X11/xorg.conf
``` You can use nano or vim

Go to this line 

```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "via"
        BusID           "PCI:1:0:0"
EndSection

```

change the driver to vesa by pressing CTRL+I and it should say insert. Then Shift+**:** and then type **wq** which will write the file and save it. Then try reloading X.

---

