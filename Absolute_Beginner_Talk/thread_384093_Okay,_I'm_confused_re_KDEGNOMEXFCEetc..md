---
title: "Okay, I'm confused re: KDE/GNOME/XFCE/etc."
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by herbster on 2007-03-14
I just have a few questions regarding Gnome/KDE/XFCE. Each one of them is exactly what, a manager that dictates how the desktop is viewed and what you can do with it? They're not programs, but rather just environments right?

I am using Gnome right now on Ubuntu 6.10. Let's say I want to install XFCE or KDE.
1. How/where from?
2. If I do install say XFCE or KDE, what exactly happens? Does it create another login session and nothing on my system changes, all is good and I just choose KDE/XFCE whenever I want or make them default? Do my programs and such change, or what?
3. How does Beryl/XGL respond to either? I currently use Beryl on an XGL session successfully and love it. If I should use KDE for example how would that affect it?

I guess my confusion arises from thinking that KDE or XFCE might be like a new Ubuntu I have to set up all over again, which with everything working perfectly I surely don't want lol..


Really appreciate any help from you folks!

---

### Post by orkim on 2007-03-14
> **herbster said:**
> I just have a few questions regarding Gnome/KDE/XFCE. Each one of them is exactly what, a manager that dictates how the desktop is viewed and what you can do with it? They're not programs, but rather just environments right?

I am using Gnome right now on Ubuntu 6.10. Let's say I want to install XFCE or KDE.
1. How/where from?
2. If I do install say XFCE or KDE, what exactly happens? Does it create another login session and nothing on my system changes, all is good and I just choose KDE/XFCE whenever I want or make them default? Do my programs and such change, or what?
3. How does Beryl/XGL respond to either? I currently use Beryl on an XGL session successfully and love it. If I should use KDE for example how would that affect it?

I guess my confusion arises from thinking that KDE or XFCE might be like a new Ubuntu I have to set up all over again, which with everything working perfectly I surely don't want lol..


Really appreciate any help from you folks!

Packages are what we use to get new software on our system.  A package manager will be helpful for this task, such as Sympatic.  Anything you install (packages) will be from the repositories.  There are several repositories such as universe or multiverse.  That is the how/where.

XFCE/KDE are two different window managers.  Window managers do just that: manage the windows and "feel" of your desktop.  The actual server running behind the scenes is X11 or Xorg (Ubuntu is Xorg) and typically doesnt do things that you can "see".  Xorg handles things like message handling, resource allocation, and interprocess communication; stuff you probably don't care to know about.  A window manger is "what you see" when you are in a graphical environment.

Beryl is still a beta application.  You should read the sticked topics in this very forum for more information about it in particular.  It's typically not very stable and may not be a good choice for a production system.  They say: living on the edge, you're bound to bleed.   Your mileage may vary.

Hope that helps.

-orkim

---

### Post by meborc on 2007-03-14
they are desktop environments

you can get KDE - "sudo aptitude install kubuntu-desktop"
you can get XFCE - "sudo aptitude install xubuntu-desktop"

after doing that you can chose from the login screen > sessions which of them you want to use... you can have them all installed

on the 3d eyecandy stuff - i have no idea :)

---

### Post by Kateikyoushi on 2007-03-14
1. can install them with the following commands.

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
sudo aptitude install xubuntu-desktop
```

If you only want the kde and xfce not the whole package with apps etc.

```
sudo aptitude update
sudo aptitude install kde-core
sudo aptitude install xfce
```

2. You can choose at login which you want to use.
3. Beryl works with all of them, at least it did for me.

You can switch from ubuntu to kubuntu or xubuntu, these are just desktop environments and application packages on the top of the same core, not really separate distributions.

---

### Post by charles.g.moore on 2007-03-14
1. if you wabted to for instance install the KDE desktop you would type
sudo aptitude install kubuntu-desktop

2. As I understand it when you install KDE onto gnome you get all of the KDE libraries which changes (adds) to your system.  Your programs do not necessarily change but you do add more programs which serve the same purpose (1 for KDE 1 for Gnome)

I have heard that many people recommend only installing one desktop environment, I installed KDE onto my Gnome ubuntu laptop and all is fine except for my program menu is bloated with too many apps from each environment, it does not bother me too much but it may bother you.

Once you have KDE & Gnomeinstalled onto the same system you can choose which session to log into when you are entering your username / password

---

### Post by astronic on 2007-03-14
> **orkim said:**
> XFCE/KDE are two different window managers.
No, XFCE and KDE are not window managers at all but desktop environments, which ship with a window manager (Xfwm in case of XFCE and kwin in case of KDE). And of course you can also use other window managers with XFCE or KDE.

> Window managers do just that: manage the windows and "feel" of your desktop.
No, a window manager usually just manages windows and has nothing to do with the desktop.

> The actual server running behind the scenes is X11 or Xorg (Ubuntu is Xorg) and typically doesnt do things that you can "see".
No. You are confusing XFree86 with X11. XFree86 and Xorg both are X11 implementations.

> Xorg handles things like message handling, resource allocation, and interprocess communication; stuff you probably don't care to know about.
The X server handles surprisingly little IPC, otherwise we wouldn't need stuff like DCOP or DBUS.

> A window manger is "what you see" when you are in a graphical environment.
The only thing I see of my window manager at the moment are window decorations and window frames.

Regards,
Stefan

---

### Post by loanrangie on 2007-03-14
> **meborc said:**
> they are desktop environments

you can get KDE - "sudo aptitude install kubuntu-desktop"
you can get XFCE - "sudo aptitude install xubuntu-desktop"



 Where do you run those commands from ? i currently have Ubuntu 6.10 and like the look of Kubuntu.

---

### Post by hyper_ch on 2007-03-14
you open a shell terminal (or command line interface [CLI]) and just type in those commands... then you will be asked for your user password and then it starts downloading and installing (if you have an internet connection).

---

### Post by j.miller565 on 2007-03-14
Since you're using GNOME, you should run the commands in the "Terminal". BTW, I use GNOME and KDE. I  can swap between the others by changing the session on the "Sessions" button on the GDM manger. BTW, when you install KDE, it'll ask you if you want to use KDM or GDM. Personally, I prefer GDM. I hope this has helped :)

---

### Post by Kateikyoushi on 2007-03-14
You can copy paste them to terminal. Applications > system tools > terminal.
You might want to read this. [LINK]("http://www.psychocats.net/ubuntu/terminal")

---

### Post by NikoC on 2007-03-14
I've tried both Gnome (my favourite) and KDE with Beryl and they both work flawlessly!

---

### Post by herbster on 2007-03-14
Wow, thanks for the replies guys! It's very clear now :)

I see a couple of you have KDE and Gnome and prefer Gnome, would you care to give a few points as to why? I'm going to install KDE and XFCE later tonight to give them a shot.

Also, is either of them "faster" than the other? ie., Uses less system resources or are they equal in that department?

---

### Post by Songwind on 2007-03-14
I use both and prefer KDE.

I like the granularity of the setup options.  I tend to like complicated things with a lot of options, just because I am the sort of guy that likes to tweak this and tweak that.

I also like the desktop setup options for dual-monitor configurations better than I did in Gnome.

I like Konqueror (and the KIO slaves) better than I like Nautilus.  I really like the ability to put [ftp://foo.com/bar](ftp://foo.com/bar) or whatever anywhere that KDE apps ask me for a file name and just watch it download it and install in one step.  I don't care too much for it as a web browser because of compatibility issues, but it's okay.

Of the things that I do regularly on my computer at home, I have found that I prefer the KDE native apps to the GTK apps.  I like Kopete a bit more than GAIM, KTorrent more than bittorrent, KOffice more than OpenOffice.org, that sort of thing.

Oh, and aRts (sound system) has given me a lot less hassle than the Gnome sound system did.

Honestly, though, it's close.  I wouldn't be bemoaning my fate or anything if I hadn't tried KDE.

---

### Post by Arby on 2007-03-14
Desktop environment is completely down to personal choice. You are doing the right thing by trying the different options. This is the Ubuntu forum rather than Kubuntu or Xubuntu so you are bound to get more responses from Gnome users here.

Personally I like KDE. The best thing to do is install them all and try working with each one _exclusively_ for a week (or a month if you're patient). Then choose the one that feels best to you.

In terms of speed, this is a never ending debate. XFCE is considered to be lighter than KDE or Gnome in terms of using less memory and disk space. This doesn't necessarily make it 'faster'.

Basically, do what your doing, give them all a spin and see what you prefer.

---

### Post by herbster on 2007-03-14
Man you guys are so helpful :) :)

Yeah, I really want to install them all but just the "environment\manager" or however it is called, itself. No additional programs to bloat my menus or anything... which brings up the question: If I install KDE and XFCE, will I be able to log in with them and use my normal Gnome programs to test them out or is it wise/necessary to install all these extra programs if I'm going to bother with another DE?

---

### Post by Wikzo on 2007-03-14
Is it easy to/how do you uninstall KDE in Ubuntu, if you do not like it?

How much space do KDE takes, if you only install the core, not all the app. and so on?

**EDIT:** Ok, now I just installed KDE-core in Synaptic. Was about 70 MB ... it is working pretty good. It is easy to switch between GNOME and KDE. But I once got a KDE look in GNOME session because of Beryl. A bit strange :P

---

### Post by hyper_ch on 2007-03-15
you can use GNOME, KDE and Xfce programs in either desktop environments. However GNOME and Xfce use GTK, KDE however uses (damn, what's that thing called again)... this means if you run GTK apps in GNOME or Xfce less libraries will be required to be loaded... if you run GTK apps in KDE more will be loaded... the same thing goes vice-versa. If you use KDE apps in Xfce (as I do) or in GNOME then additional KDE libs will be loaded...

But you can run all of it in all of the environments :)

---

### Post by Nythain on 2007-03-15
hmmm... my advice, find the desktop environment that you like most... in my case kde... try to stick with apps that rely on that library set... but since any app will run on any DE as long as you have the libraries, just install what you need to run whatever as you need it... like i run KDE but despise Adept, so i install Synaptic, wich relies on some of the gnome libraries, or at least a large chunk of gtk, but i dont have the full blown gnome DE installed cause i think its UGLY :P... beryl will work on just about anything ceptin Enlightenment, then again if you are runnin that, you shouldnt need beryl anyways (w00t enlightenment)... Compiz tends to rely more heavily on gnome though, so it would be a suggestion instead of beryl if you like gnome over kde or xfce... hope that didnt confuse you and possibly helped a little

---

### Post by Wikzo on 2007-03-15
Yesterday I installed "KDE-Core" via Synaptic. How do I remove it again? I have selected "Completly remove", but I can still log into KDE desktop session. Which files should I delete?

---

