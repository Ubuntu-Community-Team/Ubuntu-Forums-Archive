---
title: "I changed the ubuntu screen resolution and now the screens showing up weird (pics)"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by gottabeandrew on 2008-03-07
I changed my screen resolution a few times and it was fine. Then i ticked the widescreen button and chose the option for my screen (it wasn't showing up before then). I closed ubuntu properly then started it up again and this is what it shows like:

[img]http://farm4.static.flickr.com/3113/2317105230_1ccaa23b13_o.jpg[/img]

How do i put it back to normal? I'm running it through VirtualBox (a virtual machine running program) on Vista. Is there something i could do through there to change it? I've just installed it so didnt' feel the need to take a snapshot.

---

### Post by gottabeandrew on 2008-03-07
This has got to the second page now and it is vital that i get a reply to this otherwise it won't work at all.

---

### Post by smurphy_it on 2008-03-07
Hit Ctrl-Alt-F1 and login with your credentials.  Then navigate to /etc/X11 and see what xorg.conf files you have.

Usually when changes have been made Ubuntu will make a backup copy.  If you have a backup copy (recent) you can rename your current xorg.conf to another name like sudo mv xorg.conf xorg.conf.bad

and then rename your backup copy to xorg.conf (example... sudo mv xorg.conf.backup xorg.conf).

Afterwards you will have to restart x-windows.  If ubuntu, you can try Ctrl-Alt-Backspace and try logging in or while in your current shell try sudo services gdm restart

Hopefully that will fix your problem.  If not, post the output of your xorg.conf file here so we can take a look at it and help you fix it.

I believe what alot of people have done in the past to fix some of these video issues are to enter rescue mode (hit esc on grub boot) and once in the terminal / shell type in [COLOR="Orange"]*sudo dpkg-reconfigure xserver-xorg*[/COLOR]

---

### Post by gottabeandrew on 2008-03-07
It didn't detect my settings so i had to enter them myself and i have no idea about them. I've tried looking in my system information but theres no info there neither.

And the top one just returns something telling me that the folder does exist but is telling me nothing else.

---

### Post by ifross on 2008-03-07
I think that this is due to the fact that you tried to change the resolution in Ubuntu. I remember changing the resolution through windows on my XP virtual machine and it did something similar. Turns out all you need to do is install guest additions and then resize the window the VM is running in. Not sure how to change it back, iirc, I just rebooted the VM and it returned to normal. 

Sorry I couldn't be of much help, but at least maybe this will stop it happening again.

---

### Post by gottabeandrew on 2008-03-07
But how can i install anything on it while it's like that? Although i installed it and somebody said about something in another thread that you have to have guest additions to do something and i wasn't sure whether i had it or not so i continued with the guide anyway and it worked so i assume i do have it.

---

### Post by gottabeandrew on 2008-03-07
Ok, be honest here. No rubbish. Should i delete Linux and start again?

---

