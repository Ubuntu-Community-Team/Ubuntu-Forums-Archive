---
title: "I broke Compiz fusion"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by BackBack on 2008-02-08
I wanted to get the Cube effect working, so I found a tutorial and installed Compiz-Fusion, but now none of the visual effects work.  In the visual effects tab I still have none, normal, and extra, and now the custom one is there; however, regardless of which one I pick the effects no longer work.  I can only have 2x1 worktables, even if I select more.  I've tried compiz --replace, but that doesn't help me any, nor does restarting the computer.  The nVidia driver is installed and in use, but still no go.  Any help?

---

### Post by randy78 on 2008-02-08
sudo apt-get install compizconfig-settings-manager

---

### Post by kpkeerthi on 2008-02-08
Compiz is installed by default in ubuntu. You just have to enable it from System -> Preference -> Appearance -> Visual Effects.

You need ccsm only if you would like to turn on/off more effects or plugins.

---

### Post by BackBack on 2008-02-08
I was told that I need to install Compiz-Fusion because just Compiz is out of date (don't know if it's true or not), so I did.  Now it doesn't work.  The compizconfig-settings-manager is already at the newest version, and as I stated earlier, the Visual Effects are already enabled.

---

### Post by kpkeerthi on 2008-02-08
By Compiz, I actually meant compiz fusion. The compositor is now called Compiz and there are **optional** compiz-fusion plugins. Anyway, compiz fusion :) is already preinstalled in ubuntu.

---

### Post by BackBack on 2008-02-08
Ah, well that makes sense. So would it be a bad plugin that in installed that I should uninstal, or is there a fix for it?
```
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```
I also get the following message when trying to run Compiz.  Any help?

---

### Post by kpkeerthi on 2008-02-08
Mind posting the link of the tutorial you followed? I'll take a look and see what could have possibly gone wrong.

---

### Post by BackBack on 2008-02-08
I tried this one here [http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)

---

### Post by kpkeerthi on 2008-02-08
> 
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

That repository given in that site is **feisty**'s. Are you running **gutsy** now?

---

### Post by BackBack on 2008-02-08
... Yeah, I am.  I feel dumb for not catching that :/ Is there a way to undo that, or simply return to the default settings like when Ubuntu was installed?

---

### Post by kpkeerthi on 2008-02-08
Disable Visual effects from System -> Preference -> Appearance
Then....

1. Edit apt source:

```

gksudo gedit /etc/apt/sources.list

```

2. Find and delete the below lines from the file
```

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

```

3. Save and exit

4. Lets remove the bad packages you installed from feisty repository
```

sudo apt-get remove compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf

```

5. Clean up residues
```

sudo apt-get clean

```

6. Look for any hidden (dot files) that begin with .compiz in your home directory and delete it. Also delete the compiz folder from $HOME/config folder, if any.

7. Now upgrade the packages from gutsy repository
```

sudo apt-get update
sudo apt-get -y upgrade
sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf

```

8. Reboot your machine (clean state)
9. Enable Visual Effects
10. Follow this [guide]("http://ubuntu-tutorials.com/2007/10/04/compiz-fusion-on-ubuntu-710-gutsy-gibbin/") to customize compiz.

---

### Post by BackBack on 2008-02-08
Well many thanks, that worked great.  Only thing is, I still can't have more than 2 workspaces, so how would I fix that? One question though, how do you figure out how to fix it? If it happens again, I'd like to know where the solution came from so I could learn from it, rather than running back here.

---

### Post by kpkeerthi on 2008-02-08
Glad it worked for you.
> 
One question though, how do you figure out how to fix it? If it happens again,

We just noticed that the repo was wrong. So I wrote down the steps to reverse whatever you installed from that repository. :)

---

### Post by BackBack on 2008-02-08
Ah, well thank you. I still feel stupid for not noticing that, especially because I've gone through the entire thing and read it before doing anything :/  Do you have any suggestions about the workspace size, by any chance?

---

### Post by kpkeerthi on 2008-02-08
Not in front of linux at the moment. I guess you can specify workspaces in General Option -> Desktop Size in Compiz Config Settings Manager.

---

### Post by kpkeerthi on 2008-02-08
Yes it is. Just found it here [http://wiki.compiz-fusion.org/GeneralOptions#head-4652144e7ab9707a27254cf1fc3b2a66c32bc5e2](http://wiki.compiz-fusion.org/GeneralOptions#head-4652144e7ab9707a27254cf1fc3b2a66c32bc5e2)

---

### Post by BackBack on 2008-02-08
Ah, that actually did it.  I'm not sure  why it didn't work when I right-clicked > preference, and select the size I wanted it, but your way did the trick.  Thanks a lot

---

### Post by kpkeerthi on 2008-02-08
Can you mark the thread the "solved" for the benefit of others? Thanks.

---

