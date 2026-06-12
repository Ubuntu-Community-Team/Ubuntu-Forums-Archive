---
title: "Why must Ubuntu betray me so...?"
date: 2005-09-03
forum: Absolute Beginner Talk
---

### Post by Muhammad on 2005-09-03
I turned my PC on this morning, the usual, GRUB taking at least 3 mins to load, etc... etc... but it's worth it, Ubuntu is at least 10,000 times better then windows, etc... etc...

I recieved this messege after I loged in to GNOME:

[quote=Gnome Fucked up error]There was an error starting GNOME setting Daemon.

Some things such as themes, sounds, or background settings may not work correctly.

The setting Daemon restarted too many times.

GNOME will still try to restart this setting each time you log in.(my ass)[/quote]

Is there a possible solution for this problem? or should I reinstall everthing?

I used the search feature, and apperantly people never encountered this problem after Hoary was released. BTW, I'm using Ubuntu Hoary the Installation CD version.

Also I'm using Fluxbox in order to access Firefox and type this messege.

---

### Post by UbuWu on 2005-09-03
Well first I would try restarting your computer and see if it happens again.

---

### Post by Muhammad on 2005-09-03
I tried that several times in hope that GNOME would fix itself, but with no luck.

---

### Post by Wolki on 2005-09-03
Try backing up the .gnome* directories and delete the originals afterwards. Maybe the settings were corrupted.

You could also try starting the gnome-settings-daemon from a terminal to see if it gives you an error message.

---

### Post by Muhammad on 2005-09-03
I recieved this:

```
muhammad@ubuntu:~$ sudo gnome-settings-daemon
Password:
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xscreensaver: Can't open display: :0.0
xscreensaver: initial effective uid/gid was root/root (0/0)
xscreensaver: running as nobody/nogroup (65534/65534)

xscreensaver: This is probably because you're logging in as root.  You
              shouldn't log in as root: you should log in as a normal user,
              and then `su' as needed.  If you insist on logging in as
              root, you will have to turn off X's security features before
              xscreensaver will work.

              Please read the manual and FAQ for more information:

              http://www.jwz.org/xscreensaver/faq.html
              http://www.jwz.org/xscreensaver/man.html

KJ
** (gnome-settings-daemon:7993): WARNING **: Encountered problems registering the settings daemon with bonobo-activation. Clients may not detect that the settings daemon is already running.
```

Apperantly it's already running but there were problems... What?

Also how do I backup .gnome* dir and del the originals. I'm a Linux newb you see...

---

### Post by Muhammad on 2005-09-03
What's a Bonobo?

---

### Post by Knome_fan on 2005-09-03
[QUOTE=Muhammad]

Apperantly it's already running but there were problems... What?

Also how do I backup .gnome* dir and del the originals. I'm a Linux newb you see...[/QUOTE]
Don't start it as root, start it as a normal user (no sudo).

To move these directories out of the way, do the following:
mkdir gnome_bak
mv .gnome* gnome_bak

You might also want to do this with your .gconf directories.
Keep in mind that you will loose all your gnome settings after you moved these directories.

---

### Post by Wolki on 2005-09-03
[QUOTE=Muhammad]
Apperantly it's already running but there were problems... What?
[/quote]

you don't need sudo to run gnome-settings-daemon.

try killing the daemon first. "killall gnome-settings-daemon".

> Also how do I backup .gnome* dir and del the originals. I'm a Linux newb you see...

Take a file manager (nautilus, rox, konqueror, your choice). View your home dir and set it to show hidden files. Create a new directory. Copy every directory in your home dir there.

command line:  
mkdir <new dir name>
cp -R .gnome* <new dir name>/

Afterwards just delete the originals of the files you just copied.

[edit] Knome-fan beat me ^^;; yes, you will lose your settings, but you will still have a backup to get single files back should they be important.

---

### Post by Muhammad on 2005-09-03
Nautilus is dead too. Is it possible to do this in fluxbox?

I can still access the Gnome Terminal(Inside Fluxbox) BTW, but I can't killall gnome-settings-daemon.

EDIT: Apperantly Nautilus has some problems too...

---

### Post by Wolki on 2005-09-03
You can install rox to do that. It's rather small and lightweight. or just use a terminal. If gnome-terminal doesn't work, you can use one of the VTs by hitting ctrl-alt-F1.

This all sounds like your gnome is quite corrupted. If you're luck it's just the settings, then removing the config files for it (like Knome_fan and me described above) will cause it to build them again. If you're unlucky the binaries are corrupted, this *can* mean that you have a hardware defect on your RAM/hard disk.

---

### Post by Muhammad on 2005-09-03
OK then, one more stuped question.

How do I show hidden files using terminal?

Gnome Terminal is working great, nautilus was working inside fluxbox this morning, but I dunno what happened to that peice of crap now.

---

### Post by sneax on 2005-09-03
If I would be in your situation, and I had the knowledge that it worked OK before then I'd just reinstall. And make sure I don't break things.

---

### Post by Muhammad on 2005-09-03
If I reinstall, I would have to go through a 10+ hr of upgrades again... :(

And what if I encountered this problem next time?

Which brings a very important question... Is it possible to save all the packages I downloaded, so I can install them in my next installation without having to go through the downloading process again?

---

### Post by TristanMike on 2005-09-03
[QUOTE=Muhammad]If I reinstall, I would have to go through a 10+ hr of upgrades again... :(

And what if I encountered this problem next time?

Which brings a very important question... Is it possible to save all the packages I downloaded, so I can install them in my next installation without having to go through the downloading process again?[/QUOTE]You could also download the "Extras CD" from here [http://ubuntuforums.org/showthread.php?t=30147](http://ubuntuforums.org/showthread.php?t=30147)

---

### Post by Wolki on 2005-09-03
[QUOTE=Muhammad]How do I show hidden files using terminal?[/QUOTE]

With the command Knome-fan and me provided you don't need to do that.

If you want to see what's there, use ls -a

---

### Post by Muhammad on 2005-09-03
Ok I think I found the source of the crisis

There are three files in /usr/lib/

-bonobo
-bonobo-2.0
-bonobo-activation

They're colored in red when I view them by using rox.
Do you think it's possible to fix them, or should I reinstall ubuntu now without further delay.

---

### Post by bored2k on 2005-09-03
[QUOTE=Muhammad]OK then, one more stuped question.

How do I show hidden files using terminal?

Gnome Terminal is working great, nautilus was working inside fluxbox this morning, but I dunno what happened to that peice of crap now.[/QUOTE]
 ```
ls -a
```

---

### Post by bored2k on 2005-09-03
[QUOTE=Muhammad]Ok I think I found the source of the crisis

There are three files in /usr/lib/

-bonobo
-bonobo-2.0
-bonobo-activation

They're colored in red when I view them by using rox.
Do you think it's possible to fix them, or should I reinstall ubuntu now without further delay.[/QUOTE]
 There are only three files in /usr/bin ?!
Oh dear, yes, reinstall. I have enough packages there to make Nautilus hold its breath for quite some time, 1032 packages to be exact.

---

### Post by Muhammad on 2005-09-03
Not including the hidden files, no siree... :P

PLEASE, tell me it's possible to reinstall without formatting... :(

---

### Post by bored2k on 2005-09-03
[QUOTE=Muhammad]Not including the hidden files, no siree... :P

PLEASE, tell me it's possible to reinstall without formatting... :([/QUOTE]
 Of course.

---

### Post by Muhammad on 2005-09-03
And the packages I've already downloaded would still work?

Also do you think...

```
sudo apt-get install fluxbox
```

is the cause of all my problems?

---

### Post by xequence on 2005-09-03
I have no idea why it happened but something similar happened to me after installing KDE on ubuntu. I used it a bit each day for a couple days then it did that... Havnt used it since.

---

### Post by Knome_fan on 2005-09-03
Before you reinstall, did you already move the .gnome directories out of the way, as has been suggested?

---

### Post by bored2k on 2005-09-03
[QUOTE=Muhammad]And the packages I've already downloaded would still work?

Also do you think...

```
sudo apt-get install fluxbox
```

is the cause of all my problems?[/QUOTE]
 Installing fluxbox won't give you any problems at all.

And yeah, the .deb packages you have already downloaded should stay in **/var/cache/apt/archives/** . Just make sure you select the Keep partition as it is option and not the Yes, Format one.

---

### Post by Muhammad on 2005-09-03
> Before you reinstall, did you already move the .gnome directories out of the way, as has been suggested?

I tried moving and removing them, but nautilus and gnome failed to comply.

> And yeah, the .deb packages you have already downloaded should stay in /var/cache/apt/archives/ . Just make sure you select the Keep partition as it is option and not the Yes, Format one.

Ok thanks for the "you're an idiot reply", I deserve it. :D

Also thank you all for your time. :)

---

### Post by bored2k on 2005-09-03
I did not call you an idiot. I don't like to call anyone an idiot either -.- 

**> When asking for technical support:**
There are no stupid questions. You're not a stupid person simply because you do not know how to do something, or do not know the answer to a question. Everyone was a green user at one point in time. :)[http://www.ubuntuforums.org/faq.php?](http://www.ubuntuforums.org/faq.php?)

---

### Post by Wolki on 2005-09-03
[QUOTE=Muhammad]I tried moving and removing them, but nautilus and gnome failed to comply.[/QUOTE]

If you're a bit more verbose we can help you better.

Keep in mind that the files are hidden. So you have to ls -a if you want to check whether it copied them alright.

You can also just delete those folders. It seems a bit radical, but you'll probably have to set your background, theme etc again anyway.

---

### Post by Muhammad on 2005-09-03
The reason I can't be verbose is that I don't know what caused this problem, it happened suddenly, and I don't recall messing around with the system files last night.

Anyway, I reinstalled everything. :)

---

