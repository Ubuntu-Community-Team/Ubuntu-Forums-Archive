---
title: "XDM config with fluxbox"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by mdecler2 on 2006-12-15
I want to configure xdm to boot in fluxbox, not in gnome. I am also interested in running startup scripts, particularly to start numlockx and configure wireless on boot up. Can anyone give me any tips on how to go about configuring XDM?

---

### Post by kerry_s on 2006-12-15
Why didn't you just use gdm, it's way better? I suppose for XDM you have to modify it manually. Check in synaptic and see where xdm installed everything & look for a xdm.conf file or something similar.

-> [http://en.wikipedia.org/wiki/XDM](http://en.wikipedia.org/wiki/XDM)
-> [http://www.xfree86.org/current/xdm.1.html](http://www.xfree86.org/current/xdm.1.html)
-> [http://linuxgazette.net/issue43/nielsen.xdm.html](http://linuxgazette.net/issue43/nielsen.xdm.html)

---

### Post by mdecler2 on 2006-12-15
The reason why I dont want to use GDM is because it is running about 100 more processes then I need. I don't need an automounting tool for instance, I can do that myself.

The concept of "better" is relative to what I am doing, so in my case GDM and GNOME are very bloated and hanous in my case. I want to get rid of GNOME and GDM forever.

Does anyone have any tips on how to configure XDM and fluxbox? I really have no idea how. The xdm.conf file is not easy to read, and it looks like it has multiple conf files "included" in it.

---

### Post by mdecler2 on 2006-12-16
Can anyone tell me where .xinitrc, .xsession files are? It seems like the problem is that xdm is defaulting to Gnome on start-up, but I don't think XDM is at fault.

---

### Post by kerry_s on 2006-12-16
> **mdecler2 said:**
> Can anyone tell me where .xinitrc, .xsession files are? It seems like the problem is that xdm is defaulting to Gnome on start-up, but I don't think XDM is at fault.

Those 2 are files you create yourself.

> The reason why I dont want to use GDM is because it is running about 100 more processes then I need. I don't need an automounting tool for instance, I can do that myself.

The concept of "better" is relative to what I am doing, so in my case GDM and GNOME are very bloated and hanous in my case. I want to get rid of GNOME and GDM forever.

Your kidding right, GDM is a little bloated but worth it. You''ll be installing that stuff that comes with gdm anyways if you use synaptic. You wouldn't have to do all that crap your doing now. With out a proper login manager you'll always have some problem with default settings that requires 3 times as much tweaking to get it to work right. I use GDM & fluxbox on a server install with a nothing fancy no background, stock theme. I only use server installs and i've tried just about everything including what your doing now.

Which by the way before i forget->

you only need one of those either .xsession or .xinitrc and just put this inside

exec /usr/bin/startfluxbox

---

### Post by K.Mandla on 2006-12-16
If you wanted, you could go desktopmanagerless altogether and log in at the command prompt. I have two Openbox systems and on both of those I use an [autologin executable]("http://www.ubuntuforums.org/showthread.php?t=152274") to log me in and start X without a desktop manager. 

Much, much lighter than GDM, or for that matter, XDM. 

@kerry_s: I forgot I wanted to ask you ... is that a dual monitor setup, or a very wide widescreen?

---

### Post by kerry_s on 2006-12-16
> **K.Mandla said:**
> If you wanted, you could go desktopmanagerless altogether and log in at the command prompt. I have two Openbox systems and on both of those I use an [autologin executable]("http://www.ubuntuforums.org/showthread.php?t=152274") to log me in and start X without a desktop manager. 

Much, much lighter than GDM, or for that matter, XDM. 

@kerry_s: I forgot I wanted to ask you ... is that a dual monitor setup, or a very wide widescreen?

It's dual monitor. You should try my auto login how to, it's easier, no building the auto login script no extra apps needed, it uses a simple text script.-> [http://www.ubuntuforums.org/showthread.php?t=303319](http://www.ubuntuforums.org/showthread.php?t=303319)

I used that with a older machine that only had a 1 gig HD so i really had to cut back on apps to get space, the finished system came in at around 400mb. :) This one i'm on now is a feisty test build that's around 500mb(depends on how much i got cached) and thats with all the apps i use everyday. that screen shot was with iceape i was trying.Here's a pic of my normal with firefox->

---

### Post by K.Mandla on 2006-12-16
Hey, that's much better than the old howto. I'm going to give it a whirl this weekend. Thanks!

---

### Post by kerry_s on 2006-12-16
> **K.Mandla said:**
> Hey, that's much better than the old howto. I'm going to give it a whirl this weekend. Thanks!

Let me know if you have problems, i've only used it a total of 10 times, but it's always worked. Plus you don't need Internet to do it. I only found that one bug with startx and i haven't tried with other wm/de much i only tested quickly just to confirm it would work. That's why i included the option to select your enviroment in .xinitrc. Have fun.

---

### Post by mdecler2 on 2006-12-23
Hey all,
The way I did this (for those that are interested), first I changed the file /etc/X11/default-display-manager to have a single line, ```
 /usr/bin/X11/xdm 
```
exactly. This file used to have "/usr/sbin/gdm" for the record.
This assumes that you have xdm downloaded and installed in the directory /usr/bin/X11/ . You should be safe however if you installed it using "apt-get install" because that is exactly what I did. If you install xdm from the repositories using apt, it may prompt you if you would like this changed immediately...I think I remember seeing that...in any case, the file I have specified should be changed to xdm.

Then, in order to get X11 to load Fluxbox instead of Gnome, I had to create a .xsession file in my home directory. This however was easy. This is actually quoted from an email from my friend James: 
> As far as XDM...  If you create a .xsession in your home directory, it will override the "system defaults" as to what starts when X is started.  .xsession is a bash script of sorts, as it is called upon by startx, a bash script.  In the .xsession you type commands that you want to run when X is started.  Here is an example:

xterm &
fspanel &
exec fluxbox

The last command always begins with "exec" so "Bash goes away when the script is done," as my brother says.  The others have & at the end so they start in quick succession, without waiting for each other.  If things get funny, experiment taking &'s away.  It seems like you just want fluxbox, so

exec fluxbox


Hope that helps anyone!

---

