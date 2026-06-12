---
title: "[SOLVED] Install Compiz Fusion on Ubuntu Studio"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by H3!ST on 2008-02-07
Absolute beginner. I just installed Ubuntu Studio on my Dell Latitude D620 for the second time. I tried to install Compiz Fusion on it before but end up with a white screen. I want to do it right this time. Can anyone help?

---

### Post by wolfen69 on 2008-02-07
system>admin>restricted drivers manager. install your video driver. reboot.
```
sudo apt-get install compizconfig-settings-manager
```
system>preferences>appearance>visual effects>extra/custom

---

### Post by H3!ST on 2008-02-07
Where is that? This is what comes up.

[[IMG]http://img167.imageshack.us/img167/6296/screenshotbt4.th.png[/IMG]](http://img167.imageshack.us/my.php?image=screenshotbt4.png)

---

### Post by H3!ST on 2008-02-07
Also, do I need to update?

---

### Post by kesman on 2008-02-07
Do the normal updates first, all of them.

---

### Post by H3!ST on 2008-02-07
Now what?

---

### Post by kesman on 2008-02-07
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
Install ENVY and with it, install the newest drivers for your nvidia card. Then try again running visual effects.

---

### Post by H3!ST on 2008-02-07
I think I have an Intel card. Is that a problem?

---

### Post by kesman on 2008-02-07
Oh sorry for that, I read trough the Dell site a bit too fast.
Do you have direct rendering on? You can check that with
```

glxinfo | grep rendering

```
in terminal.

---

### Post by H3!ST on 2008-02-07
Yes.

---

### Post by kesman on 2008-02-07
And it still goes all white when you go to system -> preferences -> appearance -> visual effects and set it to something else than "none" ?

---

### Post by H3!ST on 2008-02-07
All I have done so far is update cause I can't find that menu the to install the drivers,

---

### Post by H3!ST on 2008-02-07
I tried what you said and this came up: Failed to execute child process "compiz" (No such file or directory)

---

### Post by kesman on 2008-02-07
Don't worry about the drivers anymore, they seem to be working just fine. Now the problem is that you don't seem to have compiz installed at all. Go to system -> administration -> software sources and make sure you have all the souces enabled.

---

### Post by H3!ST on 2008-02-07
I think I did it right. what's the next step?

---

### Post by kesman on 2008-02-07
So you enabled the sources? Did you check every tab in there? Now you should check for updates in the update manager under administration. If this doesn't update your compiz, then go to applications -> add/remove and search for compiz and install the relevant packages

---

### Post by H3!ST on 2008-02-07
So I downloaded the compiz manager thing. Restart now, or do I now do the following?

> **wolfen69 said:**
> system>admin>restricted drivers manager. install your video driver. reboot.
```
sudo apt-get install compizconfig-settings-manager
```
system>preferences>appearance>visual effects>extra/custom

---

### Post by H3!ST on 2008-02-07
Do I also need to reconfigure my gxl and xserver? I read that somewhere and I'm not sure.

---

### Post by kesman on 2008-02-07
I don't know much about intel graphics card, and also, ubuntu studio is some 3rd party version of ubuntu, I suggest you to use the default ubuntu and install the needed multimedia software after you got it up and running.

---

### Post by H3!ST on 2008-02-07
Nvm, I got it running. Thank you.

---

### Post by kesman on 2008-02-07
Please, let me know what you did so everyone browsing this forums might get help from your experiences.

---

### Post by H3!ST on 2008-02-07
I used the Synaptic Package Manager under *System-->Administration-->Synaptic Package Manager*. I typed "Compiz" in the search bar and downloaded everything related except for the KDE package.

---

