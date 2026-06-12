---
title: "Ok trying to find a few things"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Grundalizer on 2007-06-03
After fiddling around with the Ubuntu live CD, i finally made the decision to throw out windows and install Ubuntu as my one operating system.  I have it up and running, and after two freezes i updated my computer with all the updates.

I have been reading these forums for hours now trying to find some things out and have not found anything I need, can anyone point me in the right direction?

1. Is there a single (best) site that has a list you can browse through and click to download freeware software of all types?

2.  Some software I find is in .rpm file extensions, i heard that is redhat, can i not use it in ubuntu?

3.  I heard you can run Kubuntu from Ubuntu by typing in some dpkg command.

4.  Are there any guides on basic linux commands like dpkg so i can use the console a bit more.
As of now I am using Ubuntu just like windows pretty much, clicking icons.  

5.  What are some of your most cherished/favorite programs/add ons for Ubuntu?

Thank you for anyone who takes the time to answer any of these.

---

### Post by Bohlio on 2007-06-03
well, I know the answer to #1 and #5at least!
to find programs that you can install, go to applications>add/remove. There are plenty of programs there.
Also you can go to the Packetmanager, which is located at Systems>Administration>Synaptic Packet Manager. But you cant have them both running at the same time :-)

My favorite program for Ubuntu would have to be Compiz, It is a composite manager that makes your desktop look all sweetlooking and 3D

I hope i was helpful :-P

---

### Post by tdrusk on 2007-06-03
To get the Kubuntu Desktop when running Ubuntu, run this in the terminal (Applications> Accessories>Terminal
```
sudo aptitude install kubuntu-desktop
```

If you want Xubuntu, run 
```
sudo aptitude install xubuntu-desktop
```

After doing this, log out and on the login screen there should be an option to use each of the installed Desktops.

---

### Post by Grundalizer on 2007-06-03
excellent thank you both for quick responses and good info.   in the few minutes i was away i already thought of two other things i forgot to ask.

is there a command in ubuntu that is like ctrl alt del for windows?  to free up freezes?

---

### Post by Bohlio on 2007-06-03
I dont know how to pull up the "task manager" other than running System monitor, which shows processes running, but I'm pretty sure Ctrl Alt Backspace can log you out when you've frozen, although it might be a restart, I cant quite remember. :-)

---

### Post by jfinkels on 2007-06-03
> **Grundalizer said:**
> After fiddling around with the Ubuntu live CD, i finally made the decision to throw out windows and install Ubuntu as my one operating system.  I have it up and running, and after two freezes i updated my computer with all the updates.

I have been reading these forums for hours now trying to find some things out and have not found anything I need, can anyone point me in the right direction?

1. Is there a single (best) site that has a list you can browse through and click to download freeware software of all types?

System > Administration > Synaptic Package Manager
> 
2.  Some software I find is in .rpm file extensions, i heard that is redhat, can i not use it in ubuntu?

Use the program 'alien' to convert .rpm packages to .deb packages.

Install alien by typing this in the terminal:```
sudo aptitude install alien
```

Then use it like this:```
alien filename.rpm
```
> 
3.  I heard you can run Kubuntu from Ubuntu by typing in some dpkg command.

To install the Kubuntu desktop, type the following in the terminal:```
sudo aptitude install kubuntu-desktop
```
> 
4.  Are there any guides on basic linux commands like dpkg so i can use the console a bit more.
As of now I am using Ubuntu just like windows pretty much, clicking icons.  

Google it. Also, you may find 'man pages' interesting. For pretty much any program, type the following in the terminal:```
man [nameofprogram]
```where [nameofprogram] is the name of a program. For example:```
man ls
man dpkg
man aptitude

```
> 
5.  What are some of your most cherished/favorite programs/add ons for Ubuntu?

You'll love Beryl!
```
sudo aptitude install beryl emerald
```

There is a system monitor in System > Administration > System Monitor. You can restart your X-server (the system that controls your graphical windowing environment) by pressing Ctrl+Alt+Backspace.

---

### Post by dbott67 on 2007-06-03
[COLOR=Purple]*EDIT: Too slow typing!! jfinkels said it all! :)*[/COLOR]

> **Grundalizer said:**
>  1. Is there a single (best) site that has a list you can browse through and click to download freeware software of all types?

Yes, the Ubuntu repositories.  Open **SYSTEM > ADMINISTRATION > SYNAPTIC PACKAGE MANAGER**.  Virtually any app you could want has been ported to Ubuntu.  Just search using any descriptive term, there are over 20,000 packages available.

> **Grundalizer said:**
>  2.  Some software I find is in .rpm file extensions, i heard that is redhat, can i not use it in ubuntu?

You can convert (some) rpms to debs using alien.  Before doing so, see if the package exists in the repos or try building from source.  Otherwise:
```
sudo apt-get install alien
```> **Grundalizer said:**
>  3.  I heard you can run Kubuntu from Ubuntu by typing in some dpkg command.

Yep. As fuzzyhair said.

> **Grundalizer said:**
>  4.  Are there any guides on basic linux commands like dpkg so i can use the console a bit more.
As of now I am using Ubuntu just like windows pretty much, clicking icons.  

There are lots ([http://www.google.ca/search?q=linux+commands](http://www.google.ca/search?q=linux+commands)).  Probably the best learning tool is to use these forums.  By reading the posts & ***trying to answer questions***, you will learn a tremendous amount.

> **Grundalizer said:**
>  5.  What are some of your most cherished/favorite programs/add ons for Ubuntu?

- Automatix ([www.getautomatix.com]("http://www.getautomatix.com")) - it gets virtually every add-on I want
- Beryl (eye candy)
- NX Machine ([www.nomachine.com]("http://www.nomachine.com")) - super fast & secure remote access

-Dave

---

### Post by tdrusk on 2007-06-04
> **Bohlio said:**
> I dont know how to pull up the "task manager" other than running System monitor, which shows processes running, but I'm pretty sure Ctrl Alt Backspace can log you out when you've frozen, although it might be a restart, I cant quite remember. :-)
[URL="http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.5-7.04feisty_i386.deb"]
Download this[/URL]
and run it.

After it's finished installing it should be under System tools. Run it and you will see the setting for ctrl+alt+del.

---

