---
title: "What version of linux should I run on my laptop?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Ludford on 2007-06-27
I've been having some trouble with ubuntu like files disapearing and some crashing, so is there a better version of linux that has more of the bugs sorted, and dosn't come up with errors when trying to install stuff.

also thats compatable with compiz/beryl

Is there one that uses a simpler executable file, I could never download anything becuase I have no idea what a "binary" is.

---

### Post by Inxsible on 2007-06-27
> **Ludford said:**
> I've been having some trouble with ubuntu like files disapearing and some crashing, so is there a better version of linux that has more of the bugs sorted?
 
also thats compatable with compiz/beryl
 
What is your system config ?

---

### Post by overdrank on 2007-06-27
> **Ludford said:**
> I've been having some trouble with ubuntu like files disapearing and some crashing, so is there a better version of linux that has more of the bugs sorted?

also thats compatable with compiz/beryl

Hi can you give a little info on your system?

---

### Post by Seisen on 2007-06-27
Your graphics card has to be compatiable with compiz/beryl otherwise it won't work. Well besides Ubuntu you can try Fedora, SuSE, Mandriva, etc... 

[http://distrowatch.com/]("http://distrowatch.com/")

---

### Post by Ludford on 2007-06-27
whoops, Intel core duo, 1GB RAM, 128mb Intel card.

What I'm looking for is one where most of the bugs have been ironed out.

---

### Post by Inxsible on 2007-06-27
> **Ludford said:**
> whoops, Intel core duo, 1GB RAM, 128mb Intel card.
 
What I'm looking for is one where most of the bugs have been ironed out.
 
Your system is good enough to run Ubuntu or Kubuntu or any other distro. Compiz/Beryl might be a problem tho

---

### Post by Feba on 2007-06-27
Ubuntu is about as ironed out as you're going to get. If you don't take the time to read a few tutorials, you're going to suffer, not matter what type of computer you try to use.

---

### Post by Ludford on 2007-06-27
Any one know how to get round the log-in screen, I've forgotten my username

---

### Post by 3rdalbum on 2007-06-27
I've been reading some of your posts. I don't see any "bugs" that you are running into - it looks more like you don't know what you're doing, and that you've jumped in the deep end with Ubuntu rather than properly learn the basics.

A binary installer is a program that is hardwired to install one other program. Anything you've installed under Windows is a binary installer. Linux tends not to use these, for various good reasons. For now, I suggest you stay within the Ubuntu repositories, or find .deb packages for anything else you want to install. The "errors" when trying to install are possibly permissions-related - before you can execute an Autopackage or a binary installer (.run), you must tell Ubuntu that it is safe to execute. You do this by right-clicking the file, going to Properties, then the Permissions tab, and make it executable.

If a program is provided as a .tar.gz file, then it is source code. Source code is distributed for Extremely Good Reasons, but it is probably a little difficult to install from if you've only been using Linux for a month.

You will not find anything easier than .deb packages and the Ubuntu repositories for installing software. Other distributions use other sorts of packages, but these are very similar to the Debian packages that Ubuntu uses.

Hang in there. Linux and Ubuntu are very, very different operating systems to anything you've used before, and you do seem to be trying to jump into the deep end.

---

### Post by forestpixie on 2007-06-27
[http://ubuntuforums.org/showthread.php?t=463155&highlight=forgotten+username](http://ubuntuforums.org/showthread.php?t=463155&highlight=forgotten+username)

this link could help with your username issue

g luck

---

### Post by 3rdalbum on 2007-06-27
Getting around the login screen: When you first start up the computer and you get the GRUB menu, choose the second item on the list (the one which has "Recovery Mode" in it).

---

### Post by Canis familiaris on 2007-06-28
> **Ludford said:**
> Any one know how to get round the log-in screen, I've forgotten my username
NOTE: This may NOT work.
I am not sure but you can try booting into the recovery mode  and in prompt:
```
startx
```
Now go to System->Administration->Users and Groups and you can see your username.

---

### Post by rillip on 2007-06-28
or you can always boot from the live cd

---

### Post by Grigorius on 2007-06-30
Please don't do any of that your username is written in the bottom right corner! (when you are in the log in screen) just look there!

EDIT: I just realized I'm a bit late ... ups.

---

### Post by farueulogy on 2007-06-30
> **Ludford said:**
> I've been having some trouble with ubuntu like files disapearing and some crashing, so is there a better version of linux that has more of the bugs sorted, and dosn't come up with errors when trying to install stuff.

also thats compatable with compiz/beryl

Is there one that uses a simpler executable file, I could never download anything becuase I have no idea what a "binary" is.

lol - don't blame your problems on Ubuntu, sounds like broken hardware for the lost files and crashing.

Ubuntu does use a simple executable file - .deb - see [http://www.getdeb.net/](http://www.getdeb.net/)

It also has something called the synaptic package manager which has a load of applications stored up in it - along with the add remove application you should be able to find most of what you want unless you're looking for flash MX or something.

---

