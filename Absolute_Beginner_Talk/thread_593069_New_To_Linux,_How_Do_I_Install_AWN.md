---
title: "New To Linux, How Do I Install AWN?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by lookmomimonlinux on 2007-10-26
I've checked out past threads that ask the same thing, but everyone replies with "you gotta place this/that in the terminal" what is a terminal? and i got as far as dling awn0.2.tar, when i open the folder i see applets,awn-applet-activation, awn manager so on and so forth. where do i go from here?

---

### Post by Crafty Kisses on 2007-10-26
> **lookmomimonlinux said:**
> I've checked out past threads that ask the same thing, but everyone replies with "you gotta place this/that in the terminal" what is a terminal? and i got as far as dling awn0.2.tar, when i open the folder i see applets,awn-applet-activation, awn manager so on and so forth. where do i go from here?

**Applications>Accessories>Terminal**

That's where the terminal is located. :)

---

### Post by Maestro23 on 2007-10-26
And inside the extracted folder, there should be a README/Install doc with installation instructions.

---

### Post by Crafty Kisses on 2007-10-26
It can be a pain sometimes putting together a file, beleive me. :)

---

### Post by MegaJim on 2007-10-26
documentation for this project

[http://wiki.awn-project.org/index.php?title=DistributionGuides](http://wiki.awn-project.org/index.php?title=DistributionGuides)

just dive in and ask here if you get stuck

---

### Post by lookmomimonlinux on 2007-10-26
alright, it says: 

Add these lines to the bottom of your /etc/apt/sources.list

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

Where/What is this source list?

---

### Post by jusmurph on 2007-10-26
The easiest way is to download the deb from here:
[http://www.getdeb.net/release.php?id=1622](http://www.getdeb.net/release.php?id=1622)

---

### Post by marbig on 2007-10-26
>  Where/What is this source list?Just found out myself. Happy to pass on.
Paste ```
sudo gedit /etc/apt/sources.list
``` in your terminal. It will open up the file for editing. After edit, save and close.

---

### Post by lookmomimonlinux on 2007-10-26
Ok, I downloaded that, now what do I do with it?

---

### Post by Maestro23 on 2007-10-26
> **lookmomimonlinux said:**
> Ok, I downloaded that, now what do I do with it?

Follow the next step in the wiki link provided above provided my MegaJim.

---

### Post by lookmomimonlinux on 2007-10-26
Is the terminal I am able to access through applications->accessories the same one you all are referring to? I accidentally closed the window I had up before that was the awn0.2.tar, folder and I don't where to find it. I must sound impossible to help, but I would really like to learn how to use ubuntu if you folks could be so kind..

---

### Post by Maestro23 on 2007-10-26
> **lookmomimonlinux said:**
> Is the terminal I am able to access through applications->accessories the same one you all are referring to?

Yes.

---

### Post by lookmomimonlinux on 2007-10-26
> **marbig said:**
> Just found out myself. Happy to pass on.
Paste ```
sudo gedit /etc/apt/sources.list
``` in your terminal. It will open up the file for editing. After edit, save and close.



alright, I understand that I have to paste this in the bottom of /etc/apt/sources.list (btw am i supposed to hit enter after pasting these codes?): 

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

and then i have to paste this in the terminal: 

wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update

then i pasted: sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr

to install, but nothing happened?

---

### Post by marbig on 2007-10-26
> alright, I understand that I have to paste this in the bottom of /etc/apt/sources.list (btw am i supposed to hit enter after pasting these codes?):I don't believe so. Just hit the save button up top of text editor then close it.

I'll leave it to others to help on terminal side of problem.

---

### Post by lookmomimonlinux on 2007-10-26
thank you, alright so i save and closed it then the terminal asked for my password again. what should i be pasting now and where?

---

### Post by Maestro23 on 2007-10-26
> **lookmomimonlinux said:**
> thank you, alright so i save and closed it then the terminal asked for my password again. what should i be pasting now and where?

Now just follow the wiki, inputing the commands into a terminal.

> Then do this in a terminal:

wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update

Now to install AWN:

sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr

Or, if you don't want the applets, just do:

sudo apt-get install avant-window-navigator-bzr


---

### Post by BrendanM on 2007-10-26
If you downloaded the .deb file from [www.getdeb.net](www.getdeb.net), you can just double-click on it and put in your password and it will install similarly to a windows installer. You can think of a .deb package as an Ubuntu installer. If you have a .tar.gz file, it may be trickier to install.

---

### Post by lookmomimonlinux on 2007-10-26
sweet, i've made some progress. is that all though? do i just save and close it now?

---

### Post by BrendanM on 2007-10-26
Sounds good. Sorry, save and close what? Are you editing your sources list?

---

### Post by lookmomimonlinux on 2007-10-26
nevermind, i wasn't sure if you saved anything in the terminal. from the looks of things, you don't really choose the option to save in the terminal. right? anyway, do i reboot now or is there another step?

---

### Post by BrendanM on 2007-10-26
In general, you never need to reboot to install software in Linux. You don't need to "save" things you do in the terminal, but if you're using a terminal program (say, a text editor like nano) to edit a file, you will need to save when exiting that program.

Did you just do the "apt-get install" option to install from repositories?

---

### Post by Maestro23 on 2007-10-26
> **lookmomimonlinux said:**
> nevermind, i wasn't sure if you saved anything in the terminal. from the looks of things, you don't really choose the option to save in the terminal. right? anyway, do i reboot now or is there another step?

If you didn't get any errors in terminal, close the terminal. Looks like you are ready to start playing with it.  Check here:  [http://wiki.awn-project.org/index.php?title=FAQ](http://wiki.awn-project.org/index.php?title=FAQ)

---

### Post by PurposeOfReason on 2007-10-26
Run 'avant-window-navigator' in the terminal.

---

### Post by Frak on 2007-10-26
You never need to reboot after installing programs in Ubuntu, unless you install new drivers.

---

### Post by lookmomimonlinux on 2007-10-26
Holy Hell People, My First Breakthrough With Ubuntu! Thank You All Very Much For Reading Through My Dumb Questions And Resisting The Urge To Call Me Retarded And Ignore Me

---

### Post by Maestro23 on 2007-10-26
> **lookmomimonlinux said:**
> Holy Hell People, My First Breakthrough With Ubuntu! Thank You All Very Much For Reading Through My Dumb Questions And Resisting The Urge To Call Me Retarded And Ignore Me

Congrats man. Welcome to Ubuntu. :guitar:

Don't forget to mark this bad boy SOLVED using the Thread Tools.

---

### Post by BrendanM on 2007-10-26
Hahaha, awww. Everyone has to start somewhere. The cool thing about installing software using the repositories is that it lets you keep ALL the software on your computer updated from one centralized location.

---

### Post by Frak on 2007-10-26
> **BrendanM said:**
> Hahaha, awww. Everyone has to start somewhere. The cool thing about installing software using the repositories is that it lets you keep ALL the software on your computer updated from one centralized location.
Good point.

Try installing something on Windows, and the best you'll get is an annoying popup when you startup the program, when Ubuntu updates it from one central location *at your convenience.*

---

