---
title: "I love being a newbie"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by Cilionelle on 2007-03-03
Hi,

Just (actually "finally") got Xubuntu to install on my older (4 years old) Dell Inspiron, and everything's cool.  Except when it comes to the part about loggin in to [notebook_name].  What is my login name?  I didn't specify one during install, only the password...

So, um... help?

Ta!

---

### Post by Ek0nomik on 2007-03-04
During the install it didn't prompt you with a "Your Name" and "Computer Name"?  It should be one of those...

If not, try root as the username and type in your password?  Not sure, just trying to think of things...

---

### Post by Cilionelle on 2007-03-04
No prompt for user name, and I've already tried "root" and my password, to no avail.  Sigh.

---

### Post by Sef on 2007-03-04
> No prompt for user name,

When installing it asks you for a user name then it asks you for a password.   Do you remember what you put for the user name?  (If it didn't prompt you for a user name, then the install was faulty.)

---

### Post by Cilionelle on 2007-03-04
Well, there was no prompt for a username.  I've tried the install twice, both with the same results.  The install CD I have is for Xubuntu, I think it's the Alternate ISO (or something) because I was trying to set it up on an even older computer (that attempt utterly failed...).

Here's what it looks like:

> Ubuntu 6.06.1 LTS miros tty1

miros login: _

...with the "_" flashing and me not being able to do anything! :confused:

---

### Post by chuckyp on 2007-03-04
Okay well to figure out what you typed in the installer for a username.  reboot the pc in recovery mode from the grub menu.  Then after you receive a prompt type users  this should llist all user accounts on the pc.

---

### Post by pjones0404 on 2007-03-04
did u install the oem verion. 

try oem as the username

---

### Post by H.E. Pennypacker on 2007-03-04
> **Cilionelle said:**
> Well, there was no prompt for a username.  I've tried the install twice, both with the same results.  The install CD I have is for Xubuntu, I think it's the Alternate ISO (or something) because I was trying to set it up on an even older computer (that attempt utterly failed...).

Here's what it looks like:



...with the "_" flashing and me not being able to do anything! :confused:

Are you sure "miros" is not your username?  

What guide did you follow when installing the alternate CD?  Check out this webpage:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Scroll down, and go to the "The three illustrated example installs" section.  Select the one that applies to your case.  If you don't have Windows installed at all, and you only want Ubuntu, you should be able to ignore all the references to Windows.

PS:  The alternate CD definitely asks you for a username and password.

---

### Post by Cilionelle on 2007-03-04
Right!  It was the OEM version of the install, now I am in, but all I got was a command prompt.  How do I get the thing to look like the screenshots from Linux User?  hehehe!  I have no idea where to go from here, since it was supposed to be slightly simpler than this... or am I just silly?

---

### Post by Maestro23 on 2007-03-04
If it's the OEM version:

You can type 'sudo oem-config-prepare' and reboot the machine. Ubuntu will then go through the wizard to create the actual user account for you.

---

### Post by Cilionelle on 2007-03-04
Oh, and thanks for the help, by the way!

---

### Post by Cilionelle on 2007-03-04
Right!  The account is set up.  But I'm still at the prompt, with no GUI or pretty brown screen...

---

### Post by Maestro23 on 2007-03-04
startx

---

### Post by Cilionelle on 2007-03-04
And I get:

> -bash: startx: command not found

---

### Post by kittyhawk63 on 2007-03-04
I installed Xubuntu from Synaptic and had no problem. If I remember correctly, I could be mistaken, it only asked for a password. Whatever it asked, I gave it, and it installed. You might try it from Synaptic and see if you're as successful as I was. At least it will give you a package you know will work.

---

### Post by Cilionelle on 2007-03-04
Um... what's Synaptic?

"Talk to me like I'm a 3-year-old."

I really have no idea what most of the terms are, and am in the middle of it all now, out of my depth!

---

### Post by kittyhawk63 on 2007-03-04
> **Cilionelle said:**
> Um... what's Synaptic?
"Talk to me like I'm a 3-year-old."
I really have no idea what most of the terms are, and am in the middle of it all now, out of my depth!

I apologize. As a relatively newcomer myself. I should have known better. Synaptic is a program inside Ubuntu where you can look at hundreds of programs and have Synaptic download and install them automatically. It is easy to use. Don't go wild! Wait until you know Ubuntu a lttle better, and see what is in the basic package. If you need more or would like to change a program you can do it in Synaptic. 

You will find Synaptic under System->Administration->Synaptic Package Manager. You will need to enter your password to get into Synaptic. Any more questions. I will wait to answer them for you if I can.
kh

---

### Post by kittyhawk63 on 2007-03-04
You can also find more programs under Add/Remove under Application->Add/Remove. There is another program installer with many more programs you can select called Automatix2. That one you download from the Internet. It is an easy install. 
Those are the three most common package installers that the forum talks about. A package is the file that consist of the program you want to install. It may need other files added to get it to work. These other files are called dependencies.
kh

---

### Post by Zyphrexi on 2007-03-04
that's ubuntu, not xubuntu right? yeah and she doesn't have a gui yet. (graphical user interface)

also... startx cannot be found? that's... disconcerting. Somehow I think something went wrong along the way during the install.

type this
```
whereis startx
```

mine spits out this (for comparison)
```
john@ubuntu:~$ whereis startx
startx: /usr/bin/startx /usr/X11R6/bin/startx /usr/bin/X11/startx /usr/share/man/man1/startx.1x.gz

```

---

### Post by kittyhawk63 on 2007-03-04
> **Zyphrexi said:**
> that's ubuntu, not xubuntu right? yeah and she doesn't have a gui yet. (graphical user interface)

Didn't notice it was Xubuntu. I fully apologize. I took the advise from others to start with Ubuntu. It is much easier to work with. I tried Xubuntu for several days and had a difficult time getting around. Didn't like it much at all.

So, if your reading this OP (Original Poster), I would strongly recommend that you load Ubuntu (Dapper 6.06) and start with it. You will be far better off learning Linux.

---

### Post by Cilionelle on 2007-03-04
Zyphrexi's right, and wrong.  I am using Xubuntu, currently have no graphical user interface, but it would be "he's doesn't have a gui yet." :) 

So although your suggestions sound awesome, kittyhawk63, I have no way of getting there...

---

### Post by kittyhawk63 on 2007-03-04
> **Cilionelle said:**
> Zyphrexi's right, and wrong.  I am using Xubuntu, currently have no graphical user interface, but it would be "he's doesn't have a gui yet." :) 
So although your suggestions sound awesome, kittyhawk63, I have no way of getting there...

Cilonelle,
I reread your original post. I can't imagine that you were not asked for a username. Is it possible that you may have thought that it was asking for a password and you entered your password for both questions: username and password?

---

### Post by Cilionelle on 2007-03-04
Okay, here's where I stand at the moment:

I have installed Ubuntu.  I have done it using the OEM version, erasing all other comers from my laptop.  I have chosen a username (an username?) after running oem-config-prepare and am able to login.  However, there is no GUI for me to see, only a command prompt.  When I type "startx", as recommended by one of the others here (thanks!), it says it has no idea what I'm talking about.

What do I do now?

---

### Post by kittyhawk63 on 2007-03-04
> **Cilionelle said:**
> Okay, here's where I stand at the moment:
I have installed Ubuntu.  I have done it using the OEM version, erasing all other comers from my laptop.  I have chosen a username (an username?) after running oem-config-prepare and am able to login.  However, there is no GUI for me to see, only a command prompt.  When I type "startx", as recommended by one of the others here (thanks!), it says it has no idea what I'm talking about.
What do I do now?

Cilionelle, you're over my head on this one. Keep asking. Somone here most likely will know how to resolve your problem. Be patient. Some times it may take a day or two. To keep your post on the first page, you will have to add a post ever so often to this one. I don't mean to start a brand new post. Keep "this" thread going. I am talking of using "post reply."

Good luck. I am keeping you on my subscription list. If there is anything I can help you with, I will post you.
kh

---

### Post by kittyhawk63 on 2007-03-04
Cilionelle,
Do you have broadband? Do you have a CD drive? Do you have a CD burner program? I would download Ubuntu off the Internet and burn it to the CD and use it to install.

You can download the latest version of Ubuntu from:
[http://www.ubuntu.com](http://www.ubuntu.com)

kh

Edit: Cilionelle, I wanted you to know that only today, after two weeks, I have Ubuntu set up right. I just kept at it. Learned a lot. I love this Ubuntu. Can't wait until Feisty Fawn comes out as a LST. (Long Tem Support version.) Hang in there, you won't be sorry.

---

### Post by taurus on 2007-03-04
```
sudo aptitude update
sudo aptitude install xubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by kittyhawk63 on 2007-03-04
> **taurus said:**
> ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
sudo /etc/init.d/gdm start
```

Cilionelle, the right man is here. Listen to this man Taurus. Good evening to you both. I'm off to bed. Past midnight here.
kh

---

### Post by jimrz on 2007-03-04
> **Cilionelle said:**
> Okay, here's where I stand at the moment:

I have installed Ubuntu.  I have done it using the OEM version, erasing all other comers from my laptop.  I have chosen a username (an username?) after running oem-config-prepare and am able to login.  However, there is no GUI for me to see, only a command prompt.  When I type "startx", as recommended by one of the others here (thanks!), it says it has no idea what I'm talking about.

What do I do now?

apparently you do not have X installed. try:
```
sudo apt-get xubuntu-desktop
```
if you are really set on xubuntu, or:
```
sudo apt-get install ubuntu-desktop
```
to get the standard Gnome setup, which may be easier to deal with while learning your way around your new system.
then:
```
sudo /etc/init.d/gdm start
```
 in either case, as soon as you get your gui you will want to do:
```
sudo apt-get update
```
from the terminal and then run the updates from Update Manager

Welcome ... hang in there, it WILL get easier and make better sense as you go forward

---

### Post by bikeboy on 2007-03-04
Hmm, since you haven't yet customised anything, I think you'd be better off starting the install again. Bu this time, don't choose OEM, that's a specialised install for people who are a bit more experienced. Just do the normal install, from the Alternate CD that you already have.

Xubuntu is definitely the right choice for an older pc btw.

---

### Post by Cilionelle on 2007-03-04
...

Is that supposed to illicit some response from the computer.  I have tried both those options, completely uncomprehendingly, and *nothing* has happened when I have pressed enter, other than getting the command prompt up again.

Edit: sorry, bikeboy, I missed your post - which is the "normal" install?

> OEM mode
Text mode
a server
a LTS server

---

### Post by Cilionelle on 2007-03-04
Well, I'm intalling it again as we speak, through the text install option.  It has prompted me for a user name and password, so that is set (one less problem to deal with!).  Thanks to all, and I will continue to post probs I have here for the wise among you to help me with!

---

### Post by bikeboy on 2007-03-04
Ah, text mode I believe. I couldn't remember the options, even though I did an install yesterday lol.

edit: Forgot to refresh, I see that you're trying that already. Hope it works better this time.

---

### Post by Zyphrexi on 2007-03-06
last time I installed ubuntu, breezy was unstable. (yeah I started with an unstable version)

btw the nifty thing about linux (and well ubuntu as you know it) is that all these flavors of ubuntu can be installed through the package management system. 

Let us know if it's working all right.

---

### Post by ubuntu27 on 2007-03-06
> **Cilionelle said:**
> Well, I'm intalling it again as we speak, through the text install option.  It has prompted me for a user name and password, so that is set (one less problem to deal with!).  Thanks to all, and I will continue to post probs I have here for the wise among you to help me with!

Good job!

Now if you have any problems, concerns, or just a question, create a **new** thread about it :)

---

