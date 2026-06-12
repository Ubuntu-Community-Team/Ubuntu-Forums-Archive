---
title: "How to boot into shell not gui"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by acolic on 2006-05-27
Hi,

I have installed ununtu and on boot up I go to a gui ubuntu screen where I can choose which windows manager I want to boot up into.

I'd like to boot straight into a shell where I supply a username/password. From there I'd like to run startx if I want to go to a gui log in screen.

I've changed my runlevel to 3 but I still go to the Gui log in screen.

Could someone tell me how to set up my boot process to boot to a shell login?

Thanks

Alex

---

### Post by barbarian on 2006-05-27
hi,

*ctrl-alt-f1*

---

### Post by acolic on 2006-05-27
Thanks Barbarian,

Is there a way to automatically boat to the same shell that I get to when I type ctrl-alt-f1?

That way I bypass all the gui loading that is slowing down my old laptop.

thanks,

Alex

---

### Post by ifokkema on 2006-05-27
[QUOTE=acolic]Is there a way to automatically boat to the same shell that I get to when I type ctrl-alt-f1?

That way I bypass all the gui loading that is slowing down my old laptop.[/QUOTE]

Hi,

I guess, if you really want to skip the gui, you could take a look at the rcconf package. That should allow you to pick which services start at what runlevel. Just make sure gdm doesn't start up. I guess that should help you out.

Ivo

---

### Post by S{yndrom}e on 2006-05-27
The only way i know of is to reinstall ubuntu. This time, when it asks you for installation type, instead of leaving the filed blank and installing defualt instilaation, enter "server" and then press enter. Next time when you boot in all it will have is a black screen with a prompt (command line whatever =P)

---

### Post by lordharsha on 2006-05-27
[QUOTE=barbarian]hi,

*ctrl-alt-f1*[/QUOTE]

i've tried doing this before, but nothing seems to happen...

---

### Post by barbarian on 2006-05-27
> I guess, if you really want to skip the gui, you could take a look at the rcconf package.

or *sudo sysv-rc-conf*

check out here:

[http://www.ubuntuforums.org/showthread.php?t=89491&highlight=howto+boot+feel](http://www.ubuntuforums.org/showthread.php?t=89491&highlight=howto+boot+feel)

---

### Post by James_PN on 2008-06-27
To boot directly into the shell, you need to stop the program that boots the GUI, (this is called GDM)
Type this command at the shell to remove it

sudo rm /etc/rc3.d/S13GDM

Now you need to tell ubuntu to boot to run level 3 (straight to shell), you do this by creating the /etc/inittab, Issue the following command:

gksu gedit /etc/inittab

Then add following line to top of file:

id:3:initdefault:

Now save the file

To restore things as they were, all you need to do is delete the inittab file by typing this into the shell:

sudo rm /etc/inittab

Hope This Helps!

---

