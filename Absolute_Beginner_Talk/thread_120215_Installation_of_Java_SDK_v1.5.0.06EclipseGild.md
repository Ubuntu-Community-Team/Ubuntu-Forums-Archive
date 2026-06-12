---
title: "Installation of Java SDK v1.5.0.06/Eclipse/Gild"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by dyst0pia on 2006-01-21
I am currently trying to install Eclipse/Gild, but am stuck on trying to install the Java SDK.  I will admit right now that I am a rank novice when it comes to Linux.  I am currently taking labs for a CSC course that involve using a Unix system, but that doesn't mean I have any idea what I am talking about.

Now that I have provided my disclaimer, I will describe my problem.

I have downloaded what I believe to be the correct Java SDK file, which is named:

jdk-1_5_0_06-linux-i586-rpm.bin

So, I open it up and it brings up the Terminal, displaying a user agreement.  I type in "yes" and then it extracts another file, named:

jdk-1_5_0_06-linux-i586.rpm

Now, what am I supposed to do with this file?  Ubuntu doesn't recognize it and can't open it, and my Java installation documentation says nothing about it.

Anybody know what I should be doing?  Should I try downloading the non self-extracting version of the SDK?  Thanks for any and all help!!

On a side note, I am very impressed with Ubuntu.  Mainly what I am impressed with is the amount of hardware it recognized.  My machine, the one I am typing this on, is a Sony Vaio VGN-S360 Laptop.  Needless to say, when I have tried other distributions of Linux I have often ended up with odd screen resolutions, non-functional centrino wireless, and no sound.  None of that happened with Ubuntu, it recognized all of my hardware.  Beautiful.  Thanks for a great distribution!

On another side note, where is a good place to look for more Ubuntu themes?  Is there a portion of the forum and I am just blind?  Thanks again for any help!!

---

### Post by amohanty on 2006-01-21
For sun java and eclipse [this is what I did]("http://ubuntuforums.org/showpost.php?p=529068&postcount=2")

HTH
AM

---

### Post by Luke771 on 2006-01-21
I know that's not a real answer, but anyway: I installed JRE and SDK (and another pile of stuff) by clicking one or two buttons using Automatix.
You install it by typing in the terminal:
> code:
wget [http://beerorkid.com/automatix/automatix-ubuntu_4.4-2_i386.deb](http://beerorkid.com/automatix/automatix-ubuntu_4.4-2_i386.deb)
sudo dpkg -i automatix-ubuntu_4.4-2_i386.deb
This will install Automatix, then all you have to do is click Automatix in te System Tools menu and you get a long "grocery list" of programs, including SDK and JRE choose the ones you want by checking the checkboxes, click OK and they will up, working and ready to go in a couple of minutes.
(Yeah, OK, that's kinda cheating, but what the he££..."

---

### Post by Heretic Monkey on 2006-01-21
If you're looking on how to install RPM files, a very useful resource is the **TuXfiles.com** site.  Specifically, for your problem, see: 

[RPM software]("http://www.tuxfiles.org/linuxhelp/rpminstall.html")

[QUOTE=Tuxfiles]
< Installing and upgrading RPM packages >

For installing a software package, you use the rpm command with -i option (which stands for "install"). For example, to install an RPM package called software-2.3.4.rpm:

# rpm -i software-2.3.4.rpm

If you already have some version installed on your system and want to upgrade it to the new version, you use -U option instead (which stands for "upgrade"). For example, if you have software-2.3.3.rpm installed and want to upgrade it:

# rpm -U software-2.3.4.rpm

If all goes well, the files in your package will get installed into your system and you can happily run your new program. But where is your new program? Note that rpm doesn't usually create a special directory for the software package's files. Instead, the different files from the package get placed into appropriate existing directories on your Linux system. Executable programs go usually into /bin, /usr/bin, /usr/X11/bin, or /usr/X11R6/bin after installing with rpm.

But how can you run your new program if you don't know where the executable is? Sometimes the program gets automatically added into your menu, but usually you can just run the program by typing its name at the command prompt. In most cases you don't have to know where the program was installed because you don't have to type the whole path when running the program, only the program's name is needed.[/quote]

However, i do believe **Automatix** is a much easier way of doing things.  However, if you're like me, you'd rather get the full linux experience and do things the way they were meant to be done........ i'm sticking with **Automatix** until i get a firm grasp on the linux system and command line grammar.

BTW: I'm also taking CSC 116 (introduction to java).  Good luck!

---

