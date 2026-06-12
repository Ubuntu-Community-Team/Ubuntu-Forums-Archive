---
title: "Linux!"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by poysama on 2007-09-10
Hello, I am really having fun with Linux especially in (K,X)Ubuntu distro.

A few questions
1. When updating from package managers, is it ok to do something like watching media, playing sounds? Will it not affect the updating process?
2. From what I understand, sudo gives a user the privilege to install anything in a PC? Does this make you root for a while? They say when logged-in as root, it brings chaos to your PC.
3. Do I need an antivirus for Linux? 
4. How do I install printers and other USB-type devices?
5. I'm a C programmer, how do I run C in Ubuntu. I've heard that there's this GCC thing which runs, I tried running it in the terminal but didn't know what to do.

BTW, I'm currently on Kubuntu because I like KDE. 
Still 3 days of Linux Experience!

---

### Post by ubuntukerala1980 on 2007-09-10
No need for antivirux in linux. But you can use firestarter. Or set up iptables.
[http://www.linux.com/articles/55319]("http://www.linux.com/articles/55319")

To run C. Enter the directory where your c program is. Type in terminal
gcc -o helloworld helloworld.c
 to run your program 
./helloworld

For c++ programs use g++ instead of gcc

:guitar:

---

### Post by aquavitae on 2007-09-10
> **poysama said:**
> 
1. When updating from package managers, is it ok to do something like watching media, playing sounds? Will it not affect the updating process? Ahh, I sense someone used to windows :D.  Yes, you can play movies etc - it won't affect the update at all.  I think you can even use the package you're updating (e.g. play music using amarok while updating amarok)
> 
2. From what I understand, sudo gives a user the privilege to install anything in a PC? Does this make you root for a while? They say when logged-in as root, it brings chaos to your PC.Yes, sudo does give you temporary root privileges, and badly used, it can cause chaos.  Generally, only use sudo for commands that really need, and before doing so, make use you know what you're doing. E.g. "sudo rm -rf /" will wipe your entire hard drive - not something you want to do!  Basically, you can think of it as being there as a safety device.  Don't run commands with sudo if you can avoid it, and you should be safe.
> 3. Do I need an antivirus for Linux?Not unless you are using it as a server for windows pcs.  Linux doesn't havethe problems with viruses windows has. There is an antivirus for linux, but its aimed towards servers which route to windows.
> 4. How do I install printers and other USB-type devices?Depends on the device.  Most of the time they're plug-and-play.  Just plug them in and they should work.  If you have a problem with a specific device then search the forums and wikis for a howto, and if you don't find anything make a post of the problem.
> 5. I'm a C programmer, how do I run C in Ubuntu. I've heard that there's this GCC thing which runs, I tried running it in the terminal but didn't know what to do.Install the package "build-essential".  This will install gcc (amongst other things), which is a c compiler.  However, its just the compiler.  If you want an IDE (which you're probably used to in windows) try kdevelop.

Hope this helps!

---

### Post by poysama on 2007-09-10
I see. Thanks! Linux is really good. I mean GOOD! Hahaha, Fast Development.

Thanks for the help guys.

So if you say that gcc is only a compiler, does that mean I can't type my codes like in Borland C or Turbo C? (like windows?) You see, from what I've learned, when I hear the word compiler, I think of it as somewhere, something you can type your code and then compile/run your code.

And is it really normal when I run adept, I must login as root? so does this give way to chaos? as root?

---

### Post by eentonig on 2007-09-10
That's an IDE.

A compiler is just a program that takes your code and translate it, so that the computer will understand it.

You could write your code in a simple notepad (Gedit, vi, ... on linux). But that would be boring, wouldn't it. An IDE provides you with an interface to facilitate the code writting (autocompletion, intendation, etc...) and usually an interface to the compiler.

---

### Post by poysama on 2007-09-10
Thanks!

I am currently downloading kDevelop as suggested

:guitar:

---

### Post by Brightbelt on 2007-09-10
For my Epson RX580 all-in-one printer, I actually bought Linux drivers from Turboprint (see [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html) ) 

It was only $39 or so and it saved me a lot of frustration and time, plus it came with drivers for OnCD printing as well.

Just a thought in case you want to go that route. Good Luck,
Frank B.

---

### Post by BrendanM on 2007-09-10
Yes, you'll need to enter your password (sudo) with adept, because adept lets you install software. Basically anything that changes important files on your system is going to require a password. When people talk about the dangers of root, they're usually talking about actually logging in as the user "root" and using root for everything. Using sudo has the advantage that you only temporarily take root priviledges to do what you need to do, and then go back to being a regular user. It's safer that way, so I wouldn't worry too much about using sudo.

---

### Post by Benbow on 2007-09-10
Just a comment on printers. All printers rely on software supplied by the manufacturer which controls the output of the machine and most are written with windows in mind!. This may not be too important when printing text or spot colours but photographs are an entirely different matter. Turboprint is again fine for text but invariably falls down where photo reproduction is concerned. 
HP printers are apparently recommended for Linux although I have had no experience of this. My own current printer, a canon mp170, will only perform satisfactorily with windows and I am stuck with this until it is viable for me to replace the canon.
Having said this, I use Ubuntu Ultimate for all my work and only return to xp for my photographic work.

---

### Post by poysama on 2007-09-10
> **Benbow said:**
> Just a comment on printers. All printers rely on software supplied by the manufacturer which controls the output of the machine and most are written with windows in mind!. This may not be too important when printing text or spot colours but photographs are an entirely different matter. Turboprint is again fine for text but invariably falls down where photo reproduction is concerned. 
HP printers are apparently recommended for Linux although I have had no experience of this. My own current printer, a canon mp170, will only perform satisfactorily with windows and I am stuck with this until it is viable for me to replace the canon.
Having said this, I use Ubuntu Ultimate for all my work and only return to xp for my photographic work.

I see. Mine's an HP so I guess I will be having only little problems on it.
Thanks!

---

### Post by amazingtaters on 2007-09-10
HP has linux drivers, and most HP printers work flawlessly.

---

### Post by eentonig on 2007-09-10
If your printer is HP, you most likely wont have any problems at all.

---

### Post by skyjacker on 2007-09-10
> **Benbow said:**
> 
HP printers are apparently recommended for Linux although I have had no experience of this. I have an HP printer, and Ubuntu found it during install. It can do everything it could in windows.  :):)

---

### Post by AndyCooll on 2007-09-10
With hardware, over time you'll realise that some manufacturers are better than others when it comes to Linux support. And for those that don't provide any support at all it's then down to someone in the Linux community reverse engineering the relevent driver. Obviously this takes time and can mean a delay. 

That being said most hardware eventually works with Linux following one of the two above methods, it's just that the latest gadgets are often still waiting until someone can compile a driver for it.

:cool:

---

### Post by CaptainInsaneO on 2007-09-10
I too use Ubuntu Ultimate. It's really good for programmers/sound editors/image and video, etc. because it comes pre loaded (i.e. PACKED) with miscellaneous tools that you'd need for the above-mentioned. Saves a lot of time when you don't have to go and find all that stuff, you can just install the distro and get right to work!

---

### Post by Amazona aestiva on 2007-09-10
> **poysama said:**
> 1. When updating from package managers, is it ok to do something like watching media, playing sounds? Will it not affect the updating process?

I have been using Ubuntu for 7 month, and My experience is that nothing affect install, remove, reinstall or update processes.

Ubuntu is good!:)

---

### Post by daveshields on 2007-09-10
!

See my post [http://daveshields.wordpress.com/2006/10/17/on-steve-ogradys-post-where-to-innovate-let-others-make-the-call/]("http://daveshields.wordpress.com/2006/10/17/on-steve-ogradys-post-where-to-innovate-let-others-make-the-call/")

Look for the phrase "Victor Hugo almost set the world’s record for short letter writing." and read the part that follows.

---

