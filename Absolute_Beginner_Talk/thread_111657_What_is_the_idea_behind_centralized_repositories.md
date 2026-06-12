---
title: "What is the idea behind centralized repositories?"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by harisund on 2006-01-02
I am definitely not a newbie in the world of Linux, but one thing consistently surprises me. The idea of having a centralized repository that I havent seen with  Microsoft / Apple. 

Yes, it is true that Ubuntu has a huge repository, and so also does Red Hat, Gentoo and so on. But why? 

To give an example, I find some new software in Ubuntu, and want to show it to my friend running Gentoo. Unfortunately, it hasn't entered the Gentoo portage system yet. So what do we do? Resort to some other longer technique. 

Also, I understand that different softwares require different libraries (dependancies in other terms.) But how come I have never come across that in Windows. ok maybe I am wrong, but why is that for most software I needn't be worried about libraries? Or is that each software ends up installing its own libraries and I have multiple copies of the same library on my system? 

Curiosly, the only software that I installed in Windows that said it didn't find required libaries was GIMP. It complained that I needed the GTK+ Runtime environment. And of course Java programs require the JRE as well. But installing both is as simple as double clicking on a .exe file.

Don't you think it would be better if there were to be a uniform method of both installing and uninstalling software in the GNU/Linux world? When I uninstall a software, I want all the libaries it installed to vanish as well, other than those that are required by other programs of course (in other words, the functionality of deborphan to be integrated with the purge option.) 

The reason I am bringing this up is thus. When I told my Windows using friend (not a power user, just a general web surfing, emailing and chat using friend who was complaining about pop ups) about Ubuntu,and its centralized repository from where you can pick any software, his immediate response was "You mean I am limited in my choice from a single repository? can't I just download something I find on the web and install it?". Now I went on to explain in depth about the awesome size of the repository, and the capability to expand, but his initial response wasn't so good. 

Don't mistake me, but I love the power of apt-get / synaptic and couldn't live without it ..

---

### Post by Zelut on 2006-01-02
I'm sure the reason for seperate repositories is basically because each distro is run by different people.  I'm not sure that I'd want a central place for everything.  That seems a little monopolistic to me...  although it would be nice if other distros had the same packages (as per the situation with your Gentoo friend).

Personally I think apt is a MUCH better idea than the current alternative.  This makes downloading & installing very easy and provides that each user has (in most cases) the same known-stable version.

I haven't recieved the same poor reaction that you did.  Most of my reactions have been "you mean thats it?  You just click it & its installed?!" :)

---

### Post by lothar_m on 2006-01-02
[QUOTE=harisund]
Don't you think it would be better if there were to be a uniform method of both installing and uninstalling software in the GNU/Linux world? 
[/QUOTE]

That as allready been invented... its's generaly known as "compiling from source"

Off course it can be very hard process for users and sysadmin.

thats the reason why red hat made RPM, debian developed deb packages and gentoo the portage system.

---

### Post by Lord Illidan on 2006-01-02
Don't forget the autopackage and statically linked binaries like
app.run and app.bin

---

### Post by benplaut on 2006-01-02
well... rpm was created to be the standard, then deb was created to be the standard, then autopackage...

---

### Post by harisund on 2006-01-02
[QUOTE=kuyaedz]
I haven't recieved the same poor reaction that you did.  Most of my reactions have been "you mean thats it?  You just click it & its installed?!" :)[/QUOTE]

I agree with you there. A lot of people I have managed to "convert" :D indeed chose to do so simply because they were amazed at the efficiency of the apt package management system, and party due to efforts like Automatix. They are not computer science guys and don't care whether the source of the program is available or not. 

The whole "click and you are good to go" idea is terrific, I must admit

---

### Post by harisund on 2006-01-02
Could you explain what "app.run and app.bin" are? I am afraid I haven't heard those before?

---

### Post by cwaldbieser on 2006-01-02
[QUOTE=harisund]I am definitely not a newbie in the world of Linux, but one thing consistently surprises me. The idea of having a centralized repository that I havent seen with  Microsoft / Apple. 

Yes, it is true that Ubuntu has a huge repository, and so also does Red Hat, Gentoo and so on. But why? 

To give an example, I find some new software in Ubuntu, and want to show it to my friend running Gentoo. Unfortunately, it hasn't entered the Gentoo portage system yet. So what do we do? Resort to some other longer technique. 

Also, I understand that different softwares require different libraries (dependancies in other terms.) But how come I have never come across that in Windows. ok maybe I am wrong, but why is that for most software I needn't be worried about libraries? Or is that each software ends up installing its own libraries and I have multiple copies of the same library on my system? 

Curiosly, the only software that I installed in Windows that said it didn't find required libaries was GIMP. It complained that I needed the GTK+ Runtime environment. And of course Java programs require the JRE as well. But installing both is as simple as double clicking on a .exe file.

Don't you think it would be better if there were to be a uniform method of both installing and uninstalling software in the GNU/Linux world? When I uninstall a software, I want all the libaries it installed to vanish as well, other than those that are required by other programs of course (in other words, the functionality of deborphan to be integrated with the purge option.) 

The reason I am bringing this up is thus. When I told my Windows using friend (not a power user, just a general web surfing, emailing and chat using friend who was complaining about pop ups) about Ubuntu,and its centralized repository from where you can pick any software, his immediate response was "You mean I am limited in my choice from a single repository? can't I just download something I find on the web and install it?". Now I went on to explain in depth about the awesome size of the repository, and the capability to expand, but his initial response wasn't so good. 

Don't mistake me, but I love the power of apt-get / synaptic and couldn't live without it ..[/QUOTE]

Part of the reason has to do with the fact that GNU/Linux itself runs on many different architectures.  Also, a lot of the software isn't written for Linux only, but also for BSD, UNIX, Solaris, etc.  So currently, the only reasonable ways that these differences can be managed is:
1) Have binaries that conform to stock "versions" of a system (the different repositories managed by different distributions).
2) Distribute the source code and allow the dependencies to be resolved at compile time.

With Windows, you run into this a little if you try to take some old MS-DOS games and run them under XP or Win98.

---

### Post by brickbat on 2006-01-02
I love the repos.  They are one of the best things about Linux.  My only problem is that sometimes I can't find the software I want in the repos.  eg. a gui astrology program the equivalent of something like [http://www.world-of-wisdom.com/](http://www.world-of-wisdom.com/)

ciao
bb

---

### Post by Deaf_Head on 2006-01-02
Windows, OS X, Ubuntu and Suses are all OS's.

Linux is not. Why assume that each distro is, or should be compatible for any reason?

---

### Post by az on 2006-01-02
[QUOTE=harisund]I am definitely not a newbie in the world of Linux, but one thing consistently surprises me. The idea of having a centralized repository that I havent seen with  Microsoft / Apple. [/QUOTE]

That's because they are not open source.  They offer binary compatibility.  In Ubuntu (in free-libre software) the interface for connecting software is *primarily* the source code level.  It is made almost ridiculously easy to collaberate, often.

[QUOTE=harisund]
Yes, it is true that Ubuntu has a huge repository, and so also does Red Hat, Gentoo and so on. But why? [/QUOTE]

The compile it for you.   Every package is built with their toolchain and is binary-compatible with itself.

[QUOTE=harisund]
To give an example, I find some new software in Ubuntu, and want to show it to my friend running Gentoo. Unfortunately, it hasn't entered the Gentoo portage system yet. So what do we do? Resort to some other longer technique. [/QUOTE]

Yes.  Compiling from source.

[QUOTE=harisund]
Also, I understand that different softwares require different libraries (dependancies in other terms.) But how come I have never come across that in Windows. ok maybe I am wrong, but why is that for most software I needn't be worried about libraries? Or is that each software ends up installing its own libraries and I have multiple copies of the same library on my system? 
[/QUOTE]

1.  In other operating systems, you get no choice.  You build stuff with the one tool available to you.
2.  Code reuse and sharing is less elegant there, too.

[QUOTE=harisund]
Curiosly, the only software that I installed in Windows that said it didn't find required libaries was GIMP. It complained that I needed the GTK+ Runtime environment. And of course Java programs require the JRE as well. But installing both is as simple as double clicking on a .exe file.
[/QUOTE]

GIMP if FLOSS.  There are other windows apps that have the same sort of dependancies, too.  It happens when you do not use their tools to make stuff for them.

[QUOTE=harisund]
Don't you think it would be better if there were to be a uniform method of both installing and uninstalling software in the GNU/Linux world? When I uninstall a software, I want all the libaries it installed to vanish as well, other than those that are required by other programs of course (in other words, the functionality of deborphan to be integrated with the purge option.) 
[/QUOTE]

Only if it is not at the expense of making it easy for people to collaberate together.  It is better to focues on the source code interface so that the software can more easily be improved.

[QUOTE=harisund]
The reason I am bringing this up is thus. When I told my Windows using friend (not a power user, just a general web surfing, emailing and chat using friend who was complaining about pop ups) about Ubuntu,and its centralized repository from where you can pick any software, his immediate response was "You mean I am limited in my choice from a single repository? can't I just download something I find on the web and install it?". Now I went on to explain in depth about the awesome size of the repository, and the capability to expand, but his initial response wasn't so good. 
[/QUOTE]

It is not the same, but it is quite useable.  It works well.  It's just different.  It is one heck of a lot more secure, anyway.  Especially when you consider than anyone can compile a malevelent application and distribute it.  In ubuntu, it would never make it into the repos.

---

