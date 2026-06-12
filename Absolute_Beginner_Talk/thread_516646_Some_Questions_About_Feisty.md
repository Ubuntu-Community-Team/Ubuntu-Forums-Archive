---
title: "Some Questions About Feisty"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by amneziac on 2007-08-03
I am happy that I finally got Ubuntu running but now since I have been using Windows XP, Ubuntu seems like a different (and somewhat related) language. I have some questions about Ubuntu:

1. Do I need to install Nvidia driver on Ubuntu even though it's installed on Windows? (I have dual boot) If I do, then how do I do it?

2. When I try to enable desktop effects it just gives me a white screen for about 15 seconds then it goes back to normal screen with nothing changed. People told me to go to RDM, but it says my hardware does not need any restricted drivers.

3. When I try to install some programs from the internet, the package includes a lot of unknown file types that I can't use, so what applications should I have installed in order for the computer to read these files?

4. I tried to install a program called TuxGuitar, but when I went to install packages, it said that I can only have one software management tool running at once, but I don't see any running or I'm unaware of where I can close them.

Those are all the questions I have for now. It would be great for someone to tell me exactly how to fix these problems I have in a step by step procedure since I'm a noob and got to learn the new 'lingo'.

Thanks

---

### Post by ev5unleash1 on 2007-08-03
Ok if you get a white screen when enabling Desktop effects is because you are using a Generic Driver for your video card. I know you can go into the X server configuration and enable it. Or reinstall Ubuntu with out safe Graphics mode :).

---

### Post by ev5unleash1 on 2007-08-03
About your other applications not opening it may be because they are windows based and not for Linux. You can try the program WINE at winehq.com they make a software that let's you open Windows Applications.

---

### Post by amneziac on 2007-08-03
how do I go to X server configuration?

---

### Post by amneziac on 2007-08-03
Its not that they don't open, its because the file types are unknown so maybe I need an application install that can read the files. I even tried to install Wine but I oculdnt find a file that would get it to install cause it asks me to choose an application

---

### Post by ev5unleash1 on 2007-08-03
What type of file is it? Please specify what type of file and what it is targeted too.

---

### Post by amneziac on 2007-08-03
well with wine i extracted the folder to my desktop and now it says that the wineinstall is a 'shell script' and when I try to run it, a message comes up to confirm if I want to run it, when I click Run nothing happens...

---

### Post by canadianwriterman on 2007-08-03
> **amneziac said:**
> I am happy that I finally got Ubuntu running but now since I have been using Windows XP, Ubuntu seems like a different (and somewhat related) language. I have some questions about Ubuntu:

1. Do I need to install Nvidia driver on Ubuntu even though it's installed on Windows? (I have dual boot) If I do, then how do I do it?

2. When I try to enable desktop effects it just gives me a white screen for about 15 seconds then it goes back to normal screen with nothing changed. People told me to go to RDM, but it says my hardware does not need any restricted drivers.

3. When I try to install some programs from the internet, the package includes a lot of unknown file types that I can't use, so what applications should I have installed in order for the computer to read these files?

4. I tried to install a program called TuxGuitar, but when I went to install packages, it said that I can only have one software management tool running at once, but I don't see any running or I'm unaware of where I can close them.

Those are all the questions I have for now. It would be great for someone to tell me exactly how to fix these problems I have in a step by step procedure since I'm a noob and got to learn the new 'lingo'.

Thanks

You don't need to install the Nvidia driver in Feisty, unless you want to use desktop effects which requires it. To install, check out the Restricted Drivers Manager under the System menu. It should be listed there, if you have an Nvidia card in your machine. Just click on Enable, let it install and then reboot. Then you should be able to use desktop effects.

Most programs that you are used to downloading from the internet are Windows only and will not work within a normal Linux operating system. You will find people recommending using Wine, which allows you to run some Windows programs in Linux, but I would recommend staying away from it if you are new to Linux. Get used to Linux first and try out all the Linux programs first... you may find replacements for many of the Windows programs you're used to.

The reason it says that you can have only one software management tool at a time is that you probably had Add/Remove Programs and Synaptic running at the same time. They both do the same thing, although Add/Remove Programs is simpler. Close one if you are running the other.

Hope that helps.

---

### Post by ev5unleash1 on 2007-08-03
I beleave shell scripts are pacific for Windows and for a pacific program that uses them. They cannot be opened by them selves. How did you or did you ever open those scripts with a certain program and what are you trying to do or use them for?

---

### Post by Nekiruhs on 2007-08-03
> **ev5unleash1 said:**
> I beleave shell scripts are pacific for Windows and for a pacific program that uses them. They cannot be opened by them selves. How did you or did you ever open those scripts with a certain program and what are you trying to do or use them for?
No. Why would you need a shell script to install Wine on windows? I use shell scripts all the time in linux. Please learn to spell too.

@ OP: Instead of clicking run, click run in terminal. Shell scripts are series of commands for the Terminal, its a text thing. If that doesn't work, check if the first line in it looks like this: #!/bin/bash

---

### Post by amneziac on 2007-08-03
Ok for the Nvidia driver, When I click restricted drivers manager, my Nvidia card does not show up it just simply says 'Your hardware does not need any restricted drivers'
The shell script I found the Wine .rar I read the readme and it said go to tools and click wineinstall but I guess thats not for ubuntu, so now I'm at a page there that tells me to go to Terminal and type some stuff in so I'll try that and see if it works.

---

### Post by Nekiruhs on 2007-08-03
> **amneziac said:**
> Ok for the Nvidia driver, When I click restricted drivers manager, my Nvidia card does not show up it just simply says 'Your hardware does not need any restricted drivers'
The shell script I found the Wine .rar I read the readme and it said go to tools and click wineinstall but I guess thats not for ubuntu, so now I'm at a page there that tells me to go to Terminal and type some stuff in so I'll try that and see if it works.
Ok, to install the nvidia driver use [Envy]("http://www.albertomilone.com/nvidia_scripts1.html"). And to install wine, just do sudo apt-get install wine .

---

### Post by amneziac on 2007-08-03
So Im trying to install Wine using Terminal when I type sudo apt-get update and then it says that dpkg was interrupted, run dpkg --configure -a to fix the problem. When I do it says I need a superuser privilege

---

### Post by amneziac on 2007-08-03
I also tried sudo apt-get install wine but I still get the same error

---

### Post by Nekiruhs on 2007-08-03
> **amneziac said:**
> So Im trying to install Wine using Terminal when I type sudo apt-get update and then it says that dpkg was interrupted, run dpkg --configure -a to fix the problem. When I do it says I need a superuser privilege
Run sudo dpkg --configure -a

---

### Post by amneziac on 2007-08-03
Now when i say sudo apt-get install wine it says

kenan@kenan-desktop:~$ sudo dpkg --configure -a
kenan@kenan-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-bin: Depends: sun-java6-jre (= 6-00-2ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
kenan@kenan-desktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
kenan@kenan-desktop:~$ 

:confused::(

---

### Post by amneziac on 2007-08-03
My computer told me there is an update but when I tried to install them it said Software index is broken so I ran synaptic and it says i have 1 broken package, use the Broken filter to locate it

how can I fix all of this?

---

