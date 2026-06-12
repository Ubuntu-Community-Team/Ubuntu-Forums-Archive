---
title: "Screen not centered"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by nathanziarek on 2007-02-19
I'm sure this has come up before, but I simply couldn't find it anywhere.

Right now, I am simply booting from the CD. My screen, at the proper resolution (1024x768) is not centered -- it leaves black space on top and left and hangs off the bottom/right side of the screen.

This is an "all-in-one" type machine, and uses the Intel 82845G Graphics Chipset.

If I change the resolution to 800x600, it looks fine.

Suggestions?

Thanks!

Nate

---

### Post by m.musashi on 2007-02-19
Yeah, I've had that problem too. I don't really know what causes it as it's primarilly a monitor issue but it must somehow not get the right info. Anyway, on my monitor there is an auto adjust button. If I press that it blinks, flashes and moves around a bit and ends up fixed. See if your monitor has a similar option. It might be inside a menu. Once I do that it's fine - even after booting into windows and then back.

However, if there is some sort of problem with your resolution then this probably won't help.

---

### Post by nathanziarek on 2007-02-19
I've seen it before on Windows machines, and I've done the same thing. The problem here is that, in the All in one design, there aren't any buttons to press. Just a brightness knob. I've looked through all of the menus but was unable to find anything. Hopefully someone has the answer. Please?

:-) Nate

---

### Post by ubix on 2007-02-19
Graphic board and monitor negotiate the screen position through **Horizontal synch** and **Vertical refresh** ranges which are set in the **xorg.conf** file through parameters **HorizSync** and **VertRefresh**, and should look something like the following.```

	HorizSync	30-60
	VertRefresh	40-75
``` Find out (I suppose by googling) what are these ranges for your monitor and replace them the current settings with what you google'd. The more precise (the smaller the ranges the better; i.e. 26-50 is better than 30-60). [COLOR="Red"]**But be careful, if you guess this values and miss them by a critical value, you may burn your monitor**[/COLOR]. I did this once, and smoke came out of my new monitor :(

Alternatively you may try to run```
sudo dpkg-reconfigure xserver-xorg
```, which will ask you two or three dozen questions, suggesting answers, pay attention to the X server [COLOR="Blue"]**Driver**[/COLOR] setting for your graphic board/chipset and to **[COLOR="Blue"]Horizontal synch[/COLOR]** and **[COLOR="Blue"]Vertical refresh[/COLOR]** ranges. This will create a new **xorg.conf** file, hence it would be prudent to do the following:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup-123
``` before you start fiddling with this file. ;)

---

### Post by nathanziarek on 2007-02-19
I actually have access to this exact same machine running Windows XP. Does anyone know if I can find these values somewhere there?

Thanks,

Nate

---

### Post by ubix on 2007-02-19
Though you need to find out parameters for your monitor, Intel site may give you some valuable info about your problem too. Check out the following:  [Intel® 82845G Graphics Controller]("http://www.intel.com/support/graphics/intel845g/")  

The following may help you look into XP: [How to Identify Your Graphics/Video Driver Version]("http://www.intel.com/support/graphics/sb/cs-009480.htm?iid=graphics+845main&"), Good luck :)

---

### Post by nathanziarek on 2007-02-19
This sorta blows. 

I ran **sudo dpkg-reconfigure xserver-xorg** and, while I didn't know the answers to some of the questions, it didn't change a thing (I restarted to make sure the new stuff was loaded).

I browsed through the Device Manager and the Driver Settings in XP, but wasn't able to find any HSync or Vertical Refresh information.

Since this is an all-in-one, there isn't a monitor brand. I even took the back off to look for some type of marking, but there isn't anything I can see.

If this is what it takes to get a usable Linux system up and running, I might not be quite cut out for this... :-)

---

### Post by nathanziarek on 2007-02-19
OK...in the xorg.conf file, it make mention of the screen being a Sinai S5 15. I've searched on it for some time (trying all different variations) but not been able to come up with much. Is there a good place to look for this sort of data?

---

### Post by nathanziarek on 2007-02-19
SO, um...there is this little tiny button on the side of the monitor that, when pressed, does auto adjustment. And now it works fine. And I'm a jack@$$. 

Thanks for the help everyone!

Nate

---

### Post by ubix on 2007-02-19
Yes it can be intimidating at the beginning. Here we are experiencing the evil of proprietary software and copyrights first hand. There are solutions available but all boils down to experience, time and ultimately money. Here we try to ignore the commercial aspects as much as possible, and there are many people who are willing to help fight the above mentioned evils.

At one point you'll need to touch the configuration. So make sure you have the working **xorg.conf** saved. If you can print it out, too have access to working parameters at all times.

Most likely your safest path would be to download the Driver for Linux from Intell's site and install it. This should not be too hard, and nothing like the nVidea/ATI nonsense I went through. If it requires rebuilding kernel, just forget about it, and start shopping for a commercial solution or a "Linux versed" friend who can help you out.

But if you are willing to try out some other things you can start by reducing the **HorizSync** and **VertRefresh** by small amounts, from your current settings ```

	HorizSync	30-60   # --> 28-55   (do not go below 26-50)
	VertRefresh	40-75   # --> 38-70   (do not go below 36-60) 
```.
Each time you make the change restart the window manager (Ctrl+Alt+Backspace). In the worst case you'll need to **boot failsafe**.

If you know how to work in terminal mode (non-GUI), you can modify the settings in **xorg.conf** many times in the row, by subsequently trying to start the GUI by entering **startx**. During this process you will be able to obtain the **EE** entries (the errors), which may enable you to pinpoint the problem.

And yes, there are many places which may be useful, however, this may not be something you really want to do if you are looking for a quick fix. It all depends, how much time you are willing to spend on this.

---

### Post by sloggerkhan on 2007-02-19
Yeah, on a lot of monitors you have to hit the auto adjust button the first time you boot up ubuntu.

---

### Post by ubix on 2007-02-19
> Yeah, on a lot of monitors you have to hit the auto adjust button the first time you boot up Ubuntu.  This is not the best thing, particularly if you use the same monitor on multiple systems simultaneously. It also points to a very likely  misconfiguration or a problematic driver.

---

