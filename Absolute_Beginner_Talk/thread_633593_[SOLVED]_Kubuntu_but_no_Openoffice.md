---
title: "[SOLVED] Kubuntu but no Openoffice"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by kle on 2007-12-06
Running Kubuntu 7.10 on an HP Pavillion dv6000. I installed it from the alternate CD in order to configure dual boot and partitions. 

I have enabled a few extra languages in the system set-up. 
I have installed Nvidia restricted drivers. 

I use my laptop for work. And openOffice is absolutely essential.

On these pages, I see that some people seem to be able to use openOffice with Kubuntu, maybe even Kubuntu 7.10. But on my system OO seems to be utterly inert. I have installed what must be the gnome version (the splash screen is not blue). When I call the program, the splash screen appears, a window appears - but the splash scrren does not go away - and then the window freezes, but the mouse and keyboard still respond outside the window. I can "kill" soffice. 

If I tell the system to open a file (f. inst. and RTF file) with office, it will do so: No splash screen and the OO window appears, exhibiting the file, but there is no reaction to input from mouse or keyboard. I have to "kill" soffice. 

Is this a bug somewhere? Or have I configured something erroneously? 

Grateful for any help.

---

### Post by viking777 on 2007-12-07
I can confirm that Open Office works fine on kubuntu gutsy. 

I would suggest you go into Synaptic or whichever package manager you use and completely remove ooo reboot then reinstall it again.

---

### Post by hyper_ch on 2007-12-07
That should be the essential stuff:

```

sudo aptitude install openoffice.org openoffice.org-gtk

```

---

### Post by kle on 2007-12-07
Thank you both. I removed once again all OO applications with the Adept package manager and ran sudo aptitude install openoffice.org openoffice.org-gtk
But what I got was exactly what I had before: A window that was empty in all but that it had the non-blue splash screen. 

I am beginning to believe that this might be related to the Nvidia driver as I also get system freezes with Firefox. I think I shall have to read up on how to install a driver update without the help of the restricted drivers manager. It seems a slightly frightening task (me being a grandmother and all...)

---

### Post by kle on 2007-12-07
To close the issue: I reinstalled Kubuntu 7.10. 
Open Office (gnome version) was OK from the box. 

Then I started by 
1) disabling CD from sources list.
2) running sudo dpkg --configure -a
3) cancelling OpenOffice update in Adept manager
4) disabling restricted drivers
before I accepted the other updates.

I am going to see how far I get without the nVidia driver and see if I get any cold freezes.
So I consider the matter resolved, for the time being "isolating" nVidia driver.

---

