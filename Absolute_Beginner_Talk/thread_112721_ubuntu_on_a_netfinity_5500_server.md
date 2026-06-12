---
title: "ubuntu on a netfinity 5500 server"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by 010010110101 on 2006-01-04
Hi guys,
I finally got ubuntu installed and working ok on a decent little machine (to see if I like it). I LOVE IT..Now the fun begins, I recently acquired a well maintained IBM netfinity 5500 server configed to raid 5. Is there anything new I need to know to convert my old database to be linux friendly? I could access my windows based server with the linux machine perfectly,,all files with the exception of my media files opened excellent. And I took care of those with a few downloads..Any help or input would be appreciated, This server is for my sons use while he is in college at RIT so he can upload his projects and see how they look in a real server enviroment. I plan on using apache as well. ,,

Thank you now for your help
Ft

---

### Post by 010010110101 on 2006-01-04
More info,,
OK I got it loaded,,it restarted quite a few times and got to the screen where it has ubuntu and loads modules and sets up various things,,like time and networking,,,all are ok,,,unlike my small machine I tried it out on,,here it dies and the screen just goes blank  with the hdds just blinking a little every now and then,,,any tips?

Thanks
Ft    :confused:

---

### Post by benplaut on 2006-01-04
Somebody's going to kick me for this 

*looks around*

Ubuntu isn't really the best choice for servers. If you want lots of excellent graphical tools, try SuSE, Redhat, or Fedora - they are better suited to a server environment.

What type of database is it?

**edit**

just saw your new post... try pressing ctrl-alt-f1: does it do anything?

---

### Post by ed_d on 2006-01-05
I am running 5.10 on a 5600 (x240) right now, dual 1ghz and 2gb ram, runs like a champ. I also have it running ot hom on a x220, single 1ghz, 3gb ram, again runs like a champ. So, I dont know what to tell you, loaded both machines with no issues and have set up samba to share 5 36gb disks. Not running raid, just jbod. No complaints other than wish had better graphics cards (both sustems are pci only and the 240 is 4mb mem and the x220 is 8mb)

---

### Post by Mikey976 on 2008-06-25
> **ed_d said:**
> I am running 5.10 on a 5600 (x240) right now, dual 1ghz and 2gb ram, runs like a champ. I also have it running ot hom on a x220, single 1ghz, 3gb ram, again runs like a champ. So, I dont know what to tell you, loaded both machines with no issues and have set up samba to share 5 36gb disks. Not running raid, just jbod. No complaints other than wish had better graphics cards (both sustems are pci only and the 240 is 4mb mem and the x220 is 8mb)

this is an old thread revival but i need help, 
ive got a netfinity 5600 x240 at work i want to use as a samba server . im trying to install ubuntu server 8.04 but i cant get it to install. i keep getting an error after i check the cd-rom pools it loads software up to 7% then give me an error cant read from the cdrom. mind you the disc is in perfect shape and i just installed 8.04 server on another machine with no issues

anyhelp would be greatly appreciated

---

