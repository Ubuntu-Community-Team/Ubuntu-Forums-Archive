---
title: "Udated driver to nvidia, now X won't start, complete newbie."
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by kschelde on 2007-02-19
I like to warn that I have no experience in linux or programming at all, so if it to hard to walk me through this holding my hand all the way, and telling me explicit what to do, please say so.

I have been running ubuntu edgy, now for a month, liking it and getting used to the different interface, then I tried to installe second life, and found out I had to install specefic drivers to my nvidia gforce (Can't remember specifications). I found drivers in the synaptic package manager, where I have access to all respositories. I installed , rebooted and now I start up in what i know as "DOS" I would like to get back to "normal" Anybody understanding my question?:confused: 

I currently am writing from my laptop.

---

### Post by Bachstelze on 2007-02-19
All you need to know about installing the nvidia drivers is [here](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia).

Good luck, If you are stuck somewhere, don't hesitate to ask :)

---

### Post by Repent on 2007-02-19
Here give this a try,  [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717) , it's really easy and fast.

---

### Post by keith11 on 2007-02-19
> **kschelde said:**
> I like to warn that I have no experience in linux or programming at all, so if it to hard to walk me through this holding my hand all the way, and telling me explicit what to do, please say so.

I have been running ubuntu edgy, now for a month, liking it and getting used to the different interface, then I tried to installe second life, and found out I had to install specefic drivers to my nvidia gforce (Can't remember specifications). I found drivers in the synaptic package manager, where I have access to all respositories. I installed , rebooted and now I start up in what i know as "DOS" I would like to get back to "normal" Anybody understanding my question?:confused: 

I currently am writing from my laptop.

If I am not wrong, there is a problem in your xorg.conf file which has the information about your nvidia card's configuration. You should read the document hymntolife (the person who posted before I did) pointed you to and try finding something like "xorg.conf nvidia ubuntu/linux" in google and hopefully you will find a solution to your problem. Good luck!

---

### Post by kschelde on 2007-02-19
My problem is I did use that link before, but after I rebooted I can only access the system like a terminal, I know my knowlegde is very limited, but the screen is black with white writing, I can manage to log in but do not know which commands to write to make everthing "normal" again. 

I have triede hitting esc  before loading but get the same problem with fault screen about X is not working, no matter which I chose.

---

### Post by Luk0r on 2007-02-19
I recommend that script mentioned above too (envy).  It's the best way to get nvidia drivers working on Ubuntu in my opinion.

---

### Post by r4ik on 2007-02-19
> **Repent said:**
> Here give this a try,  [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717) , it's really easy and fast.


Please link to tseliot's homepage to get Envy.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Bachstelze on 2007-02-19
You certainly missed something. To get back to the nv drivers, do this :

```
sudo nano /etc/X11/xorg.conf
```

will open the X config file in the nano text editor. You should have a line like this :

```
    Driver         "nvidia"
```

Change "nvidia" to "nv". Then save the file (Ctrl+O, Enter to confirm), exit nano (Ctrl+X) and try restarting your X :

```
sudo /etc/init.d/?dm restart
```

---

### Post by Repent on 2007-02-19
OK I tried using Envy from the download page but it didn't work for me. I was ready to give up and call it a lost cause but then I found this web page and it worked, it still installs Envy but first it purged my system removing the copy of Envy that didn't work for what ever reason, all I know is this works.

---

### Post by kschelde on 2007-02-19
Repent>> The link you gave me worked. Thank you very much. 

Hymntolife>> thank you for trying to take me through this step by step.

It really helps me to like Ubuntu even more that you all, are so helpfull, even to dorks like me. *S*

---

