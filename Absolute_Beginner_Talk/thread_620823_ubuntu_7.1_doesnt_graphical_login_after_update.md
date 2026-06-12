---
title: "ubuntu 7.1 doesnt graphical login after update"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by vicky.irobot on 2007-11-23
I installed the latest Ubuntu yesterday and it was working amazingly cool until I updated it. It downloaded 82 packages and updated the machine. It did restart and after that I got this wierd screen saying that it can't start the x-server and there was a option for configure.

Clicked on that and did setup of the graphic card to my nvidia 7 series and monitor to my Samsung. Did the resolution setup and did a restart. After that the graphical login prompt was up.

Now from here the problem started. I keyed in my user name and password and after that the screen went orange which usually happens when you are logging in and it remained that way for quite some time. Suspicious that my login startup scripts might have got messed up I logged in with a different user name and found the same problem happen with that user name.

I switched to command mode login by using keys ctrl + alt + f1 and was able to do a command prompt login.

Can any one please help me with this issue.

Isn't there a user by name root in Ubuntu? I find that everything is getting done using sudo.

---

### Post by kpkeerthi on 2007-11-23
It could be one of your startup programs you had in session properties. From command line can you post what you get by running
```

ls ~/.config/autostart

```

---

### Post by vicky.irobot on 2007-11-23
I need to try that when I go home.

I checked my friend's machine for autostart file but didn't find it. 

There is this .config directory under which there are other directories and files  but no autostart file.

I need to check my system when I go home.

---

### Post by vicky.irobot on 2007-11-23
There is nothing by name autostart under .config under my home.

I have tried logging as other uses in my machine and the same problem is for others as well.

My login username and password get accepted and it tries to login and gets hung. Itz not my system that gets hung here but it is the login.

This started after I updated the machine with some 88 packages that it picked up during autoupdate

---

### Post by vicky.irobot on 2007-11-26
Since there was no solution found, lemme close this post.

After update of around 88 packages which was like 99Meg my graphical login didn't work. It asked for me to configure the hardware graphics card and Monitor. After doing that I my graphic login session was up I guess you call it GDM.

After entering the username and password it got accepted and nothing happened. The screen which was showing username went to the next stage of login where you see a orange window followed by login happenning but for some reason it was hung over there.

Mailed the mailing list for any solutions, got a few but none helped.

Finally concluded that I better not update my Ubuntu else I will have to reinstall the entire thing.

So thatz it I had to reinstall the entire thing and no more updates from here on. Sad this wasn't there for me when using SuSE. I didn't remember once after updating my Nvidia graphics driver I couldn't get my graphics login up but I did get some info on SuSE wiki and that fixed the issue for me.

FINALLY....DO WHAT EVER YOU WANT BUT DON'T UPDATE YOUR UBUNTU :mad:

---

### Post by Slakker on 2007-11-26
So you could log in to your graphical desktop environment through the command prompt login, or could you only log in to the text based environment?

Sounds like an x-server problem to me...try the following from a terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

Follow the on-screen instructions to complete it, and things should be up and running again.  I see that you've already reinstalled, but should you run into this problem updating Ubuntu again (and you should update ubuntu) this might fix it.

---

### Post by vicky.irobot on 2007-11-26
I could login using the command prompt. But not using the graphical login.

The graphical login window does come up.

Lemme try your suggestion when I go home today. I need to restart my update and recreate the problem scenario. Would be more than happy if things work.

I had similar problem when I had tried Mandrake. Updating the machine caused the graphical login to not come up, no support then so switched to other distribution.

Hope the same doesn't happen here since I find Ubuntu is quite cool and very light on my machine.

---

### Post by vicky.irobot on 2007-11-26
I think I found what was causing the problem

I reinstalled my machine and started updated one after the other

Finally only these two packages are left off linux-restricted-modules-2 6 22 14 generic
linux-restricted modules common and they seem to do something fishy by removing the nvidia driver module

Did any one install these packages with nvidia driver already running in the current machine?

---

