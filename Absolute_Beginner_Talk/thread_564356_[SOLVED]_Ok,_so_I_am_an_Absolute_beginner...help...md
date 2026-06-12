---
title: "[SOLVED] Ok, so I am an Absolute beginner...help.."
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by cjray03 on 2007-10-01
Ok, I am not an absolute beginner with computers...just Ubuntu...I love it, and I just built me a new machine...AMD X2 6000+ MSI K9N SLI Platinum MB..etc..etc...Anyways the install works great, I installed the 64 version of course. Anyways I went to nVidia and downloaded the drivers for 64bit 8600GT (my card) so I could get both of my monitors going and all...but even though I downloaded the file...its a .run file...I don't know how to get it to install...it says to type it in "sh" and so forth...but where do I type it in at? When I right click on it it gives me the option to "run with SH" but when I select it nothing happens... I know that this is probably a very novice question, but I really need the help...

-THANKS!

---

### Post by rug77 on 2007-10-01
You run commands in the terminal - it's like the windows CMD prompt.

You will probably need to type


SUDO SH ./(file-name-ending-.RUN)


The SUDO bit says 'run this command with admin (SuperUser actually) authorities'.

Should do the trick.

Matt

---

### Post by distroman on 2007-10-01
1. Either use envy it should install the drivers for you.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

2. Or follow the following howto.
[http://www.robdian.co.uk/content/view/56/](http://www.robdian.co.uk/content/view/56/)

gl

---

### Post by cjray03 on 2007-10-01
Envy worked out good, it installed the driver as it said it would. Now the problem I have is this....whenever I start the nVidia control panel and configure my multiple displays, I need to re-write my config and and restart my xserver...seems simple enough, but with the nVidia control panel whenever I go to modify the file it says "could not ...blah...blah...blah" anyways, I am sure that it is because of the permissions to the files...I am logged in as me and I am an administrator, but whenever I go to do a task it always asks for the password..I think this is a great feature...protects my settings and all, but I also think that because I don't have "carte blanche" administrator privileges that my nVidia control panel can't modify my config file, so in turn I can't save my config, and I can't actually set up my dual displays the way I like, because it requires a restart of the xserver, and of course without modifying the config file it just restarts back to default every time...

So I guess my next question is this...is there a way to modify the security settings to always allow me (while I am logged in as me) to append, delete or generally just modify files without going through all the hassles of entering and re-entering my password all the time? 

Thanks again!

---

### Post by jordanmthomas on 2007-10-01
> **rug77 said:**
>  it's like the windows CMD prompt.


BITE YOUR TONGUE YOUNG MAN

---

### Post by jordanmthomas on 2007-10-01
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

This might be what you're looking for as far as permissions.
```
gksudo nautilus
``` will open a browser window with root permissions.  Be careful with this.

If this solution isn't satisfactory, it is possible to have permission to do whatever you want whenever you want, but I wouldn't suggest it and so I'll leave you to find out how to do it (hint:  look up the /etc/sudoers file)

And finally, just run the nvidia control panel (whatever its command is) with gksudo in front of it.

---

### Post by dfreer on 2007-10-01
It's a glitch with the GUI shortcut for nvidia-settings, it needs to be run as root in order to write the configuration file. You can hit <Alt>+<F2>, which will bring up the "Run Application" screen. Type *gksudo nvidia-settings*, and then modify to your hearts content.
One thing you should always do before messing with your xorg.conf file, is backup the original. In Accessories > Terminal type:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
```

---

### Post by cjray03 on 2007-10-01
Hey, you guys are great! Everything is working fine now. Thanks!

---

