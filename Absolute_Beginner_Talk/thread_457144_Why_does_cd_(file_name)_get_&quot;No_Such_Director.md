---
title: "Why does cd (file name) get &quot;No Such Directory&quot;....?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-05-28
Hi, I'm on Ubuntu Feisty, and I'm getting better at installs, but this one is hanging me up.

I'm trying to install a driver for my Epson Stylus RX580 and I downloaded this driver: pipslite-cups-1.0.0-1.i386.rpm_FILES

I have it on my desktop and 'cd Desktop' gets me to my desktop directory just fine. So I run this command according to the instructions:
                          rpm -i pipslite-cups-1.0.0-1.i386.rpm 

I get Error: opening of Filename.....no such file or directory

And if I try to get the file name directory by doing this:  cd pipslite-cups-1.0.0-1.i386.rpm
I get 'No such file or directory'

I appreciate any assistance. I've also downloaded a tar.gz source file but I can't seem to install that either.
Many Thanks for any help, Frank

---

### Post by taurus on 2007-05-28
Maybe because the file is called pipslite-cups-1.0.0-1.i386.rpm_FILES.

What's the output of this command from a terminal?

```
cd ~/Desktop
ls -la
```

---

### Post by LPomfrey on 2007-05-28
An "rpm" file is a Red Hat package, you might need to convert it to a Debian package before you install using Alien.

First install Alien with:
```
sudo aptitude install alien
```

Then cd to your desktop and type:
```
alien <package_name>.rpm
```
To convert it to a Debian package. Followed by:
```
sudo dpkg -i <package_name>.deb
```

Alternatively for the last step you could just double click on the created .deb package to install it graphically with GDebi.

EDIT: I'm probably wrong here as it seems what you typed, with respect to rpm,  should work.

---

### Post by Brightbelt on 2007-05-28
Thanks for helping; here's what I got:

brightbelt@brightbelt-desktop:~/Desktop$ ls -la
total 1272
drwxr-xr-x  4 brightbelt brightbelt   4096 2007-05-28 12:36 .
drwxr-xr-x 25 brightbelt brightbelt   4096 2007-05-28 12:39 ..
-rw-r--r--  1 brightbelt brightbelt   8205 2007-04-10 19:03 evolution.desktop
-rw-r--r--  1 brightbelt brightbelt   2422 2007-04-03 10:52 firefox.desktop
-rw-r--r--  1 brightbelt brightbelt   4245 2007-01-16 09:12 gimp-2.2.desktop
-rw-r--r--  1 brightbelt brightbelt   4935 2007-03-13 08:58 gnome-terminal.desktop
-rw-r--r--  1 brightbelt brightbelt   4878 2007-03-31 03:49 k3b.desktop
-rw-r--r--  1 brightbelt brightbelt   2654 2007-04-07 06:29 kpdf.desktop
-rw-r--r--  1 brightbelt brightbelt   7078 2007-04-10 20:54 ooo-calc.desktop
-rw-r--r--  1 brightbelt brightbelt   7716 2007-04-10 20:54 ooo-writer.desktop
drwxrwxrwx 16 brightbelt brightbelt   4096 2006-02-06 23:55 pipslite-1.0.0
-rw-r--r--  1 brightbelt brightbelt 934440 2007-05-28 12:30 pipslite-1.0.0.tar.gz
-rw-r--r--  1 brightbelt brightbelt 276171 2007-05-28 12:30 pipslite-cups-1.0.0-1.i386.rpm
drwxr-xr-x  5 brightbelt brightbelt   4096 2007-05-28 12:35 pipslite-cups-1.0.0-1.i386.rpm_FILES
brightbelt@brightbelt-desktop:~/Desktop$

---

### Post by taurus on 2007-05-28
```
sudo aptitude update
sudo aptitude install alien
alien pipslite-cups-1.0.0-1.i386.rpm
sudo dpkg -i pipslite-cups-1.0.0-1.i386.deb
```

---

### Post by Brightbelt on 2007-05-28
More Thanks to you both -- when I do this command:
alien pipslite-cups-1.0.0-1.i386.rpm 

It tells me to run as root in order to convert to deb.

So,...going to the next one since FPomfrey went to this first anyways and trying this: 
sudo dpkg -i pipslite-cups-1.0.0-1.i386

I get "Errors were encountered while processing pipslite-cups-1.0.0-1.i386"

I appreciate any follow-up help with this. Thanks, Frank

---

### Post by taurus on 2007-05-28
```
sudo alien pipslite-cups-1.0.0-1.i386.rpm
sudo dpkg -i pipslite-cups-1.0.0-1.i386.deb
```

---

### Post by Brightbelt on 2007-05-28
Sorry, that's 'LPomfrey'....My apologies, Frank

---

### Post by Brightbelt on 2007-05-28
I'm sorry, I should have mentioned that I tried inserting 'sudo' into the command. I tried both of yours commands, Taurus, by copying and pasting...

I still get that 'errors were encountered while processing this file'... I'm wondering if the file got corrupted somehow. I may just re-download the driver and try again...

I appreciate your help and any further ideas if you have them. Many Thanks, Frnak

---

### Post by LPomfrey on 2007-05-28
> **Brightbelt said:**
> More Thanks to you both -- when I do this command:
alien pipslite-cups-1.0.0-1.i386.rpm 

It tells me to run as root in order to convert to deb.

So,...going to the next one since FPomfrey went to this first anyways and trying this: 
sudo dpkg -i pipslite-cups-1.0.0-1.i386

I get "Errors were encountered while processing pipslite-cups-1.0.0-1.i386"

I appreciate any follow-up help with this. Thanks, Frank
Replace:
```
alien <package_name>.rpm
```

With:
```
sudo alien <package_name>.rpm
```

In the instructions above. 

For future reference, if something asks to be run as root then you will need to add "sudo" in front of the terminal command. (Or if you're running a graphical application, which we aren't here, use "gksudo".)

---

### Post by LPomfrey on 2007-05-28
> **Brightbelt said:**
> I'm sorry, I should have mentioned that I tried inserting 'sudo' into the command. I tried both of yours commands, Taurus, by copying and pasting...

I still get that 'errors were encountered while processing this file'... I'm wondering if the file got corrupted somehow. I may just re-download the driver and try again...

I appreciate your help and any further ideas if you have them. Many Thanks, Frnak
There are drivers in Ubuntu for the Epson Stylus RX500 and RX510 that you could possibly try if you haven't already. Other than that, you may need to compile from source.

Extract the .tar.gz file into a directory then enter that directory in a terminal.

Install the packages needed to compile using:
```
sudo aptitude install build-essential checkinstall
```

Then type:
```
./configure
make
sudo checkinstall -D
```

---

### Post by Brightbelt on 2007-05-28
I hope it's ok to post this to place it forward, in case Taurus and/or LPomfrey (or anyone!!) can help pick up where we left off. 

I tried all the commands with sudo and it didn't make the difference. So I'm wondering if there any other ideas out there to try.

Many Thanks for your help thus far; I'm still getting messages like "Error processing filename" or 'No such directory' etc...

Thanks, Frank

---

### Post by LPomfrey on 2007-05-28
> **Brightbelt said:**
> I hope it's ok to post this to place it forward, in case Taurus and/or LPomfrey (or anyone!!) can help pick up where we left off. 

I tried all the commands with sudo and it didn't make the difference. So I'm wondering if there any other ideas out there to try.

Many Thanks for your help thus far; I'm still getting messages like "Error processing filename" or 'No such directory' etc...

Thanks, Frank
Did you try the other Epson RX5xx drivers that are already installed or compiling from source?

---

### Post by Brightbelt on 2007-05-28
LPomfrey, Hi, I missed your posts because of the Page 2 thing. I'm still getting used to that.

I have already tried the RX500, RX510 and the RX600 drivers. I get communication with my printer, but it doesn't print anything; it just begins to load and spit out blank papers, one after another !! I have to turn the printer off to get it to stop loading and shuffling out blank paper. 

But the next effort is to compile from source, so here goes and I'll post back my results.

Thanks for sticking with me on this!!!! I really do appreciate it,...Frank Bright

---

### Post by Brightbelt on 2007-05-28
Ok LPomfrey,
 what this comes down to is that when I try to configure, or refer to the file on my desktop, it says no such directory... The build-essential part worked, but here's the rest of it. I hope you can make sense of it:

...<<.(build essential part worked - here's the last few lines of that part)>>
Setting up libstdc++6-4.1-dev (4.1.2-0ubuntu4) ...
Setting up g++-4.1 (4.1.2-0ubuntu4) ...
Setting up g++ (4.1.2-1ubuntu1) ...

Setting up build-essential (11.3) ...
brightbelt@brightbelt-desktop:~$ ./configure
bash: ./configure: No such file or directory
brightbelt@brightbelt-desktop:~$ make
make: *** No targets specified and no makefile found.  Stop.
brightbelt@brightbelt-desktop:~$ ./configure make sudo checkinstall -D
bash: ./configure: No such file or directory
brightbelt@brightbelt-desktop:~$ ./configure
bash: ./configure: No such file or directory
brightbelt@brightbelt-desktop:~$ cd pipslite-1.0.0
bash: cd: pipslite-1.0.0: No such file or directory
brightbelt@brightbelt-desktop:~$ cd Pipslie-1.0.0
bash: cd: Pipslie-1.0.0: No such file or directory
brightbelt@brightbelt-desktop:~$ cd pipslite
bash: cd: pipslite: No such file or directory
brightbelt@brightbelt-desktop:~$ cd Pipslite
bash: cd: Pipslite: No such file or directory
brightbelt@brightbelt-desktop:~$ make
make: *** No targets specified and no makefile found.  Stop.
brightbelt@brightbelt-desktop:~$

---

### Post by LPomfrey on 2007-05-28
> **Brightbelt said:**
> Ok LPomfrey,
 what this comes down to is that when I try to configure, or refer to the file on my desktop, it says no such directory... The build-essential part worked, but here's the rest of it. I hope you can make sense of it:

...<<.(build essential part worked - here's the last few lines of that part)>>
Setting up libstdc++6-4.1-dev (4.1.2-0ubuntu4) ...
Setting up g++-4.1 (4.1.2-0ubuntu4) ...
Setting up g++ (4.1.2-1ubuntu1) ...

Setting up build-essential (11.3) ...
brightbelt@brightbelt-desktop:~$ ./configure
bash: ./configure: No such file or directory
brightbelt@brightbelt-desktop:~$ make
make: *** No targets specified and no makefile found.  Stop.
brightbelt@brightbelt-desktop:~$ ./configure make sudo checkinstall -D
bash: ./configure: No such file or directory
brightbelt@brightbelt-desktop:~$ ./configure
bash: ./configure: No such file or directory
brightbelt@brightbelt-desktop:~$ cd pipslite-1.0.0
bash: cd: pipslite-1.0.0: No such file or directory
brightbelt@brightbelt-desktop:~$ cd Pipslie-1.0.0
bash: cd: Pipslie-1.0.0: No such file or directory
brightbelt@brightbelt-desktop:~$ cd pipslite
bash: cd: pipslite: No such file or directory
brightbelt@brightbelt-desktop:~$ cd Pipslite
bash: cd: Pipslite: No such file or directory
brightbelt@brightbelt-desktop:~$ make
make: *** No targets specified and no makefile found.  Stop.
brightbelt@brightbelt-desktop:~$
Did you extract the .tar.gz file to it's own folder and enter that folder before trying "./configure"?

---

### Post by Brightbelt on 2007-05-28
Yes, that's what the pipslite-1.0.0 filename is. I did 'Extract Here' right on the desktop. And as you can see, I'm trying to get the file directory set and it won't recognize it. 

Any other ideas? Thanks, Frank

---

### Post by Brightbelt on 2007-05-28
Here's another try:

brightbelt@brightbelt-desktop:~$ sudo apt-get install pipslite-1.0.0
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pipslite-1.0.0
brightbelt@brightbelt-desktop:~$

---

### Post by LPomfrey on 2007-05-28
I've managed to get alien to create a Debian package that should install. You can get it from my web site here:
[http://www.lukepomfrey.com/_includes/pipslite_1.0.0-2_i386.deb](http://www.lukepomfrey.com/_includes/pipslite_1.0.0-2_i386.deb)

As for what you need to do to get it working after installation I'm afraid I have no idea.

---

### Post by Brightbelt on 2007-05-28
Thanks Luke !!! It installed just fine. However, you are correct. As for getting the actual printer or driver going, I'm at a loss.

But at least this may be a successful first step. 

Many Thanks - I appreciate your efforts and sharing,...Frank

---

### Post by LPomfrey on 2007-05-28
> **Brightbelt said:**
> Thanks Luke !!! It installed just fine. However, you are correct. As for getting the actual printer or driver going, I'm at a loss.

But at least this may be a successful first step. 

Many Thanks - I appreciate your efforts and sharing,...Frank
Try opening a terminal and typing:
```
pipslite
```

Or:
```
ekpstm
```

They appear to be the printer control programs but not having an Epson printer I can't offer any more advice, sorry.

---

### Post by Brightbelt on 2007-05-28
Ok, Luke,  I typed 'ekpstm' and I got back a message that said something like this:

"Ekpd is not started. To load a printer, ekpd must be started. (blah, blah, blah,....) Type this as a root command:
#/etc/rc.d/init.d/ekpd start ""

So I do so and here's what I get:

brightbelt@brightbelt-desktop:~$  sudo #/etc/rc.d/init.d/ekpd start
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
brightbelt@brightbelt-desktop:~$  

I don't think anything came of it.  But when I typed ekpstm, a window with a printer icon came up, so there's some hope (I hope!). 

That's where I am now. Thanks for any ideas,....Frank

---

### Post by LPomfrey on 2007-05-28
> **Brightbelt said:**
> Ok, Luke,  I typed 'ekpstm' and I got back a message that said something like this:

"Ekpd is not started. To load a printer, ekpd must be started. (blah, blah, blah,....) Type this as a root command:
#/etc/rc.d/init.d/ekpd start ""

So I do so and here's what I get:

brightbelt@brightbelt-desktop:~$  sudo #/etc/rc.d/init.d/ekpd start
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
brightbelt@brightbelt-desktop:~$  

I don't think anything came of it.  But when I typed ekpstm, a window with a printer icon came up, so there's some hope (I hope!). 

That's where I am now. Thanks for any ideas,....Frank
You need to remove the # from that.

Type:
```
sudo /etc/rc.d/init.d/ekpd start 
```

That should sort it.

---

### Post by Brightbelt on 2007-05-28
Here's what I got:

brightbelt@brightbelt-desktop:~$ sudo /etc/rc.d/init.d/ekpd start
Password:
sudo: /etc/rc.d/init.d/ekpd: command not found

I feel like I'm in a digital desert,.....;) Frank

---

### Post by LPomfrey on 2007-05-28
> **Brightbelt said:**
> Here's what I got:

brightbelt@brightbelt-desktop:~$ sudo /etc/rc.d/init.d/ekpd start
Password:
sudo: /etc/rc.d/init.d/ekpd: command not found

I feel like I'm in a digital desert,.....;) Frank
Try typing the following in a terminal:
```
sudo /usr/share/EPAva/LITE/inst-rc_d.sh
```

---

### Post by Brightbelt on 2007-05-28
Here's what that did:

brightbelt@brightbelt-desktop:~$ sudo /usr/share/EPAva/LITE/inst-rc_d.sh
Usage: install-rc_d.sh { install | deinstall | checkdist }
brightbelt@brightbelt-desktop:~$

Did that do anything? Thanks for sticking with me Luke !! Frank

---

### Post by LPomfrey on 2007-05-28
> **Brightbelt said:**
> Here's what that did:

brightbelt@brightbelt-desktop:~$ sudo /usr/share/EPAva/LITE/inst-rc_d.sh
Usage: install-rc_d.sh { install | deinstall | checkdist }
brightbelt@brightbelt-desktop:~$

Did that do anything? Thanks for sticking with me Luke !! Frank
No, not yet. I'm just going through the documentation here to try and work out what needs to be run to install everything. The package installed a few scripts that need to be run before things will work by the looks of things.

You'll want the install option so:
```
sudo /usr/share/EPAva/LITE/inst-rc_d.sh install
```

And:
```
sudo /usr/share/EPAva/LITE/pipslite-install
```

---

### Post by Brightbelt on 2007-05-28
Ok, We're Close !! I get a window that says...

 "PPD file needs to be created for the printer to be registered to CUPS. Please make sure that your Printer is connected to the computer and that you have it turned on" (I do have it on and connected already).

And there's a 'Continue' button that is a part of this window, BUT, it is greyed-out so it is not an option. And there's a 'Cancel' button which is Not greyed-out.

What do we do now? Many Thanks, Frank

---

### Post by LPomfrey on 2007-05-28
> **Brightbelt said:**
> Ok, We're Close !! I get a window that says...

 "PPD file needs to be created for the printer to be registered to CUPS. Please make sure that your Printer is connected to the computer and that you have it turned on" (I do have it on and connected already).

And there's a 'Continue' button that is a part of this window, BUT, it is greyed-out so it is not an option. And there's a 'Cancel' button which is Not greyed-out.

What do we do now? Many Thanks, Frank
First type:
```
sudo /etc/init.d/ekpd start
```
This starts the daemon that the first command above installed. This has to be running for you to be able to use your printer, from now on it will start whenever you turn your computer on.

Next, make sure your printer is plugged in and turned on. Type:
```
sudo /usr/share/EPAva/LITE/pipslite-install
```
Again.

You should now be able to install your printer using the Add Printer dialogue in System > Administration > Printing
The driver should be in the "Epson" group, and called something like "Photo Image Print System" with maybe your printer model at the end.

---

### Post by Brightbelt on 2007-05-28
Well,...I got the same window about the PPD file and the 'Continue' button is greyed out. I also checked the System/Administration/Printer interface to see if somehow the RX580 got added to the list, but it wasn't there. 

It seems like we're SO close. But of course, this is all way over my head, so I have no idea what to try next. 

I appreciate your help and I hope this isn't holding up your time at all. If you can stick with me, that'd be great, but I understand if you have other things to do.

Let me know if you want to keep going. Otherwise, I'll close it up for today maybe. Many Thanks, Frank Bright

As My Way of Showing Thanks: Download free music of mine [www.frankbright.com/compositions.htm](www.frankbright.com/compositions.htm)

---

### Post by LPomfrey on 2007-05-28
> **Brightbelt said:**
> Well,...I got the same window about the PPD file and the 'Continue' button is greyed out. I also checked the System/Administration/Printer interface to see if somehow the RX580 got added to the list, but it wasn't there. 

It seems like we're SO close. But of course, this is all way over my head, so I have no idea what to try next. 

I appreciate your help and I hope this isn't holding up your time at all. If you can stick with me, that'd be great, but I understand if you have other things to do.

Let me know if you want to keep going. Otherwise, I'll close it up for today maybe. Many Thanks, Frank Bright

As My Way of Showing Thanks: Download free music of mine [www.frankbright.com/compositions.htm](www.frankbright.com/compositions.htm)
Try stopping CUPS with:
```
sudo /etc/init.d/cupsys stop
```
Then running:
```
sudo /usr/share/EPAva/LITE/pipslite-install
```
And then restarting CUPS with:
```
sudo /etc/init.d/cupsys start
```
Then check in System > Administration > Printing again.

I'll stick around and try and get this sorted but I'll have to get some sleep soon. It's 0340 here. :? I'll check out some of your songs later though. :)

---

