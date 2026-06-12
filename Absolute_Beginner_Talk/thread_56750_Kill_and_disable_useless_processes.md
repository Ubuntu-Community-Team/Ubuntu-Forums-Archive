---
title: "Kill and disable useless processes?"
date: 2005-08-13
forum: Absolute Beginner Talk
---

### Post by subc on 2005-08-13
...
new to Ubuntu.

I was wondering how can I kill and disable processes that are running on the background so they won't load next time I restart.

Coming from winXP, I used to have a really 'boring' desktop, because I rather use my resources when I play a game or use a video/graphics/3d application than just waste em on eyecandy.

In XP I used to have some 16-20 processes running on the background, and the CPU load was something like 2% when idling (1.4Ghz processor).

Now that I have installed ubuntu, I noticed that **My processes** (for my username) are 30, and when I select **show all processes** the number jumps to 86!!!  ](*,)  what's up with that!?

I realize that most of them are 'sleeping' (whatever that is), but they still take some megs of memory, and adds to the overall count of memory usage in the system (much higher than winXP btw).

this reminds me the reason I stoppe testing/using linux some months ago (mepis, suse, mandrake).

---

### Post by aysiu on 2005-08-13
The only thing I can think of is uninstalling those programs. If you need those programs in order for your computer to function, then what's the harm of having them run in the background? If you don't need them, *sudo apt-get remove* them.

---

### Post by nad on 2005-08-13
I don't know if there is a gui startup script editor, however, as your default runlevel is 2 all the scripts in /etc/rc2.d and rcS.d are run at startup.

The convention is to stop the services that you do not wish to run ( /etc/init.d/service_name stop ) and then rename the runlevel script to K(100 -  start_number)script_name. For example: S14ppp becomes K86ppp.

---

### Post by subc on 2005-08-13
[QUOTE=nad]I don't know if there is a gui startup script editor, however, as your default runlevel is 2 all the scripts in /etc/rc2.d and rcS.d are run at startup.

The convention is to stop the services that you do not wish to run ( /etc/init.d/service_name stop ) and then rename the runlevel script to K(100 -  start_number)script_name. For example: S14ppp becomes K86ppp.[/QUOTE]
 :D sooo simple! ( ya right)

linux is not ready for my notebook (not even for my desktop).
considering that my notebook doesn't have a 'real' video card with opengl support, then linux (any flavor) is pretty much useless (no proper video, graphics, 3d... GAMES!!!)

damn it, this is like the 8th time I try linux and realize that is almost there, but not quite.

---

### Post by aysiu on 2005-08-13
[QUOTE=subc]:D sooo simple! ( ya right)

linux is not ready for my notebook (not even for my desktop).
considering that my notebook doesn't have a 'real' video card with opengl support, then linux (any flavor) is pretty much useless (no proper video, graphics, 3d... GAMES!!!)

damn it, this is like the 8th time I try linux and realize that is almost there, but not quite.[/QUOTE] Huh? Where did this come from?

---

### Post by subc on 2005-08-13
means that everytime I try to use linux in a permanent way, there's always something that holds it back.
i remember when I had to deal with re-installing nvidia drivers at every reboot lol
then I realized how crappy it was the linux experience without opengl support after installing it on 2 old notebooks with generic vid cards (trident?),
then the unending line of commands whenever the user needs to perform simple tasks (killing processes, updating software, etc).

there's always a small but.

but back to the main message: 86 processes with default installation? lol
not even crappy winxp has that many after a fresh install (and can be quickly subdue to 16 background processes for comfort).

---

### Post by aysiu on 2005-08-14
There is a graphical way to kill processes in Ubuntu/Gnome. What you're asking to do is kill processes and have them never start up again--how do you do this "simple" task in Windows? I would guess you would edit the registry. A little regedit isn't so simple now, is it? And who cares how many processes are running? Are you running out of RAM? Are most of these processes active, or are they sleeping?

There is also a graphical way to update software--it's called Synaptic Package Manager.

By the way, there are many Linux distributions out there. When you want to tinker with settings and configurations, Ubuntu isn't going to be point-and-click. If point-and-click is your cup of tea, Mepis may be a better fit.

Or, if what you consider "simple" tasks are not so simple... then maybe Linux isn't for you. Best of luck with whatever OS you settle on.

---

### Post by subc on 2005-08-14
[QUOTE=aysiu]There is a graphical way to kill processes in Ubuntu/Gnome. What you're asking to do is kill processes and have them never start up again--how do you do this "simple" task in Windows? I would guess you would edit the registry. A little regedit isn't so simple now, is it? And who cares how many processes are running? Are you running out of RAM? Are most of these processes active, or are they sleeping?

There is also a graphical way to update software--it's called Synaptic Package Manager.

By the way, there are many Linux distributions out there. When you want to tinker with settings and configurations, Ubuntu isn't going to be point-and-click. If point-and-click is your cup of tea, Mepis may be a better fit.

Or, if what you consider "simple" tasks are not so simple... then maybe Linux isn't for you. Best of luck with whatever OS you settle on.[/QUOTE]
 you are right. linux is probably not for me then.
i need an OS i don't have to worry about. after all, im not into computing to take care of the computer itself, but to 'do actual things' with it (other than configuring stuff, patching here and there, and solving OS problems).

i'll go back to distrowatch after 6 or 7 months then.

---

### Post by aysiu on 2005-08-14
[QUOTE=subc]you are right. linux is probably not for me then.
i need an OS i don't have to worry about. after all, im not into computing to take care of the computer itself, but to 'do actual things' with it (other than configuring stuff, patching here and there, and solving OS problems).

i'll go back to distrowatch after 6 or 7 months then.[/QUOTE] Have you thought about buying a Mac?

---

### Post by subc on 2005-08-14
[QUOTE=aysiu]Have you thought about buying a Mac?[/QUOTE]
 haha! nice joke btw ;)

---

### Post by aysiu on 2005-08-14
[QUOTE=subc]haha! nice joke btw ;)[/QUOTE] It wasn't really a joke, but I guess I'll take that as a "no." Seriously, though, have you tried Mepis or Blag? those are great free "out-of-the-box" working distributions.

---

### Post by Sam on 2005-08-14
[QUOTE=subc]In XP I used to have some 16-20 processes running on the background, and the CPU load was something like 2% when idling (1.4Ghz processor).

Now that I have installed ubuntu, I noticed that **My processes** (for my username) are 30, and when I select **show all processes** the number jumps to 86!!!  ](*,)  what's up with that!?[/QUOTE]
Right, but in linux every single process is displayed. But notice that in Windows, there are less processes because a lot of them (especially the system ones) are hidden from the user...

---

### Post by pmj on 2005-08-14
So many answers without any useful information.

*Is* there a way to manage your processes? In Windows there's the services manager (no, there's no registry editing needed), in Ubuntu there's what?

Since I don't have a printer I don't need the cups thingy, so seeing cupsd having a VM size of 7.7MB and gnome-cups-icon having a VM size of 33MB bugs the hell out of me. Getting rid of them forever would be nice.

---

### Post by GreyFox503 on 2005-08-14
A cool program called Boot-up Manager sounds like it might be what you want.

```
sudo apt-get install bum
```

You might have to add the extra repositories at ubuntuguide.org first, I'm not sure.

Then go to System > Administration > Boot-Up Manager

---

### Post by heimo on 2005-08-14
There's [rcconf]("http://packages.ubuntu.com/hoary/admin/rcconf") in [universe]("https://wiki.ubuntu.com/UniversePackages"). Enable universe and install using sypaptic or apt-get.

Run it on terminal (Applications->System Tools->Terminal), by entering: ```
sudo rcconf
```

It's possible to install BUM in Hoary too (but not from Ubuntu repositories, I think), it'll be available in Breezy universe.

---

### Post by pmj on 2005-08-14
[QUOTE=GreyFox503]A cool program called Boot-up Manager sounds like it might be what you want.[/QUOTE]
Yes, it was. I hope it helps the starter of the thread as well, if he didn't give up already that is. :)

BUM couldn't help me remove gnome-cups-icon though so I guess I'll try rcconf next.

---

### Post by heimo on 2005-08-14
[QUOTE=pmj]Yes, it was. I hope it helps the starter of the thread as well, if he didn't give up already that is. :)

BUM couldn't help me remove gnome-cups-icon though so I guess I'll try rcconf next.[/QUOTE]

Won't help you on that. It's not part of services started during boot, but when you login to Gnome. You need to edit default session or save your Gnome session and remove gnome-cups-manager or gnome-cups-icon from it, I guess. Pointers: System->Preferences->Sessions, /usr/share/gnome/default.session or ~/.gnome/session (or something like that). If you can't solve it, let me know and I'll give more details when I can (right now I can't logout for testing).

---

### Post by jeremy on 2005-08-14
[QUOTE=subc]you are right. linux is probably not for me then.
i need an OS i don't have to worry about. after all, im not into computing to take care of the computer itself, but to 'do actual things' with it (other than configuring stuff, patching here and there, and solving OS problems).

i'll go back to distrowatch after 6 or 7 months then.[/QUOTE]
 Well, windows is certainly not for you then. You would have to worry about virii, updates, licensing, hijacking etc. etc.

---

