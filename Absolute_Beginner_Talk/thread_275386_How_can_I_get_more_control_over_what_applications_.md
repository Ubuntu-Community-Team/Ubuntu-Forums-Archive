---
title: "How can I get more control over what applications are installed?"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by nietorigineel on 2006-10-11
I have just installed Ubuntu, and went to Xubuntu, by means of the method described at [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce). That just to describe the state my system is in right now.

Anyway, my main annoyance till now is the uninstall procedures. I have been browsing through 'synaptic', but there are like a billion entries in there. On top of that, all is mixed up: drivers, software, system tools. 

Is there an easy way to:

-Keep all stuff that is needed for my hardware to perform (sound, LAN, videocard).

-Keep all 'system' programs.

-Get rid of all third party software. I will select/find that myself.

Maybe someone tried to accomplish this with xubuntu before me and still has the commands?

Or is there a list of basic things to keep so i can kick off everything else?

---

### Post by Najand on 2006-10-11
> **nietorigineel said:**
> I have just installed Ubuntu, and went to Xubuntu, by means of the method described at [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce). That just to describe the state my system is in right now.

Anyway, my main annoyance till now is the uninstall procedures. I have been browsing through 'synaptic', but there are like a billion entries in there. On top of that, all is mixed up: drivers, software, system tools. 

Is there an easy way to:

-Keep all stuff that is needed for my hardware to perform (sound, LAN, videocard).

-Keep all 'system' programs.

-Get rid of all third party software. I will select/find that myself.

Maybe someone tried to accomplish this with xubuntu before me and still has the commands?

Or is there a list of basic things to keep so i can kick off everything else?

Everything in Linux is made by files (except modules)... And the system core is called the Kernel. You will not remove your kernel for sure. Once you get familiar with Linux, you will learn little by little how to deal with different files/configurations and you will find it is much easier to have an "apt" package manager than Windows' Add/Remove Application. Everyone, who are here has kicked off the system at least a dozen of times.... That mistakes make you learn who to deal with linux. However configuration with Synaptic is not difficult. The other GUI based package manager is "aptitude" (Try "sudo aptitude" in Terminal.) which has set everything in a nice order.

---

### Post by mozetti on 2006-10-11
You can accomplish this by downloading the alternate-install iso, installing in "server" mode, then aptitude-install ubuntu/kubuntu/xubuntu-desktop (whichvever you prefer or all of them), and then adding programs from there.

---

### Post by CatKiller on 2006-10-11
It's easy enough to get a complete minimalist install. If you do the "server" install then you get almost nothing - just the bare minimum. Then you can install things through the command line, such as ```
sudo aptitude install xubuntu-desktop
```

What you've asked for is hardly like the behaviour of Windows though - a default install of that comes with all kinds of crap. And you have to remember what all that crap is in order to keep it up to date. With the package system, it can automatically tell you when any piece of software has a newer version available, and let you update it with a couple of mouse clicks.

---

### Post by Najand on 2006-10-11
Well, I don't think he/she has a problem installing ubuntu... his/her problem is how to deal with packages....

---

### Post by brt on 2006-10-11
the day "Linux" becomes more like Windose will be the day when i stop using "Linux".

to your particular problem:

as far as i know, is a better tracking of dependencies on uninstalling for synaptic is already being discussed. 

now you could use aptitude instead of synaptic for un/installing packages:
```
sudo aptitude install <package-name>
sudo aptitude remove <package-name>
```

but i think most ubuntu users don't care about this problem, as it really does not hurt the system, if you have some unused packages installed.

---

### Post by podunk on 2006-10-11
The things you install through the package manager are very easy to uninstall. Just right click and chose "Mark for removal" then click the Apply button at the top.

3rd party (not the right term, that's a windows term) apps can be installed with the 
checkinstall

command - which enters an uninstall routine in the package manager. You have to install 
checkinstall
with the package manager first

You can get a good view of what is installed on your computer by looking in the following directories:
/usr/bin
usr/local/bin

ah, it's not a good idea to delete things out of
/bin
:-D

I made aq txt file with what packages I need to install for drivers and stuff, the text commands themselves, listed in the order they need to be installed (video, printer, scanner, network, eye candy etc) - I learned to do this using Windows. :-D

---

### Post by petri on 2006-10-11
Do not browse in Synaptic, do please Search in Synaptic ;)

- Drivers will be safe

- 'System' programs will be safe

- Define "third party software"?

---

### Post by nietorigineel on 2006-10-11
First of all: thanks for the responses. 

I've tried aptitude, but even then it remains totally unclear for me for the majority of the packages if i need them or not. I understand the Kernel cannot be influenced from within the package manager, but you can destroy Xfce, if i'm correct?

I had already been trying to remove some things, resulting in Xfce not starting up at boot anymore at least, so randomly removing packages might not be the solution either.

I Guess my best bet would be installing from the alternative cd.

---

### Post by aysiu on 2006-10-11
I'm not sure what the thread subject title has to do with your question.

You're asking if you can do a minimalist installation and add what you want... can that be done in Windows?

It's seems a pretty trivial task in Ubuntu--a server install and then *aptitude* or *apt-get* only the software you want in addition to that.

---

### Post by bodhi.zazen on 2006-10-11
> **nietorigineel said:**
> First of all: thanks for the responses. 

I've tried aptitude, but even then it remains totally unclear for me for the majority of the packages if i need them or not. I understand the Kernel cannot be influenced from within the package manager, but you can destroy Xfce, if i'm correct?

I had already been trying to remove some things, resulting in Xfce not starting up at boot anymore at least, so randomly removing packages might not be the solution either.

I Guess my best bet would be installing from the alternative cd.

LOL :lol:

May I ask how much experience you have with Linux?

If you have minimal experience, I advise you use Xubuntu as is for a month.

In general: Do not remove something you are unfamiliar with. If you do not know what it is, google. 

Here is a line to a listing and description of ubuntu packages:

[Ubuntu Packages](http://packages.ubuntu.com/dapper/)

If you prefer, go ahead and dive in.  I suggest Fluxbuntu:

[[color=navy]fluxbuntu[/color]](http://fluxbuntu.org/)

Or a server install with additional packages as needed. The hard part of a server install will be:
[list=number][*]The server install has no gui and is CLI. You will have to install X and a desktop environment.[*]You do not have enough experience yet to know what you need.[/list]

---

### Post by nietorigineel on 2006-10-11
> 
If you have minimal experience, I advise you use Xubuntu as is for a month.

In general: Do not remove something you are unfamiliar with. If you do not know what it is, google. 


Thanks for the advice!

> 
I'm not sure what the thread subject title has to do with your question.

You're asking if you can do a minimalist installation and add what you want... can that be done in Windows?

It's seems a pretty trivial task in Ubuntu--a server install and then aptitude or apt-get only the software you want in addition to that.


Let me try to answer your questions:

-In windows there is a clear division in adding/removing parts of windows, adding/removing drivers and adding/removing other software. While (at first glance) this different in linux. In windows, if i try to remove a program, it doesn't tell me it will also remove 4 other programs. In this aspect Windows is more intuitive.

-You can install windows without any programs if you wish. Then you know you start from the very basis. All that is needed for windows itself is there, and nothing more. 

-It is pretty trivial, but for me only in retrospect. Ubuntu is claiming ease of install, and provides that, but at the cost of no influence from my part on what exactly gets installed at all (a little bit un-linux-like). A division in typical/custom would have been appreciated. (There must be many people on this forum thinking i'm totally spoiled by windows after this remark :) )

---

### Post by aysiu on 2006-10-11
> **nietorigineel said:**
> 
-In windows there is a clear division in adding/removing parts of windows, adding/removing drivers and adding/removing other software. While (at first glance) this different in linux. Well, Linux is just a kernel, so if you remove everything except the kernel... you won't have much to work with. As others have told you, a server install is about as basic as you can get with functionality and no programs. > In windows, if i try to remove a program, it doesn't tell me it will also remove 4 other programs. In this aspect Windows is more intuitive. Ubuntu will rarely remove a program if you remove another program. It will remove a lot of dependencies--for example, if you remove Banshee, it's not going to keep Banshee-DAAP in there, but I would hardly call Banshee-DAAP a program.

What Windows will do when you remove a program is say "Hey, it looks as if you're not using this .dll. Do you want to remove it? If another program needs it, this can be dangerous" And, of course, you'll never know whether another program needs or not, so you keep it. And if another program did need it after it's removed... well, then you'll just get errors when you try to run that program.

> 
-You can install windows without any programs if you wish. Then you know you start from the very basis. All that is needed for windows itself is there, and nothing more.  Really? How do you do that? You can install Windows without Internet Explorer, Notepad, MSPaint, and Explorer?

> -It is pretty trivial, but for me only in retrospect. Ubuntu is claiming ease of install, and provides that, but at the cost of no influence from my part on what exactly gets installed at all (a little bit un-linux-like). A division in typical/custom would have been appreciated. (There must be many people on this forum thinking i'm totally spoiled by windows after this remark :) ) There is a division in typical/custom. The Desktop CD is typical. The Alternate CD is custom.

---

### Post by christhemonkey on 2006-10-11
I think what you want, 
is to install xubuntu-desktop, 
and then anything else you install,

Then when you come to remove things, if they want to remove xubuntu-desktop, then you know that you cant remove them.

---

### Post by aysiu on 2006-10-11
It's "safe" to remove *xubuntu-desktop* (*safe* meaning it won't damage your system), but you won't get upgraded properly if you do.

An upgrade without a *_____-desktop* package will just give you newer versions of applications you already have installed (maybe this is what you want). An upgrade with the *_____-desktop* package installed will additionally take away and replace programs with better programs.

I'm taking basic programs here. If you have XMMS or KRename installed, those will not be uninstalled unless you uninstall them yourself.

By the way, I've retitled the thread to something more accurate and less provocative.

---

### Post by nietorigineel on 2006-10-11
> Well, Linux is just a kernel, so if you remove everything except the kernel... you won't have much to work with. As others have told you, a server install is about as basic as you can get with functionality and no programs.  Ubuntu will rarely remove a program if you remove another program. It will remove a lot of dependencies--for example, if you remove Banshee, it's not going to keep Banshee-DAAP in there, but I would hardly call Banshee-DAAP a program.

You give one example. I don't have them available right here right now, but there are certainly far more obscure connections to be found. Add to that that removing Banshee, it will get rid of Banshee-DAAP, but not Banshee-DEEP (not that that exists, you get the point i hope)

> 
What Windows will do when you remove a program is say "Hey, it looks as if you're not using this .dll. Do you want to remove it? If another program needs it, this can be dangerous" And, of course, you'll never know whether another program needs or not, so you keep it. And if another program did need it after it's removed... well, then you'll just get errors when you try to run that program.


Yes it does that. But that is one DLL, not a list of 4 or 5 other programs, with names sometimes suggesting they are of big importance (while connected to what seems just a small program)

> 
 Really? How do you do that? You can install Windows without Internet Explorer, Notepad, MSPaint, and Explorer?


My last install is quite a while ago, but i think you can. If i'm incorrect you can easily 'add/remove windows components' afterwards. 

> 
 There is a division in typical/custom. The Desktop CD is typical. The Alternate CD is custom.

So I discovered.

At the end of the day, I still believe that if something were to be build in the fancy GUI installer giving the user control on what software to install would be greatly appreciated. (Not only by me)

---

### Post by steve.horsley on 2006-10-11
I'm not trying to pick an argument, but why are you trying to remove lots of packages from the default install? I've never heard of anyone trying to remove notepad, wordpad, IE, the picture viewer thingy, the file manager, the print spooler, the GUI etc. from Windows. It seems to me that you are going to a lot of effort and possible pain (from removing important packages) and I really don't see why. 

And how far do you want to go? Did you realise (I don't think anyone has mentioned it here) that the "server" install doesn't install a GUI at all? You get a 24x80 Black and white text prompt. The GUI is optional, and there are several different ones to choose from. What is your objective?

> In windows, if i try to remove a program, it doesn't tell me it will also remove 4 other programs. In this aspect Windows is more intuitive. I have to disagree here. I Windows, if you remove a progeram that others need, the 4 others simply stop working, and crash next time you try to start them. That seems less rather intuitive to me than being told about it when you do the removal.

---

### Post by aysiu on 2006-10-11
> **nietorigineel said:**
> You give one example. I don't have them available right here right now, but there are certainly far more obscure connections to be found. Add to that that removing Banshee, it will get rid of Banshee-DAAP, but not Banshee-DEEP (not that that exists, you get the point i hope) I guess it's a matter of semantics. In my mind, there are *programs* and then there are *packages*. All programs are packages but not all packages are programs.

For example, *xubuntu-desktop* is just a pointer to the default set of packages for Xubuntu. *libdvdcss2* is just a library that helps you play DVDs--it's not an actual DVD-playing program.

> Yes it does that. But that is one DLL, not a list of 4 or 5 other programs, with names sometimes suggesting they are of big importance (while connected to what seems just a small program) Well, I prefer having descriptive names than cryptically labeled .dll files. At least in Ubuntu, you can look in Synaptic or Adept to see the descriptions of packages and reinstall them easily if need be. How do you get that .dll back? Who knows?

> 
My last install is quite a while ago, but i think you can.  Please try it again. Forgive me if I don't trust your memory on this one. > If i'm incorrect you can easily 'add/remove windows components' afterwards. You can't fully remove Internet Explorer from Windows, but you can fully remove Firefox from Ubuntu.


> At the end of the day, I still believe that if something were to be build in the fancy GUI installer giving the user control on what software to install would be greatly appreciated. (Not only by me) This isn't a Windows/Linux issue.

First of all, Windows does not give you that control. It installs a whole bunch of crap you have to later remove or deactivate. If you use the Alternate CD from Ubuntu, you can fully customize your Ubuntu experience from the ground up.

Secondly, Ubuntu is not all of Linux. It is one Linux distribution. Plenty of other distros like Xandros, Mandriva, and Fedora allow you to hand-select during installation which applications you want.

Ubuntu's Desktop CD strives for simplicity--only a few questions so as not to confuse new users, one application per task (at least initially).

**Edit**: Here's a screenshot from Fedora's installer, which allows you to pick packages before you install. It has general categories, and if you click on *details* you can (de)select specific programs, too.

---

### Post by nietorigineel on 2006-10-11
> **steve.horsley said:**
> I'm not trying to pick an argument, but why are you trying to remove lots of packages from the default install? I've never heard of anyone trying to remove notepad, wordpad, IE, the picture viewer thingy, the file manager, the print spooler, the GUI etc. from Windows. It seems to me that you are going to a lot of effort and possible pain (from removing important packages) and I really don't see why. 

I might be a bit of a difficult person, i grant you that :). 

Anyhow, what I don't want to do is get rid of the print spooler, the file manager, the GUI and that kind of stuff. 

It's just that I prefer to have nothing outside of those (allow me to call them 'basic') programs.

I'd like Opera instead of Firefox for example, and VLC as my mediaplayer.

Now when i started removing stuff I kinda got overwhelmed by the amount of packages there. I figured I'd like it more if all of that was gone, and i just step by step get the stuff i need. In a way guaranteeing i have a minimal system. 

> 
And how far do you want to go? Did you realise (I don't think anyone has mentioned it here) that the "server" install doesn't install a GUI at all? You get a 24x80 Black and white text prompt. The GUI is optional, and there are several different ones to choose from. What is your objective?

I did realise that, but so far installing stuff from the commandline has worked really nice. I was hoping (with some help from the internet perhaps) I would manage without too many problems.

---

### Post by aysiu on 2006-10-11
Ubuntu isn't touted as barebones--just simple. So it seems to me your expectations were off.

Still, what you want can be done.

**Step 1**: Enable extra repositories by following these instructions...
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

**Step 2**: Paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) ```
sudo aptitude update
sudo aptitude install opera vlc
sudo aptitude remove firefox xfmedia
```

---

### Post by nietorigineel on 2006-10-11
> **aysiu said:**
> Ubuntu isn't touted as barebones--just simple. So it seems to me your expectations were off.
You probably are very right.

> 
Still, what you want can be done.

**Step 1**: Enable extra repositories by following these instructions...
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

**Step 2**: Paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) ```
sudo aptitude update
sudo aptitude install opera vlc
sudo aptitude remove firefox xfmedia
```

I have installed opera, and removed firefox. But that's only one, there are billions more. That's why I like it better the other way around, instead of removing everything i don't want, start with little and build from there.

---

### Post by aysiu on 2006-10-11
As I said before, there are other distros that let you choose packages before installation.

If you really want to stick with Ubuntu, though, do a server install off the Alternate CD.

Then type in these commands: ```
sudo aptitude update
sudo aptitude install x-window-system-core xterm gdm xfce4 menu synaptic
sudo /etc/init.d/gdm start
``` You can then use Synaptic or *aptitude* to install more packages as you need them.

In fact, one good way to do this would be to type in ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
``` It'll then list a bunch of packages and say "Do you want to install these?" Say no to installing them, but then take a look at the package list. If a package intrigues you, you can read more about it in Synaptic or just go ahead and install it (just that one package).

---

### Post by bodhi.zazen on 2006-10-11
> **nietorigineel said:**
> I have installed opera, and removed firefox. But that's only one, there are billions more.

Billions ? :---) :tongue:

> **nietorigineel said:**
> That's why I like it better the other way around, instead of removing everything i don't want, start with little and build from there.

[color=navy][size=4]Server Install !!![/size][/color] \\:D/

---

### Post by steve.horsley on 2006-10-11
Aysiu's advice is good, it that's the way you want to go. Very good in fact, and you will undoubtedly learn a great deal about the way things hang together. I know you will have to install the X GUI stuff, I'm not sure if the server package installs such things as a print spooler, scheduler etc. There still may be things to delete after a server install. It could be interesting, given the time.

---

