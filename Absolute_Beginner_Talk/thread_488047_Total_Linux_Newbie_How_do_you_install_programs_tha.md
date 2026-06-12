---
title: "Total Linux Newbie: How do you install programs that are 3rd party?"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by HamHamT on 2007-06-29
I tried searching google for about 30 minutes and found nothing. The add/remove programs list doesn't allow me to install it.

Its a game, Graalonline, and it has a supported version of linux for the game as well. When I try to run it its a whole bunch of letters and information about the installer.

The properties tell me its a shell script, other than that, I just get stuck and have no idea what to do. Am I supposed to enter some command in the ctrl+alt+f1 screen?

Thanks in advance!

---

### Post by limbourg31 on 2007-06-29
Did you cd into the folder and then execute ./configure, then make and sudo make install? Before you do that though, make sure you do sudo apt-get install build-essential

---

### Post by glennric on 2007-06-29
I didn't have any trouble installing the file.  I just had to run
```
chmod +x graal4setup
./graal4setup
```
then answer the questions it asks.

Edit: By the way, I am assuming you downloaded the following file:
[http://www.graalonline.com/downloads/graal4setup]("http://www.graalonline.com/downloads/graal4setup")

---

### Post by HamHamT on 2007-06-29
I tried both commands in the ctrl+alt+F1 screen and no luck.

I haven't done anything and I'm using the LiveCD.

The only language I know is very very very basic HTML, I don't know any commands in Linux at all. I couldn't really find a newbies guide to Linux except for really long and complex guides full of text with no illustrations at all to help me out.

---

### Post by glennric on 2007-06-29
You will have to run the commands in a terminal.  Open a terminal from the Applications->Accessories menu and change directories to where ever you downloaded the aforementioned script.  Then run the commands I gave before.

---

### Post by HamHamT on 2007-06-29
> **glennric said:**
> change directories to where ever you downloaded the aforementioned script. 

I got the terminal running and everything else set up, I don't understand this part though, I have the file on my desktop.

---

### Post by glennric on 2007-06-29
If you have the file on your desktop then type 
```
cd ~/Desktop
```
in the terminal.  Then type the other two commands.

---

### Post by HamHamT on 2007-06-29
Very cool, at the end I encountered an error and said my OS might be broken. I didn't think twice and just clicked out of it. So, how can I run the application itself now or am I stuck somewhere?

---

### Post by glennric on 2007-06-29
If it installed correctly it should show up in the Applications->Games menu.

---

### Post by HamHamT on 2007-06-29
Tried it again and got the same error:

Unable to read from /proc/self/exe. Your operating system may be broken. (2)

This happens right after I input the step: ./graal4setup

---

### Post by glennric on 2007-06-29
Hmm, try this and tell me what you get.
```
ls /proc/self/exe
```

---

### Post by HamHamT on 2007-06-29
It just repeats the /proc/self/exe in a cyan color.

Also the icon on my desktop changed into another icon and when I tried to run it this pops up:

[IMG]http://i10.tinypic.com/5yjyee9.png[/IMG]


So far I'm really liking the GUI of this and trying to get away from Windows :) I'm trying to learn this new OS and I'm pretty sure it won't be too hard to learn. As soon as I'm sure I can run this game I'm going to install this onto my computer for keeps.

---

### Post by glennric on 2007-06-29
I am not sure.  Try going to Applications->System Tools and running the Manage 3rd Party Software program.  Then uninstall everything that shows up when you select all.

Then start over and see if anything improves.  I am not sure what to do if that doesn't work.  I have to go now, so maybe someone else will be able to help you.  Sorry.

---

### Post by HamHamT on 2007-06-29
I couldn't find the way you suggested (to uninstall all programs) but since I don't have Linux installed on my harddrive itself I just restarted my computer (using the LiveCD so things don't save across each time I use the CD). At the moment I'm redownloading the GraalOnline client and trying it again and I'll repost with my results.

---

### Post by HamHamT on 2007-06-29
Update, still getting the same error.

Here's the whole thing going on:

I'm using:

```
cd ~/Desktop
chmod +x graal4setup
./graal4setup
```

its all fine until I get here:

```
# # # # # # # # # # # #

Thank you for your patience. Installation of your package will now proceed.
You should not have to install the autopackage support code again.

# # # # # # # # # # # #
```

then this error pops up:

[IMG]http://i19.tinypic.com/4yk2848.png[/IMG]

and now I'm stuck.


If you can't read the message it says:

Unable to read from /proc/self/exe. Your operating system may be broken. (2)

And heres the entire Terminal log:

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ cd ~/Desktop
ubuntu@ubuntu:~/Desktop$ chmod +x graal4setup
ubuntu@ubuntu:~/Desktop$ ./graal4setup

The installation of this software requires some additional support
code to be installed.

A] If the support code is found in a local directory, it will be used.
   The file containing the support code will be called:

      "autopackage.tar.bz2"

 or

B] If there is an active Internet connection, the support code will be
   downloaded from:

      "http://autopackage.org/downloads/latest/autopackage.tar.bz2"

   Proxy users should ensure the http_proxy environment variable is
   set, otherwise the download may fail.


Selection B --> OK to download and install support code now? (Y/n): y

Attempting download of http://autopackage.org/downloads/latest/x86/autopackage.tar.bz2 ... 

--02:16:46--  http://autopackage.org/downloads/latest/x86/autopackage.tar.bz2
           => `autopackage.tar.bz2'
Resolving autopackage.org... 130.225.247.90
Connecting to autopackage.org|130.225.247.90|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://autopackage.org/downloads/latest/logger.php [following]
--02:16:46--  http://autopackage.org/downloads/latest/logger.php
           => `autopackage.tar.bz2'
Connecting to autopackage.org|130.225.247.90|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ftp.sunsite.dk/projects/autopackage/1.2.3/x86/autopackage.tar.bz2 [following]
--02:16:47--  http://ftp.sunsite.dk/projects/autopackage/1.2.3/x86/autopackage.tar.bz2
           => `autopackage.tar.bz2'
Resolving ftp.sunsite.dk... 130.225.247.92
Connecting to ftp.sunsite.dk|130.225.247.92|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 883,555 (863K) [application/x-tar]

100%[====================================>] 883,555      154.05K/s    ETA 00:00

02:16:54 (122.72 KB/s) - `autopackage.tar.bz2' saved [883555/883555]

Download completed.


.............................................................................................
/usr/X11R6/bin/xauth:  creating new authority file /root/.Xauthority
Refreshing linker cache, please wait ... done


Attempting download of http://autopackage.org/downloads/1.2.3/autopackage-gtk-1.2.3.package ... 

--02:17:22--  http://autopackage.org/downloads/1.2.3/autopackage-gtk-1.2.3.package
           => `autopackage-gtk-1.2.3.package'
Resolving autopackage.org... 130.225.247.90
Connecting to autopackage.org|130.225.247.90|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ftp.sunsite.dk/projects/autopackage/1.2.3/autopackage-gtk-1.2.3.package [following]
--02:17:23--  http://ftp.sunsite.dk/projects/autopackage/1.2.3/autopackage-gtk-1.2.3.package
           => `autopackage-gtk-1.2.3.package'
Resolving ftp.sunsite.dk... 130.225.247.92
Connecting to ftp.sunsite.dk|130.225.247.92|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 244,876 (239K) [text/plain]

100%[====================================>] 244,876       88.50K/s             

02:17:26 (88.27 KB/s) - `autopackage-gtk-1.2.3.package' saved [244876/244876]

Download completed.



# Preparing package: Autopackage Software Installer (GTK+)                      
# Checking for required C library versions ... passed
# Checking for GTK+ user interface toolkit ... passed
# Checking for Glade user interface loader library ... passed
# Installing package: Autopackage Software Installer (GTK+) (package 1 of 1)    
# 100%[==================================================] Extracting
# Preparing executables...
# Installing GNOME 2 file type information...
# Installing GNOME 2 application registry entries...
# Installing file type information (MIME)...
# Installing KDE 3.x file type information...
# Registering file type assocations...
# Installing icons...
# Installing icon themes...
# Installing menu items...
# Copying files to /usr/share/autopackage-gtk/glade
# 100%[==================================================] Copying
# Copying files to /usr/share/autopackage-manager
# Copying files to /usr/libexec/autopackage-gtk
# Installing translated dictionary files...
# 100%[==================================================] Copying
# Installing executables...
# Updating package database...

The following package was successfully installed:
* Autopackage Software Installer (GTK+)

The following menu entry is now available:
* Manage 3rd party software (System)

This installation used 785.1 KiB (803.9 kB) of disk space.


Remove this package by running package remove autopackage-gtk from the command line.


# # # # # # # # # # # #

Autopackage support code was installed.
Autopackage graphical interface was installed.

# # # # # # # # # # # #

Thank you for your patience. Installation of your package will now proceed.
You should not have to install the autopackage support code again.

# # # # # # # # # # # #

ubuntu@ubuntu:~/Desktop$ 
ubuntu@ubuntu:~/Desktop$ 

```

---

