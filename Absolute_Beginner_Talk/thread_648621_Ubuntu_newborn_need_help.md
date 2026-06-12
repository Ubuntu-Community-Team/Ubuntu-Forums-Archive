---
title: "Ubuntu newborn need help"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by Joseph5000 on 2007-12-23
Now I have it, no more MS. But have no idea how it works. The Lingo and all that. 
$ things already I need help with.
a. I accidentally deleted my top-panel and could re assemble it, except I can't find the Wireless connection bars. The ones that show how strong my connection is.
b. I can't install Google Earth, It's on my desktop. When I open it it tells me: 
Could not open the file /home/joseph/Desktop/GoogleEarthLinux.bin.
I don't even know what a .bin file is.
c. Skype was easy to install, but I have to get every time a new password, only then can I open it. Aaaaaah.
d. How do I uninstall in General and where are my program files.

MS was easier, but getting the error messages all the time they wanted me to report. Not good with hacked versions. Too much stress.
Please help me and I am sure Santa will love you even more.
Cheers Joseph

---

### Post by Sordelka on 2007-12-23
You should maybe start with a clean install. Reinstall Ubuntu. Then, carefully read the ubuntu documentation, which is readily available at [www.ubuntu.com](www.ubuntu.com)

Always read the manual, if not, you will have to reinstall many times. Believe me. Speaking by personal experience.

---

### Post by Rocket2DMn on 2007-12-23
Whoa, whoa, a reinstall is totally not necessary.
To install/uninstall in Ubuntu we usually use the Synaptic Package Manager which is available under System->Administration.
A .bin file is similar to a .exe file - it is an executable.  You may need to reinstall Google Earth, I'm not sure what you did there.  It might be availble in the repositories - open Synaptic and Search for Google Earth (you may need to enable the Universe and Multiverse repositories by going to Settings->Repositories)
The program with the wireless bars is called nm-applet, right click the panel and click Add to Panel and ensure that Notification Area is added.
I don't have answers to your other questions at the moment, but I'll look into them - hopefully others have input, if not start new threads for each problem.

---

### Post by Rocket2DMn on 2007-12-23
Update: I just tried out Google Earth, didn't realize it wasn't quickly available.  To install it, here's what you do:
Open a Terminal (Applications->Accessories->Terminal)
1) change directory to your desktop
2) set executable permissions on the install (.bin) file.
3) run the install
```
cd Desktop
chmod +x GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```
You will then get the install screen.

---

### Post by Presto123 on 2007-12-23
I'm not trying to mess you up on this, but, really, you don't HAVE to do it from the terminal. It's useful to know how to navigate it, though. 

All you really need to do is as you said there is to right click it, select properties and navigate to the permissions section. At the bottom you see "Allow to Be Executable" something like that. Double click the .bin file and when it pops up asking what you want to do with it, you can simply hit "Run". 

That's if you want to do it a bit easier, but, I would certainly get to know Terminal. Very useful for getting programs and customizing stuff. :)

---

### Post by Rocket2DMn on 2007-12-23
> **Presto123 said:**
> I'm not trying to mess you up on this, but, really, you don't HAVE to do it from the terminal. It's useful to know how to navigate it, though. 

All you really need to do is as you said there is to right click it, select properties and navigate to the permissions section. At the bottom you see "Allow to Be Executable" something like that. Double click the .bin file and when it pops up asking what you want to do with it, you can simply hit "Run". 

That's if you want to do it a bit easier, but, I would certainly get to know Terminal. Very useful for getting programs and customizing stuff. :)

Good call, I never even think to do it graphically... been stuck at unix ssh terminals for too long...

Do whichever works best for you!

---

