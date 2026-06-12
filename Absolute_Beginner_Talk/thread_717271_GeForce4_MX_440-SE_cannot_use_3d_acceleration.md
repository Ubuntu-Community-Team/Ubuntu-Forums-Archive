---
title: "GeForce4 MX 440-SE cannot use 3d acceleration"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-06
I recently needed help installing a driver for my Nvidia GeForce4 MX 440-SE. Here is a link to the thread in which I asked for help:

[http://ubuntuforums.org/showthread.php?t=711777](http://ubuntuforums.org/showthread.php?t=711777)

Within that thread I happened to come accross a link that gave specific instructions on how to install the driver I needed. The link to that is:

[http://ubuntuforums.org/showpost.php?p=4284483&postcount=8](http://ubuntuforums.org/showpost.php?p=4284483&postcount=8)

It turned out that, after I installed the driver, it would just hang during "Running local boot scripts (/etc/re.local). It turns out that I had to edit the xorg.conf for the driver and change the driver from "nvidia" to "nv" for it to boot my interface.

It worked, I was happy, I could see things. However, I still couldn't play any 3d games. I really didn't put too much thought into it, as I had a million other things to worry about. Well, while stumbleing around I happened to come accross:

Applications -> System -> Restricted Drivers Manager

I noticed that it said no proprietory drivers are in use on this system. Down below was the option to check a checkbox that would enable the NVIDIA accelerated graphics driver. When I checked it a second box popped up stating that it was necessary for 3d utilization.

Here is a screenshot of the window and the second window that popped up after I checked the box:

[IMG]http://www.geocities.com/lookin4busstop/MyScreenshot.jpg[/IMG]

After I press the enable driver button it then tells me that I will have to reboot the system for the new changes to take effect. That's understandable. So, I go ahead and reboot the computer only to have it hang in that spot that it used to hang whenever I had the other driver installed prior to changing "nvidia" to "nv". With that in mind, I decided to check the xorg.conf and sure enough, "nv" had changed back to "nvidia". So, I changed it back to "nv" and it booted up fine without any problems. However, after checking the Restricted Drivers Manager, I was right back to where I was. The box was unchecked and it said I didn't have the NVIDIA accelerated graphics driver in use. After all this I've begun to realize that when I change "nvidia" to "nv" I am basically changing from the accelerated graphics driver which does not work to an open source driver that does work. This epiphany was mainly given to me by slowly rereading a post that someone said in that last thread I had posted a link to.

jocko has posted:

```

I think the instructions on the page Whiffle gave are wrong:
To use the drivers installed with those instructions, you need to make sure that the driver in xorg.conf is "nvidia", not "nv".
"nv" is an open source driver which, as far as I know have very limited functionality.
```

My question is....

How can I get the accelerated graphics driver to work on MY computer?! ](*,) :sad:

PS: I came across this post that mentioned something that I'm not sure would fix it for me, in all actuality I don't think it would work for me as I am using an AGP card, but I suppose it couldn't hurt to try. Here is a link to that thread:

[http://ubuntuforums.org/showthread.php?t=65071](http://ubuntuforums.org/showthread.php?t=65071)

My brother now needs to use the computer for a moment so, I'm going to let him use it for a quick hour before I check to see if anyone's answered this thread and to test what the last link had suggested. Thanks to anyone who can help me.

PPS: I would quickly test that out now, if he wasn't freaking out that I told him I'd be 10 min 3 hours ago LOL!

---

### Post by sanddgroper on 2008-03-06
Hi
For that card you probably need the nvidia legacy driver from
synaptic.
You will need the propirety drivers repository selected in settings->repository->
Ubuntu software

Cheers
Sandy

---

### Post by whoscheesemine on 2008-03-06
> **sanddgroper said:**
> Hi
For that card you probably need the nvidia legacy driver from
synaptic.
You will need the propirety drivers repository selected in settings->repository->
Ubuntu software

Cheers
Sandy

Did you read the first thread I gave a link to? Just wondering before I do this cuz it seems kind of like what I did after I installed the driver from the NVIDIA website. I guess whenever they make a new driver they don't put it into the repository until the next Ubuntu release. So, the one in the repository is the 2nd newest, and is what I actually already have.

Also, "Settings -> Repository -> Ubuntu Software" isn't an option in Xubuntu, I'm not sure if I mentioned that I use Xubuntu.

---

### Post by sanddgroper on 2008-03-07
Hi
Ok do you have synaptic on your system.If you do enable the proprietry restricted
software repositories.Then select the nividia-glx-legacy package and install it.If
you dont have synaptic you will have to use apt.It would appear that if you use
any of the newer drivers (nvidia-glx and nvidia-glx-new)they dont work.

Cheers
Sandy

---

### Post by whoscheesemine on 2008-03-07
After installing the nividia-glx-legacy package. It still said that I wasn't using the NVIDIA accelerated graphics driver, just like in my picture. I also still couldn't get any games to work. (any good one's anyways). So, I figured I just needed to reboot my system. So, I rebooted, and still nothing, in fact everything looked just the same. From my past knowledge of WinBlows (yes i'm aware linux is different) after you install a new graphics driver, you almost always have to reconfigure your settings like screen ratio and such. I tried once again to play some games, but this game to no avail. I checked the restricted drivers manager, and once again the thing said that to use 3d acceleration I have to enable that driver, so this time I decided to have it display the terminal as it installed and I saw that it uninstalled the legacy driver, reinstalled the other one, and then after rebooting like I was prompted to do (which makes sense to me after you install a graphics driver) it hung at

Running local boot scipts (/etc/rc.local)

So, then I decided to get smart. I booted in recovery mode so I could see exactly why my computer wouldn't boot.

After being told it wouldn't boot, I typed in "startx" which I read somewhere to start the GUI, and I received the following error:

Error: API mismatch: the NVIDIA kernel module has the version 1.0-7185, but this X module has the version 1.0=9639. Please make sure that the kernel module and all NVIDIA driver components have the same version.

(EE) NVIDIA (0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA (0): that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA (0): that the NVIDIA device files have been created properly.
(EE) NVIDIA (0): Please consult the NVIDIA README for details
(EE) NVIDIA (0): ***Aborting***
(EE)                    Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
        after - requests (0 known processed) with - events remaining

After that I edited the /etc/X11/xorg.conf to where nvidia said nv instead of nvidia and it booted with out a problem. I suppose I'll keep trying different options untill I can figure this out. If I find something that works before someone answers me I'll post again.

---

### Post by sanddgroper on 2008-03-07
Hi
Ok the 7185 module is the nvidia-glx-legacy driver and the 9639 is the
nvidia-glx module.I guess the way to go would be to remove the 7185
module and install the 9639 one.I can not advise you how to do this.
But I think you might be close.

Cheers
Sandy

---

### Post by whoscheesemine on 2008-03-07
I just reinstalled the driver from the NVIDIA site via logging in a terminal session and it worked great. However, in some apps now the text is very small. Here is an example of some of those applications:

[IMG]http://www.geocities.com/lookin4busstop/MyScreenshot2.jpg[/IMG]

I'm not sure how to fix this, any ideas?

---

### Post by baracuda68 on 2008-03-07
so, despite the small text, do you now have the acceleration that you seek?
What resolution are you at right now?

---

### Post by whoscheesemine on 2008-03-07
1024 X 768 @ 55

Alien Arena works so I suppose that's all the acceleration I need.

---

### Post by whoscheesemine on 2008-03-08
After a reboot I've now discovered that I cannot get XFCE to boot untill I run the following two commands:

```
rmmod nvidia && modprobe nvidia

startx
```

but now every bit of text is as small as the examples I've previously shown

---

