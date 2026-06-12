---
title: "Installing flash player on amd64 system"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Thrasonic on 2007-03-22
I'm running Ubuntu 6.10.  I'm trying to follow the instructions from the adobe web page for installing this but it's not working.  I am running an amd64.  Can flash player be installed on this architecture?  If so, how?  Below is the error I'm getting.

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

---

### Post by cowlip on 2007-03-22
Macromedia Flash is only 32 bit and only for certain architectures.  Try this for amd64: [https://help.ubuntu.com/community/FirefoxAMD64FlashJava](https://help.ubuntu.com/community/FirefoxAMD64FlashJava)

Konqueror can use 32 bit flash, but Firefox needs a bit of work to get it going

There are new free open source alternatives such as Gnash and swfdec that can be used on any architecture (swfdec also plays youtube videos, just google their names).

---

### Post by Thrasonic on 2007-03-22
Thanks, I'll give swfdec a try and report back.

---

### Post by Thrasonic on 2007-03-22
Okay, I dl'd it, extracted it, opened a terminal to the folder and ran .configure just as the install file said to do.  Than the instructions say to type make to compile the package.  However, when I type make I get the following:

bubba@ubuntu:~/Desktop/swfdec-0.4.3$ make
make: *** No targets specified and no makefile found.  Stop.

What am I doing wrong?  I'm a total newbie so please keep that in mind...

---

### Post by Thrasonic on 2007-03-22
bump

---

### Post by aanderse on 2007-03-22
hey,

what is happening here (i assume) is that you don't have the proper dependencies installed.  you will need to take a look at the output when you try to compile code, see what errors it gives you.  if you have never compiled before it might be a bit overwhelming but you can find all the help you need here.

start by using a terminal and making sure you have your compiling tools ready:
sudo apt-get build-essential

then you will need to install the pango development files, glib, gtk, etc ...  so if you don't know what i'm talking about you'll have to post some more questions, but if you do, then just work through the ./configure output until it successfully runs for you.

---

### Post by cowlip on 2007-03-22
Did you run .configure or ./configure ?  Try running ./configure
 , and of course install build-essential as aanderse said

Also for Debian systems like Ubuntu, install checkinstall to intregrate a source package into apt so you can keep track and uninstall it easily.  "sudo apt-get install checkinstall"

Then, instead of "sudo make install", you do "sudo checkinstall"

so
1) ./configure
2) make
3) sudo checkinstall

---

### Post by Thrasonic on 2007-05-02
When I try to run the sudo apt-get build-essential I get the following error message:

E: Invalid operation build-essential

Can you tell me what's wrong?  I did successfully install checkinstall, however.

---

### Post by Thrasonic on 2007-05-02
I've also tried going the swfdec route again but I get the following error:

configure: error: Couldn't find a suitable Gtk version. You need at least version 2.8.0

I don't know what that means or what needs to be installed.

---

### Post by macogw on 2007-05-02
You can replace Firefox with 32-bit Swiftfox & put 32bit Flash on that.  I know this advice is hated here, but Automatix can do it...

---

### Post by Kilz on 2007-05-04
If you prefer a freeer alternative to Swiftfox (proprietary application), look in my signature.

---

