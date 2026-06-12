---
title: "Uninstall FireFox"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by maxM on 2006-12-27
Hi, I'm a big Opera fan and was wondering how I can delete FF from my Ubuntu Edgy? I can find How To Install Opera, but no one have described how to uninstall FF ;) 
And are there standard codes to uninstall programs (terminal), or do they change?

No offense to all of you who loves FF

Regards maxM

---

### Post by nhandler on 2006-12-27
You can use the following command to uninstall firefox.
```
sudo apt-get remove firefox
```

You use apt-get remove the same way you use apt-get install. One just removes the the package and the other installs the package.

Another option is to use synaptic. This will give you a GUI to remove any package you want.

As for the code changing, all that changes is the name of the package at the end.

---

### Post by tuxcantfly on 2006-12-27
if you like the terminal:

sudo dpkg --purge firefox

if you like the gui:

system -> administration -> synaptic package manager

then just find firefox and right click "completely remove", then apply

---

### Post by Sef on 2006-12-27
It would be best to keep Firefox on there as a back up in case Opera cannot connect at some point to the net.   Sometimes upgrades can mess up a browser.

---

### Post by nhandler on 2006-12-27
> **Sef said:**
> It would be best to keep Firefox on there as a back up in case Opera cannot connect at some point to the net.   Sometimes upgrades can mess up a browser.

I would also keep firefox on your computer. Some sites require it. If you are removing it to save space, at least install lynx. Lynx is a console based web browser. This way, if you mess something up, you will still have internet. Ubuntu I believe comes with w3m, which is another console web browser. I personally prefer lynx over it, but I also prefer Firefox over Opera :)  In the end, it is all up to you.

---

### Post by maxM on 2006-12-27
Ok, but now I have an other problem. 
At Ubuntuguide.org they say that on amd64-bit version I only need to [replace any i386 tag with amd64](http://ubuntuguide.org/wiki/Ubuntu_Edgy#General_Notes). But this doesn't work out with the [HowTo install Opera.](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Opera_web_browser) 
I get the message that

```
jd@jd-dapper:~$ sudo dpkg -i opera_9.02-20060919.6-shared-qt_en_amd64.deb
dpkg: error processing opera_9.02-20060919.6-shared-qt_en_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 opera_9.02-20060919.6-shared-qt_en_amd64.deb
```

---

### Post by nhandler on 2006-12-27
That error could be caused by 2 things:

1) You did not cd into the appropriate directory before running that command. Unless the .deb file is located in the /home/YOURNAME folder, you need to type: cd FOLDERNAMEHERE, before running the command.

2) The .deb file is not called: opera_9.02-20060919.6-shared-qt_en_amd64.deb. If the file is really called: opera_9.02-20060919.6-shared-qt_en_i386.deb, you need to leave it that way in the command (otherwise, the computer doesn't know what file you are talking about).

---

### Post by maxM on 2006-12-27
sudo apt-get install opera  results in:
```
E: Couldn't find package opera
```

The 32-bit file got the right adress. Cause I get the message:
```
dpkg: error processing opera_9.02-20060919.6-shared-qt_en_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
```

Anyone knows what the right adress is for my amd64?

---

### Post by nhandler on 2006-12-27
> **maxM said:**
> sudo apt-get install opera  results in:
```
E: Couldn't find package opera
```

The 32-bit file got the right adress. Cause I get the message:
```
dpkg: error processing opera_9.02-20060919.6-shared-qt_en_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
```

Anyone knows what the right adress is for my amd64?

Try using this command:
```
sudo dpkg -i --force-architecture opera_9.02-20060919.6-shared-qt_en_i386.deb
```

I found that in this thread: [http://ubuntuforums.org/showthread.php?t=75940](http://ubuntuforums.org/showthread.php?t=75940)

---

### Post by mechanic on 2006-12-29
> **tuxcantfly said:**
> if you like the terminal:

sudo dpkg --purge firefox

if you like the gui:

system -> administration -> synaptic package manager

then just find firefox and right click "completely remove", then apply

Have you any idea how many packages depend on Firefox? Apt-get informs us that these packages will be removed if we try to remove FF:
"[I]The following packages will be REMOVED
  ekiga* firefox* firefox-gnome-support* gnome-app-install* liferea* liferea-mozilla*
  ubuntu-desktop* yelp*[/I]"

Looks like it's pretty well plumbed into the system!

Regds, mechanic.

---

