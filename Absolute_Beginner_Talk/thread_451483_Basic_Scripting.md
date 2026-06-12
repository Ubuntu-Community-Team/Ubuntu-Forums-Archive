---
title: "Basic Scripting"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by stim on 2007-05-22
Hi Everyone,
I spent the last couple days trying to get ubuntu edgy to work on my lattitue d600, after having problems with suspend\hibernate working I decided to move to feisty.  I must say I am impressed.  Almost everything that didnt work before works now.  However, bcm43xx provides support for my wireless card rather than ndiswrapper.  My problem is that everytime I boot I have to sudo modprobe bcm43xx and then iwconfig to load my wireless.  Since this is a laptop I would like that to happen automatically at boot.   Im a real n00b, so if theres an easy way to script this I would love to hear it.

Chris

---

### Post by matburton on 2007-05-22
There are two ways really,

1. Do it when you log on:

This one is really easy, just choose System -> Preferences -> Sessions
Under Start-up Programs click New and name it with the command you need

2. This ones harder but will do it as soon as you start ubuntu:

First start nautilus with root privileges, hit ALT-F2 and type
```

gksu nautilus

```
Be careful with this, you now have complete control to break your system ;)

Navigate to /etc/init.d
Here is where all the scripts are that are run when the system starts.

Right click and choose Create Document -> Empty File
Name this file something.sh (replace the something) and double click the file
Here paste the command you need into gedit
Save and close the file and then right click and choose Properties on the file
Under the permissions tab make sure the execute field is ticked

Now you have to tell ubuntu to run this script when the system starts
Navigate to /etc/rc2.d
This is the folder for the run level 2, which is the default for ubuntu
All the files are symbolic links to scripts in the previous folder and they all have a number in the name to indicate their order

So choose a number which is not used and open a terminal and type
```

cd /etc/rc2.d
sudo ln -s /etc/init.d/<something>.sh S<num><name> 

```
Replace the < ? > bits with the chosen numbers and names

You should see the new link appear in that folder
Restart ;)
Hope that helps

---

### Post by stim on 2007-05-22
Amazing. Thank you.

---

### Post by ruy_lopez on 2007-05-22
Won't appending "bcm43xx" to "/etc/modules" not do the same thing?

---

### Post by stim on 2007-05-24
yes I tried it and i beleive it does.
however i needed a little kickstart for the scripting because just reading documentation can be a little confusing at first.
I used this to auto-mount my external hard drive and do some other stuff.
Thanks for taking the time to help me, the nubcake.

---

