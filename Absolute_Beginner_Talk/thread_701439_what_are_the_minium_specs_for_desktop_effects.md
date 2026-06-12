---
title: "what are the minium specs for desktop effects"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by divindavid on 2008-02-19
hello i installed ubuntu 7.10 on my friends computer what is a compaq presario. i was wondering what the minum specs are for desktop effects. this computer has a 20gig HDD 1.20 GHz  intel celeron processor 
and 512mb or DDR1 RAM with a 11meg video card and i cant run desktop effects. if i upgrade to a Diablotek Radeon 7500 Video Card - 64MB DDR video card. would i be able to basic desktop effects.\



David.

---

### Post by divindavid on 2008-02-19
does any one know

---

### Post by philinux on 2008-02-19
Scroll down this page.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by SunnyRabbiera on 2008-02-19
Your specs should do, though if you can get a bit more memory then do so.

---

### Post by KIAaze on 2008-02-19
I have a Compaq Presario 2500 with 512 MB RAM and an ATI IGP345 M video card with 64 MB shared memory.
Compiz work well on it, but only now that I upgraded to Hardy.
I had a lot of problems with the ATI driver. :/

So, your specs will certainly be able to handle compiz theoretically, however you might have problems with the driver...

Note:
I had Beryl+AiGLX working about a year ago on Debian. So even if the default driver doesn't work for you, you might be able to get desktop effects to work by hacking around if you're motivated.

---

### Post by divindavid on 2008-02-19
it says desktop effects could not be enabled.
is it my RAM or my Video card

---

### Post by divindavid on 2008-02-19
I'm getting my wireless card today

---

### Post by KIAaze on 2008-02-21
Before buying hardware always make sure it works on GNU/Linux.

> is it my RAM or my Video card ?
Probably the video card.
512 MB of RAM is enough for desktop effects.
Like I said, it might be a problem with the driver.
Is the "Diablotek Radeon 7500 Video Card" from ATI?

One thing you can easily check is if direct rendering works.
Run this command in a terminal:
```
glxinfo | grep direct
```
If it returns ```
direct rendering: Yes
``` that means direct rendering is ok, which means all kinds of 2D/3D games will run well.
Unfortunately it doesn't mean that compiz will work, but if you don't have direct rendering, compiz certainly won't work as far as I know.

If you get a "command not found" error, you have to install glxinfo first by doing:
```
sudo apt-get install mesa-utils
```

You can also run "glxgears" to see the performances of your pc.

But to get compiz working, the best thing would be to go ask on the compiz forums. They might have a better idea of how to solve the problem.
[http://forum.compiz-fusion.org/](http://forum.compiz-fusion.org/)

You should also have a look at the compiz-fusion wiki:
[http://wiki.compiz-fusion.org/](http://wiki.compiz-fusion.org/)

Otherwise, you could try upgrading to hardy, but I wouldn't recommend it unless you are already very experienced with GNU/Linux and don't mind having sudden bugs & problems, like some programs not working anymore or crashing.

It will come out on April 24th 2008, so you can wait and hope it will work then...

If you don't want to wait and don't want to hack around to get it working, you could always try other user-friendly distros like Sabayon or openSUSE.

> I'm getting my wireless card today 
I would recommend getting one with an Atheros chipset. That's what I did and it worked out of the box.

Here are some compatibility lists you should look at before buying hardware:
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)
[http://www.linuxquestions.org/hcl/](http://www.linuxquestions.org/hcl/)
[http://www.linuxcompatible.org/compatibility.html](http://www.linuxcompatible.org/compatibility.html)
[http://www.google.com/search?q=linux+compatibility&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=linux+compatibility&ie=UTF-8&oe=UTF-8)

Tip:
If you want a webcam that works with skype, look at this list:
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

PS:
I managed to get the conexant 56k modem to work on my presario, so if you have the same modem, here's how to get it to work:
[http://archives.linmodems.org/28296](http://archives.linmodems.org/28296)
If you have any problems, look at this page:
[http://www.linmodems.org/](http://www.linmodems.org/)
It's also helpful if you want to connect over a USB modem.

---

### Post by Ojkar on 2008-05-05
Hello KIAaze,

I could say I'm a new linux user.. I used to run suse and red hat long time ago, and now I'm catching up with linux through these wonderful distros.

I've tried a few of them under virtual machines, but the one I'm running now on my laptop (Compaq presario 2500, now you con imagine why I'm writing you) is Opengeu which I upgraded to ubuntu 8.04 last week. Everything works fine (considering e17 is still a beta), itask-ng, wireless network, samba, etc..

I'm trying to run compiz, and I'm finding lots of trouble. I hoped you could help me...

First of all, I'm finding difficult to find out which is the suitable radeon driver for my IGP 345... I've looked for many many places without a definite answer.

I installed the latest version 8.42,it didn't work out and I had to come back to mesa driver. I've read several threads that talk about compiling the kernel and that's something I've never done before.

Please, could you illuminate me??

Many thanks

---

### Post by KIAaze on 2008-05-06
They blacklisted ATI cards in 8.04 for some reason.
See here for more info and how to bypass the blacklisting: [http://ubuntuforums.org/showpost.php?p=4690955&postcount=8](http://ubuntuforums.org/showpost.php?p=4690955&postcount=8)

I hope this solves it for you.
I attached my current xorg.conf and the output of glxinfo to this post.

It seems I'm currently using the open-source driver (jockey-gtk shows no restricted drivers) with fglrx (server glx vendor string: SGI
).

---

### Post by Ojkar on 2008-05-06
Thank you so much...

I'll try it out this very afternoon... I hope I can tell everything's working.

See you.

---

### Post by Ojkar on 2008-05-06
Hi again,

I tried to work-around the Ati cards check, and it didn't work. It really does not check it and continues but there are another error message, look:

/usr/bin$ compiz --replace
Checking for Xgl: not present. 
Found laptop using ati driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Another window manager is already running on screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Advertencia del gestor de ventanas: La ventana 0 en la pantalla «:0.0» ya tiene un gestor de ventanas

I can't think of which window manager is running...

I have the same xorg.conf and glxinfo that you have..

I think this is going to take a bit longer...

Salu2

---

### Post by KIAaze on 2008-05-06
Well, then I really don't know because here's the output I get:
```
[11][~]$  export SKIP_CHECKS=yes
[12][~]$  compiz --replace
Checking for Xgl: not present.
Found laptop using ati driver.
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

I'm using Gnome and already upgraded to Intrepid. But I remember Compiz working with Gutsy/Hardy. So I really don't know...
Are you still using Enlightment (since you switched from opengeu)? (altough Desktop environment!=window manager=metacity)

P.S: Maybe we should start a new thread on this...

---

### Post by Ojkar on 2008-05-07
Hello,

You're damn right!... I found out e17 is a window manager and it's not compatible with compiz, so I created a new user, loaded the dri module, added 0666 at the dri section to allow all users to load dri and started ubuntu on Gnome, and... Al fin!!! Everything works really fast.

Thank you very much, you've been very helpful. Gracias.

P.S.: I tried to awake the laptop after getting it to sleep, and it happened the same.... But while starting the system I saw and error loading the ACPM module... I'm intrigued... If I find out something I'll let you know.. Saludos.

---

