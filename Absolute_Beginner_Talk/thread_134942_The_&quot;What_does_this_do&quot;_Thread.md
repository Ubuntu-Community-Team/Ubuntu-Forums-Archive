---
title: "The &quot;What does this do?&quot; Thread"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by schenkin on 2006-02-22
Well I have been putzing around with linux in a none-too-serious way. A week ago I finally buckled down and installed ubuntu. It wasn't very difficult, except for installing the new ATI drivers. Now I am faced with some basic questions about how Linux works. I hope some other newbie will ask a question or two.

1. What are all these built in directories? /usr /tmp /home /bin, etc. What do they do?

2. When I install an application via Synaptic / Adept what is really happening?

3. What is the difference between a binary installation (and what is a .deb file anyway) and any other kind of installation.

4. What is the kernel? Why would I build one from scratch?

Anyway I'm sure I will think of more, but I just figure these are imporant things to know. If anyone knows of a simple online resources that deals with these topics please pass it on!

---

### Post by evilc on 2006-02-22
Here's a link that may help you  [http://ubuntuguide.org/](http://ubuntuguide.org/)  I have a small 506k pdf file that is very good but I forgot where I got it from, if you like I can email to you.

Clive

---

### Post by schenkin on 2006-02-22
neat, thanks! 

My address is: schenkin {at} gmail

---

### Post by direwolf on 2006-02-22
I'll try the first and last ones. 

*"1. What are all these built in directories? /usr /tmp /home /bin, etc. What do they do?"*

/bin holds the essential binaries (i.e. programs) - things like "cat", "chmod", "echo", "mkdir", "rm", etc. 

/home contains user home directories - a place for a users data and their user specific config files. 

/tmp contains temporary files

/usr contains shared and read only data - icons, programs for "all users", etc. 

for the rest (and more in-depth) go here: 
[http://www.secguru.com/files/linux_file_structure.jpg](http://www.secguru.com/files/linux_file_structure.jpg)

*"4. What is the kernel? Why would I build one from scratch?"*
The kernel is the fundamental part of the OS. In many ways it IS the OS. It is the thing that does all the work. It is the channel through which software communicates with the hardware. You might build one from scratch for many reasons - including but not limited to - security, performance, testing new features and customizing your system to fit your needs in general. 

for the rest (and more in-depth) go here: 
[http://en.wikipedia.org/wiki/Kernel_(computer_science](http://en.wikipedia.org/wiki/Kernel_(computer_science))

---

### Post by alfonz on 2006-02-22
great chart direwolf, many thanks

Cheers!

---

### Post by az on 2006-02-22
[QUOTE=schenkin]
2. When I install an application via Synaptic / Adept what is really happening?[/QUOTE]

Packages are source code written by upstream developers (the ones who write the individual apps themselves, and not in the context of the whole operating system) which is configured and compiled into one file.  The package manager takes this file, unpacks it (puts each file into the right place) and then runs configuration scripts (preinstall and postinstall).  When you remove a package, the opposite happens (preremoval script, deletion of files and the postremoval script)

There are many many rules to follow to package an application as a debian package.  It is a high standard to keep.


[QUOTE=schenkin]
3. What is the difference between a binary installation (and what is a .deb file anyway) and any other kind of installation.[/QUOTE]

The way the OS is developed is through the source code.  Users do not need to compile everything by hand (although they can if they wish to).  Precompiled binary packages are the applications in executable form.


[QUOTE=schenkin]4. What is the kernel? Why would I build one from scratch?[/QUOTE]

The kernel runs your computer.  It abstracts the hardware from the program running on it.  A program written to compile and run using the unix toolchain should compile and run on linux, BSD, Solaris or any other unix environment (there are always porting issues, but the point is a unix environment is a unix environment.  Linux is a unix environment.)

---

### Post by ubuntu27 on 2006-02-22
[QUOTE=evilc]Here's a link that may help you  [http://ubuntuguide.org/](http://ubuntuguide.org/)  I have a small 506k pdf file that is very good but I forgot where I got it from, if you like I can email to you.

Clive[/QUOTE]


ANd this [http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)   is the almost OFFICIAL one ;) 


[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

---

### Post by KingBahamut on 2006-02-23
ubuntu27, 

We try our best. 

The UDSF Team.

---

### Post by K-9 on 2006-02-23
Great answers guys! I mean it and great JPEG.  as a total neophyte I know squat about linux and Kubuntu and command line stuff. this new linux experience which will officially start next week when I get my new laptop with kubuntu is absolutely scaring the hell out of me!If everyone could answer questions as diligently as these people have I would have felt like I just wasted $ on this new laptop and also just jumped of the cliff!

thanks - 

K-9

---

### Post by schenkin on 2006-02-23
Thanks for the quick answers! The links in particular are helpful. Now I have another question.

My computer is a 64bit AMD Machine. I downloaded and installed the i686 version of Kubuntu. Now as I understand it all of the packages found in my package manager (i'm using synaptic) are already compiled for this architecture. I also understand that I can manually compile (a nightmare, but doable) many applications for my architecture.

Now, I have been trying to get WINE to work, but do I want to compile it for my architecture? Will I be able to run i386 windows programs? I ran accross a reference somewhere to "chroot," which seems to be a way to install a second set of apps and libraries on this system. Is this a better way to do things? How does it work?

---

### Post by ubuntu27 on 2006-02-23
[QUOTE=KingBahamut]ubuntu27, 

We try our best. 

The UDSF Team.[/QUOTE]


I know you guys are trying your best :) 

And I must say that you and your team are doing a great job.


Don't stress yourself :)

and ganbatte

---

