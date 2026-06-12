---
title: "Envy turns off laptop screen"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2007-01-28
I would like to update my nvidia graphics card driver. I came across [Envy]("http://albertomilone.com/nvidia_scripts1.html").

My gaphics card is a: **GeForce Go 6200**
Driver version: **1.0-8776**

I installed Envy and then restarted the desktop environment. I launched Envy through the terminal, I was asked to choose an option from the ones provided in Envy so I chose '1' for installing nvidia drivers, after I hit ENTER some text appears in the terminal but I don't have any time to read it because the screen turns off.

I can't proceed past this point, I tried it 2 or 3 times but every time the screen turns off after I choose an option in envy and hit ENTER.

(the laptop continues to run, perhaps it is waiting for more input from me, but the screen is off at this point so I can't do anything but shut down and restart).

I would really appreciate some help with this,
Thanks.

---

### Post by PartisanEntity on 2007-01-29
bump.

really need help with this, thanks

---

### Post by edwardLS on 2007-01-29
I also am having some problems with ENVY, but I am getting different symptoms than you describe.  I don't know if this will help, but when your screen goes blank, trying pressing ALT-F1.  My screen don't go blank, but I must press that combination to see what is happening in ENVY.

---

### Post by PartisanEntity on 2007-01-29
I have tried pressing ALT-F1 and unfortunately nothing seems to happen, the screen remains off while the laptop is on without any apparent (to me) change. Upon forcing the computer to power off and on again manually there is no change at all as far as graphics drivers or settings are concerned.

---

### Post by edwardLS on 2007-01-29
I have re-read your original posting, and I may be splitting hairs, but you said you started ENVY in a terminal window.  If this is the case, I think you still have X running and I don't believe that will work.  In my case I press CTRL-ALT-F1 in the GUI desktop environment to close the X Server, and get into a console.  I then log in and type ENVY.  Hope this may help.

---

### Post by PartisanEntity on 2007-01-29
hmm, you may be on to something, ill give it a try right away.

---

### Post by PartisanEntity on 2007-01-29
Okay I tried it, after pressing CTRL-ALT-F1 the laptop screen turns off.

I may be wrong, but at this moment in time I believe that when the X server shuts down the laptop screen turns off.

---

### Post by Pobega on 2007-01-29
You mean you can't even get into a TTY1 session with Ctrl+Alt+F1? Have you tried doing Ctrl+Alt+F1 before logging into Ubuntu?

---

### Post by Sunflower1970 on 2007-01-29
This happened to me the first few times I tried to use envy before I figured it out. I'm using a desktop though. I don't know if the steps are the same. Reboot the computer. When the it starts, you should come up to the GRUB menu. From there, choose the option to go in to the safety mode (should be the second choice on the menu) You'll only be in the terminal. Once everything's loaded, and you get to a prompt (something like root@user $) type in envy. From there you should be able to get it to start, and the drivers will load. Then you can restart the windows manager and you should be able to get in with your new drivers. 

Otherwise, if you haven't done this, you can go and download Automatix2 ([http://www.getautomatix.com/](http://www.getautomatix.com/) for some reason the page isn't loading for me right now though) You can then get the nvidia drivers from this program. I found that easier than using envy...

---

### Post by PartisanEntity on 2007-01-29
> **Pobega said:**
> You mean you can't even get into a TTY1 session with Ctrl+Alt+F1? Have you tried doing Ctrl+Alt+F1 before logging into Ubuntu?

No I haven't tried that. I tried pressing ctrl-alt-f1 while logged in.

---

### Post by PartisanEntity on 2007-01-29
> **Sunflower1970 said:**
> This happened to me the first few times I tried to use envy before I figured it out. I'm using a desktop though. I don't know if the steps are the same. Reboot the computer. When the it starts, you should come up to the GRUB menu. From there, choose the option to go in to the safety mode (should be the second choice on the menu) You'll only be in the terminal. Once everything's loaded, and you get to a prompt (something like root@user $) type in envy. From there you should be able to get it to start, and the drivers will load. Then you can restart the windows manager and you should be able to get in with your new drivers. 

Otherwise, if you haven't done this, you can go and download Automatix2 ([http://www.getautomatix.com/](http://www.getautomatix.com/) for some reason the page isn't loading for me right now though) You can then get the nvidia drivers from this program. I found that easier than using envy...

The 3D graphics card drivers are **already** installed. As you mentioned, I used automatix2 to install them (this was several months ago).

But now I want to **update** them, does automatix2 do that too?

Concerning your tip about launching in safe mode, what command do I need to enter to restart the windows manager?

---

### Post by Pobega on 2007-01-29
> **PartisanEntity said:**
> No I haven't tried that. I tried pressing ctrl-alt-f1 while logged in.
Try it without, you never know. Otherwise you can probably try logging into a terminal session through GDM and doing it, I'm not sure if that would work perfectly though. Your best bet is a TTY1 Session.

---

### Post by PartisanEntity on 2007-01-29
> **Pobega said:**
> Try it without, you never know. Otherwise you can probably try logging into a terminal session through GDM and doing it, I'm not sure if that would work perfectly though. Your best bet is a TTY1 Session.

Excuse my ignorance, what's a TTY1 session?

---

### Post by Sunflower1970 on 2007-01-29
> **PartisanEntity said:**
> Concerning your tip about launching in safe mode, what command do I need to enter to restart the windows manager?

I'm not too sure how it's done on laptops, but Id' think it's the same...when you start up the computer when it's been off, it goes through the splash screen for whatever computer company your computer's from/BIOS, and then it should come to the GRUB menu. You have the choice of booting normally into Ubuntu, the safe mode (I think that's what it's called) a memtest, another option and then if you have any other OS's on your computer as well. Choose the second option on the screen. That'll get you to just the terminal to use then be able to use Envy.

ETA: 
I found this: [http://www.linuxselfhelp.com/HOWTO/Text-Terminal-HOWTO-6.html](http://www.linuxselfhelp.com/HOWTO/Text-Terminal-HOWTO-6.html) on what TTY is...

---

### Post by PartisanEntity on 2007-01-29
Okay I have gone from one problem to another :)

I should have mentioned that I am on a wifi connection, I do not have ethernet here. It would appear that Envy does not support wifi and needs ethernet.

I logged into safe mode, launched envy and waited, it called up numerous error messages since it could not connect, then it proceded to remove my nvidia drivers and then finished without being able to download and install the newer nvidia drivers.

So I had to edit xorg.conf to make it use 'nv' drivers instead of 'nvidia' since it could not load the windows manager otherwise.

So now I am using the nv drivers, instead of upgrading, I have downgraded...

*p.s. now I am trying to launch automatix to install the previous 3d graphics card drivers but apparently automatix cant download the keys so it wont start, great.*

---

### Post by Sunflower1970 on 2007-01-29
Can you try automatix2 again and see if maybe you can upgrade to the newest version of the drivers? I've just assumed that they have the newest drivers (but I could be wrong--and I usually am lol :) )... one computer that has an nVidia 7600GT and one that has a Geforce3 Ti500 and so far so good with everything (knocks on wood...)

---

### Post by PartisanEntity on 2007-01-29
automatix is having trouble downloading keys (from their server I guess) and wont start. Can you confirm this on your end by trying to launch automatix?

---

### Post by Sunflower1970 on 2007-01-29
I'm at work, so no Ubuntu here, but I cannot get into automatix's site at all. So I'm gonna guess if I tried it from home, I'd probably not be able to get it to work either...I know the site worked early this morning...about midnight or so....I was downloading stuff from it....

---

### Post by PartisanEntity on 2007-01-29
Thanks for the info, I have gone ahead and installed the driver manually from the repository, so now I am back to driver version: **1.0-8776**, this **isnt** the latest driver according to the nvidia website.

I guess ill wait until automatix servers are online again, to see if I can updates the drivers like that.

**But I am still interested to know why my screen turns off when x server is shut down, anyone?**

---

