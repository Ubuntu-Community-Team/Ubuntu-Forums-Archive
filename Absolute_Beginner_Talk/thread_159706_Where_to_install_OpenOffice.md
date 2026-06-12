---
title: "Where to install OpenOffice"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-04-13
I downloaded, via Azureus, the OpenOffice Suite. 134 meg. I have the .tar.gz file in /home.

Where do I move it to in order for Ubuntu to find it? That is, is the package smart? Will it install itself in the proper folders from /home?

And can I then remove the 134 meg of packed files, i.e., delete it?

I tried using Automatix to download OpenOffice, but when it completed the program(s) always returned:

Cannot launch entry

Details: Failed to execute child process "/usr/bin/oowriter" (No such file or directory)

which I have asked about in an earlier post.

---

### Post by NeghVar on 2006-04-13
[http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)

Scroll down to where it talks about compiling.

Yes it will auto install to where it should just follow thoise instructions

---

### Post by mostwanted on 2006-04-13
I thought OpenOffice came standard with Ubuntu? :-k Otherwise, if you've removed it by accident, you can install it in Synaptic or by using the command:

```
sudo apt-get install openoffice.org2
```

I don't think installing it from a tar.gz is very advisable. And certainly not if it's a source file... which I highly doubt, though; OOo is a very big and complex program, not your everyday compile.

---

### Post by MartinG on 2006-04-13
If you're using Breezy the version in the repos is not 2.0.2, but a flawed earlier build, which I (and others) have abandoned.  However, I agree that compiling from source is not a good idea for this very complex program (If that's what you have, which may well be so from the size of the download).  Try the appropriate .deb.tar.gz from
[ftp://ftp.linux.cz/pub/localization/OpenOffice.org/2.0.2](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/2.0.2)

Unpack it in its own directory, delete any unwanted files, open a terminal there, and type ```
sudo dpkg -i *.deb
```

As to the original problem, this might have been quickly solved by checking in /usr/bin for the correct executable (a script, probably), and amending the menu entry to point to it.

---

### Post by Mark_in_Hollywood on 2006-04-13
OOo_2.0.2_LinuxIntel_install_wJRE.tar.gz (132.2 MB tar archive . . .)

is the name of the file in /home.

It was downloaded from OpenOffice via there BitTorent page. As they make no mention of compiling, etc. I thought I needed to move it into the "right" directory and open/run it with a right click on the mouse. This is the first I've heard about having to compile, dpkg., etc.,  I just want to make sure I'm on the same page as you all.

Answer: I thought OpenOffice came standard with Ubuntu?

Newbie response: yes it came with this Ubuntu, and it was "updated" with Automatix, after which I started getting the Failure to Launch error message. So, after waiting for a few days in another post about this  Launch Failure, etc., I thought to obtain the latest version from OpenOffice.org.

MOSTLY 
From the 3rd answerer: 

"As to the original problem, this might have been quickly solved by checking in /usr/bin for the correct executable (a script, probably), and amending the menu entry to point to it."

NewbieMe: and how to go about that? This is (almost) Breezy 5.10. Ubuntu was installed here with the Hoary CD-ROM. It was then updated. Then upgraded. Now Breezy itself needs updating with ~ 145 meg. I have a 56K modem. It's a very slow process. Last time, it took 7 days x 12 hours per.

---

### Post by MartinG on 2006-04-14
> **Mark_in_Hollywood]OOo_2.0.2_LinuxIntel_install_wJRE.tar.gz (132.2 MB tar archive . . .)

is the name of the file in /home.

It was downloaded from OpenOffice via there BitTorent page. As they make no mention of compiling, etc. I thought I needed to move it into the "right" directory and open/run it with a right click on the mouse. This is the first I've heard about having to compile, dpkg., etc.,  I just want to make sure I'm on the same page as you all.[/quote]Right.  First, sorry if my earlier reply assumed you knew too much:-? 

What you have downloaded, when unpacked, should be a directory full of rpm files, which is how OOo is distributed from the main site.  It doesn't matter where you unpack it said:**
> From the 3rd answerer: 

"As to the original problem, this might have been quickly solved by checking in /usr/bin for the correct executable (a script, probably), and amending the menu entry to point to it."

NewbieMe: and how to go about that? This is (almost) Breezy 5.10. Ubuntu was installed here with the Hoary CD-ROM. It was then updated. Then upgraded. Now Breezy itself needs updating with ~ 145 meg. I have a 56K modem. It's a very slow process. Last time, it took 7 days x 12 hours per.This is now an academic point as you're embarked on a different way of doing it, but if you open /usr/bin in a file manager and search for files with names beginning variously openoffice, ooffice, soffice, oowriter etc., one of these will launch the program (check by entering the command in a terminal, e.g. soffice). Once you have established which one, you can use the menu editor (kmenuedit in Kubuntu, I don't know in Ubuntu) to check the entry which gives an error, and replace the command it issues with the command you have just tested.

---

### Post by tubunu on 2006-04-14
I have the same problem with OpenOffice.org 2, I performed all the steps, Ooo got installed in /opt/openoffice.org2.0/program, but I can't run it. When I click on "swriter" there's nothing happening, (there aren't any menus for running Ooo2, btw) and when I try "soffice" it's got a small red cross icon in the upper right hand corner of the bigger icon and says it can't display soffice. 

The original file I installed it off was called "OOo_2.0.2_LinuxIntel_install.tar.gz". I unpacked it, converted RPM files to .deb with *sudo alien *.rpm*, and then entered *sudo dpkg -i *.deb*. 

Could anyone point as to what has gone wrong?

---

### Post by tubunu on 2006-04-14
I would also like to point out that I've just installed 
**openoffice.org-debian-menus_2.0.2-3_all.deb**
and now I can see the OOo2 menus in Applications/Office, but when I click on any nothing happens. :(

---

### Post by MartinG on 2006-04-14
[QUOTE=tubunu]I have the same problem with OpenOffice.org 2, I performed all the steps, Ooo got installed in /opt/openoffice.org2.0/program, but I can't run it. When I click on "swriter" there's nothing happening, (there aren't any menus for running Ooo2, btw) and when I try "soffice" it's got a small red cross icon in the upper right hand corner of the bigger icon and says it can't display soffice. 

The original file I installed it off was called "OOo_2.0.2_LinuxIntel_install.tar.gz". I unpacked it, converted RPM files to .deb with *sudo alien *.rpm*, and then entered *sudo dpkg -i *.deb*. 

Could anyone point as to what has gone wrong?[/QUOTE]Sounds like you've done everything right, actually, so I'm a bit baffled.  However, can you open  /opt/openoffice.org2.0/program and check the permissions on soffice and swriter there (right click in the file manager, and the permissions tab), to make sure they are executable.  If they are, open a terminal there and enter ./soffice or ./swriter as a command.  If that doesn't launch it there should at least be some output which might give us a clue.

As I said in an earlier post, I've used the semi-official deb files from [ftp://ftp.linux.cz/pub/localization/OpenOffice.org/2.0.2](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/2.0.2) -- sometimes alien doesn't get it right.  And a final thought -- what version of Java have you got?  OOo shouldn't need it, but programs are funny things.

---

### Post by steve.horsley on 2006-04-14
I installed OOo from their RPMs, and had the same problem launching it. I used this littel script that I called **/usr/bin/ooo**, and then used this. I told nautilus to open all the relevant file types with ooo. Here is that one line script:

/opt/openoffice.org2.0.2/program/soffice "$*"

Noice that I renamed the install directory to that I could install other versions too, so you may have to edit the above script to suit.

---

### Post by Mark_in_Hollywood on 2006-04-17
Success

Of a sort. Using Synaptic I updated, about 11 hours at 56K. Even got a warning from my ISP about too much usage. That's OK they are a non-profit ISP and I pay $50 per year for service.

OOo installed ver. 2. I find it to be way cool. It saves a 26 page document in 2 columns in under 1 second.;)

---

