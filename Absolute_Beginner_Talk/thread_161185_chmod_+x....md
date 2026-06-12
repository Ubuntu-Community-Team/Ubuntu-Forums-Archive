---
title: "chmod +x..."
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by Sonic132 on 2006-04-16
Ok, I just barely got my Win-Linux Dual-boot system working yesterday and now I'm trying to install files. I've tried the command above in an effort to install java(or any other program that is in '.bin' format). But it gives me the following error

```
chmod: failed to get attributes of `jdk-1_5_0_06-linux-i586.bin': No such file or directory
```

What should I do? 
I need to install all of the firefox plugins(java, quicktime, etc...), and any other programs(like Wine, and whatnot). But I haven't a clue what to do.

---

### Post by malavar on 2006-04-16
chmod: failed to get attributes of `jdk-1_5_0_06-linux-i586.bin': No such file or directory

No such file or directory... make sure you are in the correct directory or maybe you mispelled something.
btw if you need help getting all your plugins for media players and browsers go here:

[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=mp3](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=mp3)

---

### Post by Sonic132 on 2006-04-16
I finally got the Install Shield prog to work for the java developers kit. Instead of typing 'chmod +x'. A page I was reading said, 'chmod a+x'. I still dont entirely know what that means but it somehow made Ubuntu start the install anyway.

---

### Post by Sonic132 on 2006-04-16
One other thing I want to get working is the 'su' command. I've read on various websites that the 'super user' command is used alot. But whenever it asks me for a password I dont know what it is. Is there a Ubuntu default pw? Because it never told me what it was during or after install, or allowed me to set one.

---

### Post by malavar on 2006-04-16
chmod man page explains this. 

chmod a+x would give all (user group and others) execute permission
chmod ugo+rwx would = owner(user) group and others get (R)ead (W)rite and e(X)ecute permissions.

---

### Post by malavar on 2006-04-16
[QUOTE=Sonic132]One other thing I want to get working is the 'su' command. I've read on various websites that the 'super user' command is used alot. But whenever it asks me for a password I dont know what it is. Is there a Ubuntu default pw? Because it never told me what it was during or after install, or allowed me to set one.[/QUOTE]

su password is the root password. to change the root password type
sudo passwd root

---

### Post by Sonic132 on 2006-04-16
[QUOTE=malavar]chmod man page explains this. 

chmod a+x would give all (user group and others) execute permission
chmod ugo+rwx would = owner(user) group and others get (R)ead (W)rite and e(X)ecute permissions.[/QUOTE]

Ohhh! I thought the 'a+x' command converted the '.bin' file to a executive. I think I am beginning to understand. ](*,)  Oh and thanks for the directions on changing the root password.

---

### Post by Sonic132 on 2006-04-16
```
chmod a+x R
   ~/Desktop $ su ./R
Unknown id: ./R
   ~/Desktop $ sudo
usage: sudo -V | -h | -L | -l | -v | -k | -K | [-H] [-P] [-S] [-b] [-p prompt]
            [-u username/#uid] -s | <command>
   ~/Desktop $ sudo ./R
Password:
Sorry, try again.
Password:
Sorry, try again.
Password:
Sorry, try again.
sudo: 3 incorrect password attempts
```
Ok, so basicly. I used the 'su' command. But the pw I set is no longer the password. I typed it twice when I set it. So it should be right. What should I do? Try and change it again? Or do I need the password in order to change the password(Catch 22)?

---

### Post by Sonic132 on 2006-04-16
In one of the Sticky Threads it says that the Linux equivalent of Winamp is Xmms, so I downloaded it. But the instructions aren't written in Noobie. So what am I supposed to do exactly to install it?

---

### Post by htinn on 2006-04-16
Sonic132, search for "xmms" in Synaptic and install it there.

---

### Post by Sonic132 on 2006-04-16
Ok, so basicly whatever I download goes in Synaptic? Then I can install it from there?
Thanks alot.

---

### Post by htinn on 2006-04-16
I think you misunderstood. What I mean is that you do not download anything. Synaptic downloads, installs, and configures everything for you. All you have to do is load Synaptic and search for whatever it is you want.

---

### Post by Sonic132 on 2006-04-16
[QUOTE=htinn]I think you misunderstood. What I mean is that you do not download anything. Synaptic downloads, installs, and configures everything for you. All you have to do is load Synaptic and search for whatever it is you want.[/QUOTE]
Yes but, what if the file you want isn't in Synaptic? How exactly do you go about adding it?

---

### Post by htinn on 2006-04-16
In that case, you either need to add "repos" ([https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)) or you need to download a package (deb file) and use dpkg to install that (sudo dpkg -i somefile.deb).

Beware however that installing random deb files can mess up your system.

---

### Post by Sonic132 on 2006-04-16
[QUOTE=htinn]In that case, you either need to add "repos" ([https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)) or you need to download a package (deb file) and use dpkg to install that (sudo dpkg -i somefile.deb).

Beware however that installing random deb files can mess up your system.[/QUOTE]

I've been trying unsuccessfully to download and install xine and Kaffeine. But for some reason it keeps saying I'm missing something once it comes down to doing the xine ui.

Is there a way I can get xine working through Synaptic?

---

### Post by htinn on 2006-04-16
Xine should be available in the "universe" repo (named "xine-ui").

---

### Post by Mustard on 2006-04-16
[QUOTE=Sonic132]I've been trying unsuccessfully to download and install xine and Kaffeine. But for some reason it keeps saying I'm missing something once it comes down to doing the xine ui.

Is there a way I can get xine working through Synaptic?[/QUOTE]

There certainly is.  It's in the universe repository, which is a community maintained repository and not enabled by default.  Try the link given above or this link below to enable both the Universe and Multiverse repositories.
[http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse](http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse)

Once you have them enabled you can use the 'Reload' button in Synaptic to get the latest package lists and use the 'Search' functions in Synaptic to find the packages you want.

If you recieve error messages then post the error messages in here, as they are the easiest way for us to diagnose what the problem is.

---

### Post by Sonic132 on 2006-04-16
[QUOTE=htinn]Xine should be available in the "universe" repo (named "xine-ui").[/QUOTE]
Ok, I opened up Synaptic and searched for xine-ui but it doesn't show anything. That's why I went the hard way and manually looked it up, downloaded it, and then attempted to install it. But to no avail.
Do you have to have the "Breezy Badger" version of Ubuntu to use it? I'm almost done downloading the iso on my other computer.
Also, do I keep all my current Warty Warthog settings once I install the Breezy Badger, and will my system still be dual-boot?

---

### Post by Sonic132 on 2006-04-16
> There certainly is. It's in the universe repository, which is a community maintained repository and not enabled by default. Try the link given above or this link below to enable both the Universe and Multiverse repositories.
[http://help.ubuntu.com/starterguide/...addinguniverse](http://help.ubuntu.com/starterguide/...addinguniverse)

Once you have them enabled you can use the 'Reload' button in Synaptic to get the latest package lists and use the 'Search' functions in Synaptic to find the packages you want.

If you recieve error messages then post the error messages in here, as they are the easiest way for us to diagnose what the problem is.
I visited that page, and while it's very informative. It refers to several options that aren't in The Warty Warthog. Do I need the Breezy Badger to use this information?

---

### Post by htinn on 2006-04-16
It really shouldn't make any difference. "xine-ui" has always been "xine-ui" (from Warty to Dapper) in Universe.

---

### Post by Mustard on 2006-04-16
[QUOTE=Sonic132]I visited that page, and while it's very informative. It refers to several options that aren't in The Warty Warthog. Do I need the Breezy Badger to use this information?[/QUOTE]

It doesnt make a difference in terms of the package names.  It does make a **big difference** in that you would need to use Warty Warthog sources, rather than the two upgrades since then, Hoary Hedgehog and Breezy Badger.  When did support for Wary Warthog finish does anyone know?  I wonder whether the 18 months has run out for Warty.

If you are upgrading you really should be upgrading one version at a time too.  Warty to Hoary, then Hoary to Breezy.

If I had realised you were using Warty Warthog, I wouldn't have shown you those links, as you could break your system using the wrong sources.list.

---

