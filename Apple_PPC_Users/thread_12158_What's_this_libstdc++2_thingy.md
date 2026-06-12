---
title: "What's this libstdc++2 thingy?"
date: 2005-01-22
forum: Apple PPC Users
---

### Post by kadymae on 2005-01-22
And how on earth do I get it on my computer?

Why, yes, I am trying to install NVU.

I just ran synaptic with the "universe" repositories checked (but not smart update) and while (once again) I have drenloads of new libstdc++5 and ++6 files, I have no ++2.  Actually, I don't have any number lower than ++5 on my computer.


Why yes, I have tried to manually edit sources.list (using the instructions at ubuntuguide) and I get nothing but cthuluspeak that scrolls off the screen when I run apt-get.

In fact, so far, the whole thing has been a wash,rinse, repeat of my first time getting software to go on Ubuntu.

Thanks.

---

### Post by Viro on 2005-01-22
[QUOTE=kadymae]And how on earth do I get it on my computer?

Why, yes, I am trying to install NVU.

I just ran synaptic with the "universe" repositories checked (but not smart update) and while (once again) I have drenloads of new libstdc++5 and ++6 files, I have no ++2.  Actually, I don't have any number lower than ++5 on my computer.


Why yes, I have tried to manually edit sources.list (using the instructions at ubuntuguide) and I get nothing but cthuluspeak that scrolls off the screen when I run apt-get.

In fact, so far, the whole thing has been a wash,rinse, repeat of my first time getting software to go on Ubuntu.

Thanks.[/QUOTE]
 What's NVU? libstdc++ is the standard C++ library, you need it to run any C++ programs that are compiled using GCC. libstdc++5 is for GCC 3.3 which is the default compiler shipped with Ubuntu, and v6 is kinda experimental.

Don't think there is libstdc++2 since that will be well old.

---

### Post by RevJack on 2005-01-22
This might help. It got Nvu installed and working for me:

[http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-20.3307060179](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-20.3307060179)

---

### Post by kadymae on 2005-01-22
I've been to that link.  I have followed said instructions.  Several times.

Without getting  libstdc++2.10-glibc2.2  on my computer, I can't get NVU to install.

(Go, read, laugh -- it's a rant.

[http://members.cox.net/kadymae/installhell.html](http://members.cox.net/kadymae/installhell.html))


Any other suggestions for how to get  libstdc++2.10-glibc2.2 onboard?

---

### Post by RevJack on 2005-01-22
Did you update the repositories and do apt-get install libstdc++2  glibc2.2?

It worked for me.

---

### Post by kadymae on 2005-01-22
Read the rant.

I update and update and update with "universe" enabled.

I search through all packages.

It. NEVER. Appears.  (And I have the screen caps to prove it)

---

### Post by Viro on 2005-01-23
[QUOTE=kadymae]Read the rant.

I update and update and update with "universe" enabled.

I search through all packages.

It. NEVER. Appears.  (And I have the screen caps to prove it)[/QUOTE]
 I just read through your rant, and I can see where you've gone wrong. :)

The Ubuntu page you were looking at lists the instructions for getting NVU working on x86 Linux (i.e. Intel and AMD chips) since it's the most common processor architecture by far.

This is what you need to do to get it installed on Ubuntu for PPC.

1) Download this file instead of the one in the document. [http://www.nvu.com/download/nvu-0.60-ppc.tar.gz](http://www.nvu.com/download/nvu-0.60-ppc.tar.gz)
2) You don't need libstdc++2.whatever. You need libstdc++5 and libstdc++6. To get these, I'm assuming you've correctly edited your sources.list file and added the correct repositories. You got the errors in your post because you didn't update the local listing of all the files available in the repositories. To correct that, do *sudo apt-get update*. Now install libstdc++ 5 and libstdc++6 by doing *sudo apt-get install libstdc++5* and [sudo apt-get install libstdc++6[/i]
3) Now, you can follow step 2, 4, 5 and 6 in the document you linked.

Hope that helps.

---

### Post by kadymae on 2005-01-23
Okay, updated and have all of ++5 and ++6 on my computer.

I'm using the instructions  here [http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-20.3307060179/view?searchterm=nvu](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-20.3307060179/view?searchterm=nvu)

And I get to this line:
sudo tar xvfj nvu-0.60-pc-linux2.4.23-gnu.tar.bz2 -C /opt/

(which I'm reading as the name of the tarfile[space]-C[space]/opt/)  

Let me copy and paste out of my terminal session.  I'm still getting errors.

> 
kadymae@gilestel:~ $ ls
Desktop  nvu-0.60-ppc.tar.gz  Wallpapers
kadymae@gilestel:~ $ sudo tar xvfj nvu-0.60-ppc.tar.gz -C /opt/
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error exit delayed from previous errors
kadymae@gilestel:~ $


When I try the  instructions from ubuntu guide which say to use jxvf, I get this error:

> 
kadymae@gilestel:~ $ sudo tar jxvf nvu-0.60-ppc.tar.gz -c /opt/
tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' for more information.
kadymae@gilestel:~ $


Thanks.

---

### Post by Viro on 2005-01-23
[QUOTE=kadymae]Okay, updated and have all of ++5 and ++6 on my computer.

I'm using the instructions  here [http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-20.3307060179/view?searchterm=nvu](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-20.3307060179/view?searchterm=nvu)

And I get to this line:
sudo tar xvfj nvu-0.60-pc-linux2.4.23-gnu.tar.bz2 -C /opt/

(which I'm reading as the name of the tarfile[space]-C[space]/opt/)  

Let me copy and paste out of my terminal session.  I'm still getting errors.



When I try the  instructions from ubuntu guide which say to use jxvf, I get this error:



Thanks.[/QUOTE]
 You need to use -xvzf for tar.gz files, and -xvjf for tar.bz2 files.

---

### Post by kadymae on 2005-01-23
Viro --

SNOOPY DANCE SNOOPY DANCE SNOOPY DANCE!

(Now it took me a little hunting and pecking through the file system to find out where, exactly, /opt was .. but NVU is up and running .)

Thanks.  I would never have figured this out without you.

(But I still say this whole alphabet soup approach is a stupid way to install software.)

---

### Post by Viro on 2005-01-24
Agreed. It's a stupid way to install software but that's mainly because it isn't packaged for Debian. If it was, all you would need to do is to search for it via Synaptic Package Manager, or apt-cache. Installing it would be much easier then and it will automatically resolve the dependencies for you by downloading all the necessary libraries (like libstdc++) so the user doesn't have to do all the leg work.

Oh well, glad you got it working. :)

---

### Post by Viro on 2005-01-24
Updated the Wikipage to reflect the changes that apply to the PPC version.

---

### Post by Chris Weaver on 2007-04-29
I use NVU on Windows XP and thanks to all the above I have NVU running on Ubuntu 7.04 PPC. I only have perhaps a simple question:

How to I get it to run for the Applications menu rather than the terminal?

I have made a menu item using Preferences/Main Menu and have put the the command as:

sudo /opt/NVU-0.60/nvu

yet clicking on the icon provides no response?

---

