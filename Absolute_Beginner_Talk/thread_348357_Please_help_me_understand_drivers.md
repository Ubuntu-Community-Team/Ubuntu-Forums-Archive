---
title: "Please help me understand drivers"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Curt101010 on 2007-01-28
I'm really not understanding how driver installation works in Linux.  In Windows it's easy, there's one of two ways: 1) There's an executable that does everything for you; or 2) You run Hardware Installation Wizard and point it at the folder where you put the drivers.

I think my machine might be faster if I upgraded some drivers, but whenever I see anything about editing OS files or re-compiling the kernel I break out in hives.  Plus, it doesn't help that most instructions are written for people who have a strong knowledge of how to do what it is that they need to do.  (At the opposite end of the spectrum, most directions written for any Windows software read like a "Dick and Jane for People with Head Trauma" book.)  It doesn't help that every distro has it's own terminology and software with which to do the exact same thing.

I've been an IT professional for 7 years now, so I understand how a computer works, what I'm having problems with is how Linux uses the hardware and interacts with itself.

Could someone recommend a good website or book that can run me though it at a beginner's level?  I don't mind laying out a few bucks for a good book on the subject, as long as it's reasonable.  The last time I tried to use Linux (don't remember the distro, one of the "big" ones) I was having problems trying to do something that should have been very easy and all the "help" boards would tell me was to go out and buy these books (total > $250).  I responded that for that price I would just go out and buy a copy of Windows that would do what I wanted very easily.  So I did.

I really like Ubuntu and this forum is 1000% better than anything I've ever experienced before.  I just need some basic training on how Linux works with itself and hardware.  Is there a Linux equivalent to .DLL files?  How about the registry?  Why would I ever need to compile the kernel?  How can I make sure all my drivers are up to date?  These are the types of questions that haunt my dreams....  :D 

Thanks for all you guy's help.  This really is a great site and I'm enjoying Ubuntu.

---

### Post by BarfBag on 2007-01-28
> **Curt101010 said:**
> I'm really not understanding how driver installation works in Linux.  In Windows it's easy, there's one of two ways: 1) There's an executable that does everything for you; or 2) You run Hardware Installation Wizard and point it at the folder where you put the drivers.

I think my machine might be faster if I upgraded some drivers, but whenever I see anything about editing OS files or re-compiling the kernel I break out in hives.  Plus, it doesn't help that most instructions are written for people who have a strong knowledge of how to do what it is that they need to do.  (At the opposite end of the spectrum, most directions written for any Windows software read like a "Dick and Jane for People with Head Trauma" book.)  It doesn't help that every distro has it's own terminology and software with which to do the exact same thing.

I've been an IT professional for 7 years now, so I understand how a computer works, what I'm having problems with is how Linux uses the hardware and interacts with itself.

Could someone recommend a good website or book that can run me though it at a beginner's level?  I don't mind laying out a few bucks for a good book on the subject, as long as it's reasonable.  The last time I tried to use Linux (don't remember the distro, one of the "big" ones) I was having problems trying to do something that should have been very easy and all the "help" boards would tell me was to go out and buy these books (total > $250).  I responded that for that price I would just go out and buy a copy of Windows that would do what I wanted very easily.  So I did.

I really like Ubuntu and this forum is 1000% better than anything I've ever experienced before.  I just need some basic training on how Linux works with itself and hardware.  Is there a Linux equivalent to .DLL files?  How about the registry?  Why would I ever need to compile the kernel?  How can I make sure all my drivers are up to date?  These are the types of questions that haunt my dreams....  :D 

Thanks for all you guy's help.  This really is a great site and I'm enjoying Ubuntu.

Welcome to the world of free software!  I can't answer all of your questions, but I can tell you this - I'm only 16 and by no means am I an IT professional.  I have a pretty decent understanding of Linux, though.  If I can do it, surely you can.

What drivers do you want to upgrade?  If you give some specifics, we can help you out.

I believe the Linux equivalent to a .DLL is a lib.  Not 100% positive on that one, though.

Linux doesn't have a registry.

You can make sure all of your drivers are up to date by adding a repository (server containing them) to your sources (config file that stores the repos).  The system will automatically keep track of them.

---

### Post by livingtarget on 2007-01-28
Right, I imagine that most performance issues come from not having 3D acceleration drivers enabled. This is not a simple thing to change, but there are several helper scripts out there. Installing the drivers is one thing, but actually switching the Xorg configuration is a bit more difficult. Xorg = The X Window System, think of it as the base graphical user interface.

Most drivers/libraries go by either *.o/*.so/*.ko you often need to compile drivers or get pre-compiled drivers from somewhere. It's quite rare to find pre-compiled drivers.

*.deb files are Debian installer files, these can be installed and are especially used for Debian & Ubuntu.

Anyhow there are some books about ubuntu, but I don't really know how good they are and if they would go into things like kernel recompiling. For more information about the official ubuntu book including a couple of examples: [https://help.ubuntu.com/6.10/book/book-toc.html](https://help.ubuntu.com/6.10/book/book-toc.html)

---

### Post by tcrroadie on 2007-01-28
I'm not a Linux kernel expert but from what I understand is that most hardware drivers you will ever need are included (**built into **) the kernel.  Typically, you will never need to recompile the kernel.  The typical reason for recompiling a kernel is to include driver support for a piece of hardware in your machine that is not working.  In most cases if a piece of hardware is not working after the default install such as a sound card or network card, you can just load the drive for said hardware into the kernel with the command *modprobe*.

As far as your machine running a little slow, could you please give the system specifications of the machine you are using.  A vanilla install of Ubuntu using the Gnome desktop really needs a machine with 512mb or ram or more.  There are alternative desktop environments such as Fluxbox and Enlightenment which can drastically improve the performace of a machine with low amounts of ram and a low spec CPU such as a 500mhz PII.  

In response to the Windows registry question, nearly all system configuration files with the exception of Users configuration files will be stored in the /etc dirctory.  User specific configuration files will be stored in the users home director and begin with a . before the file name or directory, for example /home/username/.xinitrc

Comming from Microsoft Windows to a Linux machine is a bit confusing at first, but once you get the hang of using and administering a Linux system you will appreciate the design of a Linux (Unix) operating system and find that it is much easier to make Linux do what ever you want, and fix anything.  

Some recommended reading.  

Moving to Ubuntu Linux

[http://www.amazon.com/Moving-Ubuntu-Linux-Marcel-Gagn%C3%A9/dp/032142722X/sr=1-8/qid=1170027564/ref=sr_1_8/102-2405495-3013759?ie=UTF8&s=books](http://www.amazon.com/Moving-Ubuntu-Linux-Marcel-Gagn%C3%A9/dp/032142722X/sr=1-8/qid=1170027564/ref=sr_1_8/102-2405495-3013759?ie=UTF8&s=books)

Unix (Visual Quickstart Guide).  **A must have. **  

[http://www.amazon.com/UNIX-Third-Visual-QuickStart-Guide/dp/0321442458/sr=8-17/qid=1170027442/ref=sr_1_17/102-2405495-3013759?ie=UTF8&s=books](http://www.amazon.com/UNIX-Third-Visual-QuickStart-Guide/dp/0321442458/sr=8-17/qid=1170027442/ref=sr_1_17/102-2405495-3013759?ie=UTF8&s=books)

Linux Bible.  

[http://www.amazon.com/LinuxBible-Fedora-KNOPPIX-Debian-Distributions/dp/0471754897/sr=1-1/qid=1170027508/ref=sr_1_1/102-2405495-3013759?ie=UTF8&s=books](http://www.amazon.com/LinuxBible-Fedora-KNOPPIX-Debian-Distributions/dp/0471754897/sr=1-1/qid=1170027508/ref=sr_1_1/102-2405495-3013759?ie=UTF8&s=books)

---

### Post by tcrroadie on 2007-01-28
I almost forgot one of the most important online sources for Ubuntu.  

The Ubuntu Guide.

[http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)

Explains for example how to install additional applications and basic system administration.

---

### Post by Curt101010 on 2007-01-28
Thanks to everyone for their input! 

BarfBag - I'm concerned about the drivers for my MB.  I have a N-Force 3 chipset and would like to make sure I have all the correct drivers.  For XP I can go and download the drivers from NVidia's website to make sure the drivers aren't some generic junk that works, but doesn't function like it should.  My install of XP on this machine runs laser quick, but Ubuntu (while fast) isn't near that fast.  Also, could I have loaded some TSRs that are slowing things down?  I know how to check for that in Windows, but am totally clueless in Linux.  I don't use this machine for gaming, but don't like my hardware to go to waste either.

LivingTarget - I am running an NVidia 6600 graphics card.  I had to install special drivers (don't ask me what or how... I found the instructions on a website for the alternative drivers and used that.  Since then, I have slept and all the knowledge ran out my ear onto the pillow.) to get that to work well.  Now, is it working to it's full capacity??  Is the 3D acceleration enabled??  I have no clue.  Windows drivers would have a piece of software that I could look at and it would tell me.  Also, I could stick a high powered game on and be able to tell how well the drivers were working.  Unfortunately, there's not many high-powered games for Linux.  Plus, as I said above, I'm not using this as a gaming box.  I just want to learn about Linux and get this working as well as it can.  

Also, the term "compiling" gives me a rash.  I don't understand why I, an end user, need to compile the software.  Shouldn't the programmer do that in order to make sure the software works??  I understand that this is open source, but I don't want to be a super-guru and reprogram and tweak stuff.  I just want good solid software that does what I need.  Honestly, Linux will never make much headway into MS' domain without making things as easy as possible on the end user.  Ubuntu is a great start.  Very easy to install and use straight out of the box.  (Easier, in fact, than XP)  But until programmers realize that MS' main power base is it's ease of use and compatibility, most people will never even try Linux.  I have a USB headphone set that was released this past year.  I plugged it into XP and it just worked.  No driver install, no configuration, nothing.  It just worked.  I plugged the same thing into this Ubuntu box and nothing happened.  I went searching for some kind of driver for it and found less than nothing.  Apparently, I am the only person in the entire world who bought USB headphones and wants to use them with Linux.

Ok, sorry.  Went off a bit there.  [/rant off]

tcrroady - Thanks for the links.  I will defiantly get one or more of these books.

I am running:
AMD Opteron 3400+
1 GB RAM
BioStar NF325A7 - NVidia nForce3 250 MB
200GB Maxtor HD
PNY Verto GeForce 6600 256MB Graphics card

While not a bleeding-edge screamer, not a old hunk-o-junk either. I didn't figure the hardware would be so new, old or odd as to have a problem getting the drivers for it.  Perhaps I should have put the 64bit version of Ubuntu on.  But XP isn't 64 bit compatible, so I didn't figure there should be much difference.

Thanks again, guys.  All great information!!

---

### Post by old_geekster on 2007-01-28
You might also want to download the "Official Ubuntu Book".  It is a good source of help.

I believe that you can download it for free on this site.

---

### Post by igknighted on 2007-01-28
The version of the linux kernel shipped with Ubuntu comes to you precompiled.  In this kernel they try to add support for any common hardware out there.  However, if you have something really old, really new, or from a vendor with poor support (such that any drivers are probably experimental and/or possibly unstable) the kernel might not support it.  In this case you can download the source of the kernel and the new driver and recompile the kernel with that support.  Also, NVIDIA drivers need the kernel source code because they have to compile a kernel module built specifically for your system.  Most users will never have to compile anything, its only a feature that allows linux to be more adaptable, so if you do push the envelope it can adapt.

---

### Post by reacocard on 2007-01-28
> **Curt101010 said:**
> ...Now, is it working to it's full capacity??  Is the 3D acceleration enabled?? ...

to find out whether 3d accel is enabled, open a terminal and enter this command: 
```
glxinfo | grep direct
```
if it returns
```
direct rendering: Yes
```
then you have 3d accel.

> ...Also, the term "compiling" gives me a rash.  I don't understand why I, an end user, need to compile the software.  Shouldn't the programmer do that in order to make sure the software works??  I understand that this is open source, but I don't want to be a super-guru and reprogram and tweak stuff. ... 
The reason most Linux programs are distributed as source code is because it is virtually impossible to create binaries that will work on every Linux system, since there are so many different kinds.  This is why we have package managers like apt that give easy access to binaries compiled specifically for whatever distro you're using. Also, compiling isn't that hard under linux (usually). Most source tarballs are in a standard format, so all you have to do is extract them and run 3 short commands in a terminal (./configure, make, make install). When I first came to Linux, I felt as you did, but I have since become comfortable with compiling my own software. 

> I just want good solid software that does what I need.  Honestly, Linux will never make much headway into MS' domain without making things as easy as possible on the end user.  Ubuntu is a great start.  Very easy to install and use straight out of the box.  (Easier, in fact, than XP)  But until programmers realize that MS' main power base is it's ease of use and compatibility, most people will never even try Linux.  I have a USB headphone set that was released this past year.  I plugged it into XP and it just worked.  No driver install, no configuration, nothing.  It just worked.  I plugged the same thing into this Ubuntu box and nothing happened.  I went searching for some kind of driver for it and found less than nothing.  Apparently, I am the only person in the entire world who bought USB headphones and wants to use them with Linux.

The reason MS has such compatibility is because it has >90% of the market, so everyone develops drivers for it. Very few companies make drivers for Linux, so pretty much all Linux drivers are reverse-engineered from the windows ones. Considering that we have to do this, it's amazing just how much hardware *is* supported.  More niche devices like your USB headphones may not have drivers, but most major and many not-so-major hardware works.  Popular support is a major obstacle for Linux adoption, but it's not likely to be resolved soon. In order to get 3rd party support, we have to have enough of the market to make it profitable, and to get the market we need 3rd party support.

---

### Post by tcrroadie on 2007-01-29
If you successfully installed the Nvidia video driver you will see a Nvidia splash screen just before the log in screen comes up.  If you never see a Nvidia splash screen when your system is booting into your graphical working environment it is not installed properly.

What resource did you use to install the Nvidia driver?  

One small piece of software I would highly recommend that you install is an application called Automatix.  Automatix will allow you to easily install any third party piece of software such as applications and drivers such as the Nvidia graphics driver.  You can also use Automatix to install proprietary media codecs. You can find install instructions for Automatix on the Ubuntu Guide. 

[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu")

If you have installed the i386 addition of Ubuntu on your system and everything is working I would recommend sticking with it instead of the Ubuntu 64 bit install.  There is more application support on 386 than 64bit such as Shockwave Flash support.  

Also keep in mind that Microsoft Windows and Linux are completely different architectures.   Not all applications that run on Linux will be as fast and snappy as a similar application on Windows.  What really affects the speed of an application is the efficiency in its code.  Take the Amarok media player for example.  I can remember using Amarok over 2 years ago when it was very young and it ran very slow.  Today Amarok is very fast and efficient.  Same applies to the Gnome desktop.  2.14 was much slower than 2.16.  As software matures and growes it becomes more efficient and faster.

Another great resource for new Linux users is a podcast called Linux Reality.  I have been listening to Chess's show for almost a year and he does a really great job of introducing new users to Linux and explaining how to administer a Linux system and use applications. 

You can find Linux Reality here.  **Highly recommended listening.**

[http://www.linuxreality.com/]("http://www.linuxreality.com/")

:D

---

### Post by Curt101010 on 2007-01-30
Thanks to everyone for all their wonderful suggestions, thoughts and information.  I just subscribed to Linux Reality.com.  About to start listening to one of the pod casts now.

---

