---
title: "Kubuntu and Firefox (and some theme business)"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by Zeno50 on 2005-12-26
I have a fresh installation of Kubuntu on my laptop.  I thought that firefox was preinstalled so I followed the wiki instructions for updating firefox.  [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)


After following those instructions I realized that FF only comes preinstalled on Ubuntu and not Kubuntu.  So then I used Adept and installed the Ubuntu build of FF.  It then appeared in my applications menu, however every time I click on it nothing happens. I uninstalled the package through Adept, restarted, reinstalled...still can't get the browser to open.  Do I have to reformat again to use Firefox?

Also I downloaded the Acqua theme from kde-look.org to my home directory but I don't know how to apply it or add it to the built in theme manager.  I'm confused on how tar files work in general if anyone wants to explain it in a more conceptual way.

Like in Windows to install something (add it to start menu, add/remove list, registry entries, etc) you use the setup.exe file or at least something to that effect.  What is the Linux analogy to this?  And if it's the package manager, how does downloading stuff outside the package manager (like themes?) and installing them work?

I know Windows XP inside and out but I'm finally attempting the Linux switch so I'm willing to go through anything painful or time consuming.


Thank you in advance!

---

### Post by robert114 on 2005-12-26
Proberly the first step to trouble shoot Firefox is to open a terminal like Konsole and type firefox in it and press enter to see what error's you get. 

you can start the Konsole program from the menu
"START" => SYSTEM => TERMINAL PROGRAM(Konsole) or something like that i'm using a dutch version of KDE!

You can post the outcome of the terminal on this forum. so we can have a look at it!

---

### Post by Zeno50 on 2005-12-26
In the konsole, typing firefox and then enter produces

bash: firefox: command not found

---

### Post by robert114 on 2005-12-26
Well that indicates that firefox is not properly installed.

alltoag *(bad english i know)* i'm using Kubuntu I do not use Adept instead i use synaptic i like this program better.

Anyway, you could try installing firefox from the commandline the only negative point is that you won't get the 1.5 version but 1.07 instead this is because Ubuntu is released with Firefox 1.X 

Any way you can install it on the command line in Konsole with the following command: sudo apt-get install firefox 

If any thing goes wrong you can post it here!

---

### Post by Zeno50 on 2005-12-27
Yeah, I have uninstalled and reinstalled the Ubuntu version, and it will show up in the application menu.  However, nothing happens when I click on it.

The only thing I can think of is that those instructions I followed for updating it before it was even installed messed something up.

---

### Post by robert114 on 2005-12-27
But have you tried to install firefox via apt-get in Konsole I'm curious in the output off the installation.

---

