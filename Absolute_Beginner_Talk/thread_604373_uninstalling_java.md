---
title: "uninstalling java"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by raheel on 2007-11-06
[Linux newbie here so forgive my lack of proper term usage]

In trying to install java on Ubuntu so I can run java apps in FireFox, I went to [www.java.com](www.java.com) and downloaded the jre-6u3-linux-i586.bin package.

After finding some instructions on that same website about what to do with the package, I installed it (I think) using the command:

./jre-6u3-linux-i586.bin

I did that while the bin file was sitting on the desktop.  Being used to how installation on Windows work, I thought the package would install itself in the appropriate folder somewhere in the system but instead it created a folder named jre.6.0_03 on my desktop with a lock on the folder.

After some effort to try to get rid of it, only to be met with Access Denied errors, I did some more research and discovered Add/Remove programs and 'Synaptic Package Manager'.  In other words, I did not have to navigate to java.com to obtain java.

RTFM came to mind ...

Nevertheless, I still have the problem of getting rid of this installation so I can install java using one using one of the two features I just mentioned.

Anyone who can offer help, in detailed steps (did I mention I am a total newbie to linux?), please feel free to offer a solution.

Thanks,

Raheel.

---

### Post by juantovarm on 2007-11-06
Ok, welcome to not having to surf for software :popcorn:
Open synaptic and check if it shows up as installed. If it does, simply tell it to un-install it. 

In order to remove the package with the lock you must be root, or have root priviledges, this is where the sudo command comes in handy.

Type this in the terminal:

gksudo nautilus

That will give you a superuser graphical interface, simply go to your desktop and remove the folder. Since you are a newbie, I strongly suggest you close the superuser nautilus interface as soon as you eliminate the folder, cause you can seriously damage your installation playing ariound in that mode

---

