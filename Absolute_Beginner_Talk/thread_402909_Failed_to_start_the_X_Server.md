---
title: "Failed to start the X Server"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Dragon665 on 2007-04-06
Hi all,

I installed using the alternat version of Ubuntu and after finishing the installation it restarted as I preume it should and it came up with an error stating "Failed to start the X Server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X Server output to diagnose the poblem?" If I press 'No' another message comes up saying "The X Server is now disabled. Restart GDM when it is configured correctly."
Can someone help me?

Thanks

Roy

---

### Post by Happy_Man on 2007-04-06
```

sudo aptitude install ubuntu-desktop

```

---

### Post by Dragon665 on 2007-04-06
Sorry to be a n00b, but where, how and when do I type that?

Thanks

---

### Post by Happy_Man on 2007-04-06
Well, after it gives you the Fail message, does it drop to a text-only  login, or do you see just a blinking cursor?

---

### Post by Dragon665 on 2007-04-06
The screen goes black with a blinking cursor up in the top left corner, and when I tpye anything in and press enter it just prints it onscreen and goes onto the next line and does nothing?

---

### Post by Dragon665 on 2007-04-06
Bump

---

### Post by Dragon665 on 2007-04-06
Bump. Can someone help me, Im really eager to get into Linux!

---

### Post by sessine on 2007-04-06
> **Dragon665 said:**
> Hi all,

I installed using the alternat version of Ubuntu and after finishing the installation it restarted as I preume it should and it came up with an error stating "Failed to start the X Server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X Server output to diagnose the poblem?" If I press 'No' another message comes up saying "The X Server is now disabled. Restart GDM when it is configured correctly."
Can someone help me?

Thanks

Roy

what happens if you pres 'yes' to see the log?

---

### Post by Razorback on 2007-04-06
You will need to correct your xorg.conf file for your video card.  What vidoe card are you using?

You can hit Ctrl-Alt-F1 at the prompt and configure X by typing:

sudo dpkg-reconfigure xserver-xorg

---

### Post by Dragon665 on 2007-04-06
I have an nvidia 8800 gts 640 mb. Im very new to this and it seems to be a pain. Im wndering wether its worth it? Whats involved with editing it bearing in mind i know nothing what so ever of linux?

Thanks

Roy

---

### Post by Happy_Man on 2007-04-06
It asks you a few questions like what's your graphics card and such. You'll know. Don't worry. :)

---

### Post by Dragon665 on 2007-04-06
Right, i tried what you said, went through all of the options until it put me back to the console, then i restarted and it gave me the same error. What now?

Thanks

Roy

---

### Post by Dragon665 on 2007-04-06
bump again

---

### Post by Dragon665 on 2007-04-06
I'm guessing nobody can help me with this problem?

Can any body recommend another good linux version?

---

### Post by Dragon665 on 2007-04-06
bump

---

### Post by Dragon665 on 2007-04-06
HEEEEELLLLLLLLLLOOOOOOOO! 

CAN ANY 1 HERE ME!!!???!!! Im going to end up not bothering soon, i keep seeing people answering to other posts and mine keeps going down the list, can no one help me?

---

### Post by confused57 on 2007-04-06
I believe from reading other posts, that the "nv" driver doesn't work with your card...you'll need to get to a console, then enter the "sudo dpkg-reconfigure xserver-xorg" command & change the driver to "vesa"...once you can get to a GUI, you can download the "nvidia" drivers for your card.

I'll see if I can find the links for using envy, which will automatically install the correct drivers for you.

In a console, you can also do it manually:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf
```

scroll down to the section for video driver & change the driver to "vesa", with the quotes.
ctrl+x, y, enter...this will save the change

then try 
```
startx
```
or
```
sudo /etc/init.d/gdm start
```

Added:  Found the thread for your video card:
[http://ubuntuforums.org/showthread.php?t=376483&highlight=nvidia+8800+gts](http://ubuntuforums.org/showthread.php?t=376483&highlight=nvidia+8800+gts)

---

### Post by Dragon665 on 2007-04-06
i feel like suicde

---

### Post by Razorback on 2007-04-06
When you configured X server what video did you try?

---

### Post by Dragon665 on 2007-04-06
AT LAST! Thanks very much, all i needed to do was change it to vesa. Although performance is very slow in ubuntu. Right onto next n00b question, how and where do i get proper drivers.

Roy

---

### Post by confused57 on 2007-04-06
> **Dragon665 said:**
> AT LAST! Thanks very much, all i needed to do was change it to vesa. Although performance is very slow in ubuntu. Right onto next n00b question, how and where do i get proper drivers.

Roy

Here's the link to the Envy script that automatically installs nvidia(or ATI) drivers:
[http://www.albertomilone.com/latest_nvidia_udsf_edgy.html](http://www.albertomilone.com/latest_nvidia_udsf_edgy.html)
I've never installed the nvidia drivers, so I can't personally help you with doing so.

Once you get your "nvidia" drivers installed & working, be sure not to update the kernel through automatic updates until you read the section about how to update the driver for the newer kernel...

---

