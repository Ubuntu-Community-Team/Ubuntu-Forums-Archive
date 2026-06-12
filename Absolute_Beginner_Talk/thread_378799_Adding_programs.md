---
title: "Adding programs"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by jrandolph on 2007-03-07
I am wondering how I would go about adding programs to Ubuntu
The one i am trying to add is a Unix based inventory control software
Does anyone have an idea how I can do this?

I have a disk for the software but i dont know how to get it to install

---

### Post by diskotek on 2007-03-07
i couldn't offer you an advance solution but you should use "synaptic package manager". you can find it on menu and use it with your root software. there is also another choice like "add/remove program" in other section.

you can search and install softwares via these application. synaptic package manager is advanced and you can search whole repository for ubuntu. i think this information will be usefull (i believe that if you search the forum there would be more advance & profesional answers). 

[i think this works on ubuntu/xubuntu, don't know about kubuntu).

---

### Post by Kateikyoushi on 2007-03-07
In case you can't find it in the ubuntu repositories check the disc for installation instructions.

---

### Post by jrandolph on 2007-03-07
well i searched for the file with the synaptic package manager it found the one on my desktop that i had taken off the cd and i installed it but then nothing -- what do i do now?

---

### Post by jrandolph on 2007-03-08
I cannot seem to figure out how to install this program -- I have the disk and it is just a simple program can anyone help me to get this up and running

---

### Post by gigaferz on 2007-03-08
I think you need to provide more information.

Look in the cd and post what is in there

There could be a script  to install it.

besides, when you install something, most of the times you have to go to that directory, and run it like for example

./actioncube.sh

./ioquake3.xxx

Honestly that is all that I know, I still do not know where to install things I just  unzip them and put them in opt. 

remember to use sudo before any command.

---

### Post by Marsolin on 2007-03-08
What is the name of the program?

Since you can find it in Synaptic, select it and look at the properties. There is a tab for installed files. I'm guessing that it may not have come with a menu entry so you will need to look for the name of the file that was installed in the bin directory and execute it from the terminal or the run dialog.

---

### Post by jrandolph on 2007-03-08
This is what the installed files tab says
to me it doesn't mean alot
but maybe u can decipher it for me
/.
/usr
/usr/lib
/usr/lib/tn5250
/usr/lib/tn5250/lib5250.so.0.0.0
/usr/bin
/usr/bin/scs2ascii
/usr/bin/scs2pdf
/usr/bin/scs2ps
/usr/bin/tn5250
/usr/bin/lp5250d
/usr/bin/xt5250
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/scs2pdf.1.gz
/usr/share/man/man1/scs2ps.1.gz
/usr/share/man/man1/lp5250d.1.gz
/usr/share/man/man1/scs2ascii.1.gz
/usr/share/man/man1/tn5250.1.gz
/usr/share/man/man5
/usr/share/man/man5/tn5250rc.5.gz
/usr/share/terminfo
/usr/share/terminfo/5
/usr/share/terminfo/5/5250
/usr/share/terminfo/l
/usr/share/tn5250
/usr/share/tn5250/dialogrc
/usr/share/tn5250/XTerm
/usr/share/tn5250/uk5250.map
/usr/share/tn5250/us5250.map
/usr/share/doc
/usr/share/doc/tn5250
/usr/share/doc/tn5250/README
/usr/share/doc/tn5250/TODO
/usr/share/doc/tn5250/BUGS
/usr/share/doc/tn5250/AUTHORS
/usr/share/doc/tn5250/changelog.gz
/usr/share/doc/tn5250/README.Debian
/usr/share/doc/tn5250/copyright
/usr/share/doc/tn5250/NEWS.gz
/usr/share/doc/tn5250/README.ssl.gz
/usr/share/doc/tn5250/changelog.Debian.gz
/usr/share/menu
/usr/share/menu/tn5250
/usr/share/pixmaps
/usr/share/pixmaps/tn5250-48x48.png
/usr/share/pixmaps/tn5250-62x48.png
/usr/share/pixmaps/tn5250-32x32.xpm
/usr/lib/tn5250/lib5250.so.0
/usr/share/man/man1/xt5250.1.gz
/usr/share/terminfo/l/linux-5250

---

### Post by Zuuswa on 2007-03-08
/usr/share/doc/tn5250/README.Debian

try looking in this file.  Maybe you will find some pertinent info there?

---

### Post by jrandolph on 2007-03-08
I am sorry for all these dumb questions -- but how do I go about looking into that file
where do I pull it up at?

---

### Post by Marsolin on 2007-03-08
I don't think that is the program you think it is.  You are looking at [tn5250]("http://tn5250.sourceforge.net/") which is a telet emulator, not an inventory control program.

I'm not sure if they are the type of inventory that you are interested in, but you could look at [OCS Inventory NG]("http://linuxappfinder.com/package/ocsinventory") or [SysAid]("http://linuxappfinder.com/package/sysaid") if it's IT related.

If you can tell us the name of the program you have on the CD it might be easier to help.

---

### Post by hanexar on 2007-03-08
I know you really want to install the program on your cd, but I suggest you first read the link in my signature about installing anything on ubuntu. It may save you lots and lots of trouble.

---

### Post by jrandolph on 2007-03-09
I just noted that it was an inventory control software because I did not think anyone wanted me to go into long detail about it but ur are exactly right it is a telnet emulator and I use it for a sales & inventory program I have installed on my server I have the disk for it I and I think I have it installed I think I just need to know how to run it

---

### Post by Marsolin on 2007-03-09
> **jrandolph said:**
> I just noted that it was an inventory control software because I did not think anyone wanted me to go into long detail about it but ur are exactly right it is a telnet emulator and I use it for a sales & inventory program I have installed on my server I have the disk for it I and I think I have it installed I think I just need to know how to run it

In that case tn5250 is the executable that you want. Type "man tn5250" in the terminal for usage instructions.

You also notice the following file in the list: /usr/share/menu/tn5250. It is a text file that would add a menu entry to the old style Debian menu. You can look in it for the simple command to run the program as well.

---

### Post by jrandolph on 2007-03-09
> **Marsolin said:**
> In that case tn5250 is the executable that you want. Type "man tn5250" in the terminal for usage instructions.

You also notice the following file in the list: /usr/share/menu/tn5250. It is a text file that would add a menu entry to the old style Debian menu. You can look in it for the simple command to run the program as well.

This is what that file says --

?package(tn5250): \
	command="/usr/bin/xt5250" \
	needs="X11" \
	icon="/usr/share/pixmaps/tn5250-32x32.xpm" \
	section="Apps/Net" \
	hints="Terminal" \
	title="Xt5250" \
	longtitle="5250 Terminal Emulator"


I suppose I dont know what to do to make this work

---

### Post by Marsolin on 2007-03-09
I see now.  tn5250 is the command line version of the program and xtn5250 is the graphical version.  To run it press Alt+F2 to bring up the run dialog and then type in xtn5250 followed by enter.  That should do it.

---

### Post by jrandolph on 2007-03-09
> **Marsolin said:**
> I see now.  tn5250 is the command line version of the program and xtn5250 is the graphical version.  To run it press Alt+F2 to bring up the run dialog and then type in xtn5250 followed by enter.  That should do it.

When I do this it says

Could not open location 'file:///xtn5250'
The location or file could not be found

---

### Post by jrandolph on 2007-03-09
I have tried to run this app by <Alt>F2 and typing xtn5250 and tn5250
neither one works and I am so lost right now

:confused:

---

### Post by Marsolin on 2007-03-09
I'm running out of ideas.  My last suggestion would be to try running it from the terminal in case an error message is being generated that Alt+F2 doesn't report.

---

### Post by jrandolph on 2007-03-12
I have downloaded a different version of this program that is designed for Linux and now I wonder if anyone can help me to install and run this version since I had no success with the other version

---

### Post by jrandolph on 2007-03-12
Is there anyone who has any experience with TN5250 or any type of telnet emulator

---

### Post by jrandolph on 2007-09-12
I am revisiting this install -- trying it over 
can anyone help with this?

---

### Post by jrandolph on 2007-09-13
Bump

---

