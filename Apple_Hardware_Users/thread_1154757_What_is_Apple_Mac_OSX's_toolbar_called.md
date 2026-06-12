---
title: "What is Apple Mac OSX's toolbar called?"
date: 2009-05-10
forum: Apple Hardware Users
---

### Post by isa.k on 2009-05-10
Hello friends,

I wanted to know what the toolbar at the bottom of Apple Machines are called?

Please see the following image:

[[IMG]http://img136.imageshack.us/img136/1580/macosxtoolbar.gif[/IMG]](http://img136.imageshack.us/my.php?image=macosxtoolbar.gif)

I have "see-through"ed down the appearance of everything else, and drawn the emphasis on the actual toolbar.

Image from [http://sephyleader.deviantart.com/art/The-Simpsons-Mac-OS-X-Desktop-72511342](http://sephyleader.deviantart.com/art/The-Simpsons-Mac-OS-X-Desktop-72511342)

I was wondering if there was an Ubuntu equivalent, and if so, what procedure would one have to go through to get it working on a 64 bit Jaunty Ubuntu?


Kind Regards,

**isa**

---

### Post by ad_267 on 2009-05-10
That's called a dock. There are quite a few equivalents for Ubuntu actually. AWN (Avant Window Navigator) seems quite popular, there's also Cairo dock and a few others. Docky is a more recent one which is pretty good too and is a theme for Gnome-Do.

There's instructions for installing AWN at [http://wiki.awn-project.org/Installation:Ubuntu#PPA](http://wiki.awn-project.org/Installation:Ubuntu#PPA)

---

### Post by isa.k on 2009-05-10
Thank you for that **ad_267** :)

I followed the link's instructions upto here:

> 5. For each line from the gray box on the PPA page, copy it, click on the "Add" button in "Software Sources", paste the line into the new dialog box, and press OK.

Problem is, I am in [**this page**]("https://launchpad.net/~awn-testing/+archive/ppa") and can not see a "gray box"... Where should I be looking?

---

### Post by konqueror7 on 2009-05-10
```

deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/awn-testing/ppa/ubuntu jaunty main

```

these are from the 'gray' box...

or if you just want to experiment first and don't want the latest version, you could just do a,
```
sudo apt-get install awn-manager
```

---

### Post by ad_267 on 2009-05-10
Yeah if you're using Jaunty then you're probably fine installing AWN from the Ubuntu repositories, there won't be a huge difference in the versions available. Sorry I should have just said that first.

You can also install gnome-do from the repositories in the same way and try out docky.

---

### Post by gjoellee on 2009-05-10
It is called a "dock". You can get many different docks in Linux:
-Avant Window Navigator (AWN)
-Cairo Dock
-Docky
-And many more!

---

### Post by isa.k on 2009-05-10
This thread is one of the most helpful I have started :D

Thank you to all the wonderful contributors.

I just went through the instructions in [**the link**]("http://wiki.awn-project.org/Installation:Ubuntu#PPA") in [**post #2**]("http://ubuntuforums.org/showthread.php?p=7250023#post7250023"), and just got GNOME Do working :D

I am just realising how huge and ermm... versatile?/powerful/awesome Linux is!

I just installed Jaunty yesterday, and have had some problems, but I do not hold that against Linux, rather, my lack of knowledge...

This is a huge learning curb for me!

Now, I wonder what to do next?

I looked in Synaptic Package Manager for AWN files(?) and found the following:

[[IMG]http://img14.imageshack.us/img14/2333/screenshotsynapticpacka.png[/IMG]](http://img14.imageshack.us/my.php?image=screenshotsynapticpacka.png)

At the moment, I am lost... officially... and wonder what to do now?

Again, to all you that helped, thanking you very much :)


**isa**

---

### Post by isa.k on 2009-05-10
No one?

Just when I mention how this thread has been the most helpful... everyone seemed to disappear! LoL :D

---

### Post by konqueror7 on 2009-05-10
just install the 'awn-manager' package, all its dependencies will just be automatically installed...this will get you the basic awn dock and applets, the other packages you see are just extra applets, so no worries...

oh, and before launching avant, try to remove your lower panel first,  ad experience the my panel just froze...

oh, and sorry for the late reply, different timezones...:P

---

### Post by isa.k on 2009-05-10
OK, how to install it?

I have been tinkering around since yesterday, and now when I looked at Synaptic, it (awn-manager) has a green square next to it (meaning it is already installed?).

So now I would need to learn how I get the dock to appear...

If possible, in spoon-fed form :oops: plskthx :D

---

### Post by konqueror7 on 2009-05-10
well, you just got to check the tickbox, then click 'Apply' above...it will install it...

or you may want to do it via the terminal, open the terminal and issue the following,
```
sudo apt-get install awn-manager
```

after the installation you will see it in  you applications menu, in the accessories section...

here's a [guide]("http://www.simplehelp.net/2007/05/31/how-to-install-setup-and-use-avant-window-navigator-awn-in-ubuntu-feisty/") to further help you in avant...

---

### Post by isa.k on 2009-05-11
> . . .after the installation you will see it in you applications menu, in the accessories section...

Bingo :D Thank you so much :)

---

### Post by isa.k on 2009-05-11
How would I get to permanently dock the programs into the dock?

Or would I need a different dock program for that?

---

### Post by konqueror7 on 2009-05-11
you can apps/launchers in the 'Launchers' section in the dock preferences...or you can just directly drag launchers into the dock...

---

### Post by isa.k on 2009-05-12
> **konqueror7 said:**
> you can apps/launchers in the 'Launchers' section in the dock preferences...or you can just directly drag launchers into the dock...
LoL!

If only I knew where they are located, no problems! :D

I really am new at this game :oops:

---

### Post by konqueror7 on 2009-05-12
haha... forgot to add 'add'...:lolflag:

---

### Post by isa.k on 2009-05-12
> **konqueror7 said:**
> haha... forgot to add 'add'...:lolflag:
LoL :D

Nah, I got that bit fine... but where do I add the programs installed on my box from?

In Windows, it would be located in (considering we use a default setup of windows):

C:/Program Files/**PROGRAM FOLDER**/*.*exe file**

Not sure where the programs are in Ubuntu though?

---

### Post by ad_267 on 2009-05-12
You can drag them straight from your menu or your desktop.

---

