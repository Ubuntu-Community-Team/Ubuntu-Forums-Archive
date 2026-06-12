---
title: "Kubuntu vs Ubuntu"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by richiewrt on 2006-11-22
I have been playing arround in kubuntu for the past week or so and I really like the look and feel of it, but there seems to be a little more support/documentation about ubuntu out there, so my questions is if I install ubuntu, is there an easy way to get the look and feel of kubuntu or a way to run the kubunty desktop in ubuntu?

---

### Post by Dokatz on 2006-11-22
You can have them both at the same time. KDE and Gnome both have their strong points, The Kubuntu Package comes with its own set of perferred applications for the most part, And seeing those entires in gnome is kind of lame, Other than that having them both is nice.

> sudo apt-get install kubuntu-desktop


---

### Post by richiewrt on 2006-11-22
Ok, as I am new to this could you please explane that last post? Do you mean like a dual boot situation, or will it work out to where I can just "point and click" between the two.

---

### Post by LLRNR on 2006-11-22
> **richiewrt said:**
> Do you mean like a dual boot situation, or will it work out to where I can just "point and click" between the two.

Well, it's actually something between the two. At login, you can choose your session - so you'll be able to choose KDE session for now, then log off and choose a Gnome session. It's very confortable. And the best part is that, since both Ubuntu (with Gnome as desktop environment) and Kubuntu (with KDE as desktop environment) come with their own apps, you can use any app you like, either a Gnome (Ubuntu) one, either a KDE (Kubuntu) one, within the same session. ;)

---

### Post by CatKiller on 2006-11-22
[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

---

### Post by richiewrt on 2006-11-22
Ok, so if i do the dual install will my setting for one carry over to the other, such as once i get my network working on one, will i have to go in and set it up again in the other?

---

### Post by LLRNR on 2006-11-22
Yes, certainly. The only thing I had to set up again after installing KDE on top of Gnome was to re-add the input language switcher in my taskbar. (And yes, another thing too, since I prefer working with the keyboard rather than the mouse, I had to reconfigure for KDE the custom keyboard shortcuts I had in Gnome.)

Good luck!

LLRNR

PS - Oups I forgot - the wallpapers too :D

---

### Post by rev_b on 2006-11-22
And if you have the two desktop environements installed, you can run KDE apps in gnome and vice-versa. That's the best part of it.

You can change from one to another in like less than 10 seconds, just press ctrl+alt+backspace, change login session to KDE and type username and password. No need to reboot.

I started intalling Kubuntu, then I got ubuntu-desktop, and I find myself liking gnome better. Anyway, I can use all my KDE apps, they work just fine with Gnome...

---

### Post by PartisanEntity on 2006-11-23
Sorry if I butt in. What is the difference between the two environments, any screenshots somewhere? (Or better said, any screenshots of the Kubuntu environment since I am already using Gnome?) Thank you.

---

### Post by Bachstelze on 2006-11-23
[http://kubuntu.org/screenshots.php](http://kubuntu.org/screenshots.php)

You could have done a bit of searching though, it was not especially hard ;)

I could show you some screenshots of my KDE desktops, which are a bit more customized if you want (not Kubuntu though).

---

### Post by PartisanEntity on 2006-11-23
You are right, I could have searched, in fact just a second ago I posted advising someone to search :) Point taken, and thanks for the link.

---

### Post by AndyCooll on 2006-11-23
> **rev_b said:**
> And if you have the two desktop environements installed, you can run KDE apps in gnome and vice-versa. That's the best part of it.

This is true, though of course you don't actually have to install the whole of the KDE environment to get KDE apps in GNOME. You can install just the apps that you like if you prefer. For instance I don't have the Kubuntu desktop environment installed, I just installed Amarok  on its own (Synaptic installs the relevent bits of KDE that the app needs), and it runs fine.

I usually advise beginners to start off with Ubuntu, rather than Kubuntu. And it is simply for the reason that the original poster stated, that it is the default installation and therefore getting hold of relevent information and help is a little easier. Once you've got a feel for the basics then is the time to explore ...and some people find as they explore that they actually prefer Kubuntu or Xubuntu or one of the host of desktop envoronments available. 

:cool:

---

### Post by Bachstelze on 2006-11-23
The sad part is that most of the documentation you'll find for "Ubuntu", in the wiki for ex., is desktop-independent and will work just as well in Kubuntu/Xubuntu/Whateverbuntu but people expect it to work un "Ubuntu" only. That's why I still think it's a bad idea to release them with different names.

---

### Post by richiewrt on 2006-11-23
Actually all these post were alot of help, Thanks. I now have ubuntu and kubuntu installed and working perfectly. And as far as the last port goes, I was using kubuntu for about the last week and every time I would ask a question I would get an answer that would look like, click here, type this , click here, ect....  all those little click heres I never could find in kubuntu, but were right where I was told un ubuntu. It may run on the same stuff, but the GUI is set up completly different so ubuntu is deffinantly easier to ask for help as there seems to be more people who use it and can point you in the exact right direction.  Just a newbie's $0.02 worth :)

---

### Post by Bachstelze on 2006-11-23
That's a good reason to learn to do as much stuff from command-line as possible ;)

---

### Post by richiewrt on 2006-11-23
Well, as a complete newbie, the command line stuff still is a little harry for me. I'm working on learning, but that is how i screwed up my first attempt at kubuntu and ended up doing the reinstall in the first place

---

### Post by Charles Hand on 2006-11-23
> **richiewrt said:**
>  I was using kubuntu for about the last week and every time I would ask a question I would get an answer that would look like, click here, type this , click here, ect....  

That's a problem - since Gnome is the default, most of the archived GUI-oriented help is in Gnomish. Also, I find it awkward to give help now that I've switched to KDE because noobs are most likely using Gnome. So this would be a reason for a newbie to stick with Gnome until he/she is settled in. There is power in the command line, and when I say command line I really mean editing configuration files. As one gets settled into Linux I recommend that one slowly become familiar with how to tweak things from the command line.

I want to add to this thread that we're talking about a fundamental difference between how Linux is put together versus how Windows is put together. Windows is all integrated together - the system configuration, the applications, the window manager, the drivers, the GUIs, the libraries... Linux takes a different approach called "modularity". It means that the GUI's are independent of the window managers and the window managers are independent of the applications and the system configurations are independent of everything. So whereas in Windows the desktop environment is married to all the other components of the system, in Linux the desktop environment can be changed without changing everything else. Modularity is neat, and it gives benefits all over the place, not just in selectable window managers.

-Charlie

---

### Post by chlorinekid on 2006-11-25
i tried the command mentioned to install kde desktop but i get this error:

dave@dave-laptop:~$ sudo aptitude install kubuntu-desktop 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "kubuntu-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
dave@dave-laptop:~$ 

whats wrong???

---

### Post by meteora184 on 2006-11-25
i prefer gnome rather then kde.

---

### Post by aysiu on 2006-11-25
> **chlorinekid said:**
> i tried the command mentioned to install kde desktop but i get this error:

dave@dave-laptop:~$ sudo aptitude install kubuntu-desktop 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "kubuntu-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
dave@dave-laptop:~$ 

whats wrong???
Looks as if you have nothing in your sources.list.

Try [**this**](http://www.psychocats.net/ubuntu/sources) first. Then do [**this**](http://www.psychocats.net/ubuntu/kde).

---

### Post by chlorinekid on 2006-11-25
> **aysiu said:**
> Looks as if you have nothing in your sources.list.

Try [**this**](http://www.psychocats.net/ubuntu/sources) first. Then do [**this**](http://www.psychocats.net/ubuntu/kde).thanks for the help, looks like its updating now, about 217 are currently being downloaded, i assume kde will be a part of that download??

thanks for the guides :)

---

