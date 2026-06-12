---
title: "Help with ATI RADEON 9550"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by chewy86 on 2007-06-26
I reading a book and I am now to the point where it is telling me how to upgrade my video drivers so that my card can do 3d.  I AM USING AN ATI RADEON 9550

This is what it tells me to do:

[LIST=1]
[*]install [FONT="Courier New"]xorg-driver-fglrx[/FONT], from the Synaptic Package Mangager
[*]When this has finished installing, open a terminal window and type [FONT="Courier New"]sudo aticonfig --initial[/FONT].
[*]Reboot
[*]It tells me to now open a terminal window and type in [FONT="Courier New"]fireflcontrolpanel[/FONT] to further configure my cards settings.
[/LIST]

I get to step 2 and this does not work, the terminal responds with [FONT="Courier New"]Found fglrx primary device section
Nothing to do, terminating.
[/FONT].

By the way I am using Edgy, not Feisty.

I have even removed the driver and reinstalled it, I do not know what to do.

Any help would be awesome!

---

### Post by starcraft.man on 2007-06-27
Uh, well for starters I'm 100% nvidia guy so I can't really tell ya whats wrong (never installed fglrx manually...), which book is it btw?

Anyway, I always install my drivers with the Envy script. Awesome program, and it does it all for you automatically...

[Envy.]("http://albertomilone.com/nvidia_scripts1.html") It works with most ATI cards I think, if it doesn't work hang around for one of the ATI folks... Download the stable version, install and run from the applications menu.

Hope that does it, best of luck :).

---

### Post by w4ett on 2007-06-27
I agree with starcraft....Envy should do a good job with the 9550...

---

### Post by chewy86 on 2007-06-27
Awesome, I installed the driver using envy.  My graphics are not running super smooth though when I test it with the screensavers. 

Are there any more solutions?

---

### Post by w4ett on 2007-06-27
post your fps rate from:

glxgears

---

### Post by chewy86 on 2007-06-27
So I don't mean to sound stupid but how do you do that?

---

### Post by Boris-- on 2007-06-27
type glxgears into console?

---

### Post by sludgman on 2007-06-27
I tried using the Envy program to install my nVidia drivers like so many have suggested and it seemed to work at first, then on reboot it said there was a problem with the driver and would leave me in the text based interface. I just reinstalled the OS after that because I had no idea what was going on. Any suggestions?

---

### Post by phr0ze on 2007-06-27
When that happens you just need to restore the /etc/X11/xorg.conf file. Here is how.
cd /etc/X11
ls
Look for a file called xorg-backup.conf, xorg.conf-backup or anything at all like that.
Then type:
sudo cp Name-of-backup-file xorg.conf

---

### Post by bodhi.zazen on 2007-06-27
> **sludgman said:**
> I tried using the Envy program to install my nVidia drivers like so many have suggested and it seemed to work at first, then on reboot it said there was a problem with the driver and would leave me in the text based interface. I just reinstalled the OS after that because I had no idea what was going on. Any suggestions?

First, you are unlikely to get a response to a nvidia question in an ATI thread.

Second, when this happens, try installing the nvidia driver a second time.

Third, FYI, you will need to re-install the nvidia driver with each and every kernel update, so keep that envy script handy.

---

### Post by stchman on 2007-06-27
> **chewy86 said:**
> I reading a book and I am now to the point where it is telling me how to upgrade my video drivers so that my card can do 3d.  I AM USING AN ATI RADEON 9550

This is what it tells me to do:

[LIST=1]
[*]install [FONT="Courier New"]xorg-driver-fglrx[/FONT], from the Synaptic Package Mangager
[*]When this has finished installing, open a terminal window and type [FONT="Courier New"]sudo aticonfig --initial[/FONT].
[*]Reboot
[*]It tells me to now open a terminal window and type in [FONT="Courier New"]fireflcontrolpanel[/FONT] to further configure my cards settings.
[/LIST]

I get to step 2 and this does not work, the terminal responds with [FONT="Courier New"]Found fglrx primary device section
Nothing to do, terminating.
[/FONT].

By the way I am using Edgy, not Feisty.

I have even removed the driver and reinstalled it, I do not know what to do.

Any help would be awesome!

Installing ATI drivers in Edgy is a PITA.  Here is how I did it on my ATI equipped laptop when I ran Edgy.

[http://www.stchman.com/video_drivers.html](http://www.stchman.com/video_drivers.html)

I then discovered Envy and it made it far easier.

Feisty has restricted drivers to install both ATI and Nvidia cards.

I recommend Feisty.

---

### Post by chewy86 on 2007-07-02
So i get glxgears running but how do I find the frame rate?

---

### Post by bodhi.zazen on 2007-07-02
Open a terminal, enter ```
glxgears
```

You will see the gears ~ let 'em hypnotize you for a while

doh, look at that terminal :lolflag:


> bodhi@Fedora:~$glxgears
30993 frames in 5.0 seconds = 6198.472 FPS
31032 frames in 5.0 seconds = 6206.191 FPS
27857 frames in 5.0 seconds = 5571.253 FPS
27793 frames in 5.0 seconds = 5558.595 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
bodhi@Fedora:~$

---

### Post by chewy86 on 2007-07-03
so i type it in the gears come up and then i sit and stair, got hypnotized, and then exited it.  it didn't tell me my frame rate or any info at all! how do i get that?

---

### Post by bodhi.zazen on 2007-07-03
> **chewy86 said:**
> so i type it in the gears come up and then i sit and stair, got hypnotized, and then exited it.  it didn't tell me my frame rate or any info at all! how do i get that?

bodhi looks up from a hypnotized stupor ~ Hmm ... no feedback in the terminal ? not sure about that one mate, hopefully someone with a little more ati experience can help ???

---

### Post by kittyhawk63 on 2007-07-03
> **chewy86 said:**
> So I don't mean to sound stupid but how do you do that?

You're not stupid. You're inexperienced. Start the console (terminal) and copy and paste  **glxgears **into the console. Now hit the enter key on the keyboard. The gears will turn and you will find the fps rate below where you pasted **glxgears.**
kh

---

### Post by chewy86 on 2007-07-07
> **kittyhawk63 said:**
> You're not stupid. You're inexperienced. Start the console (terminal) and copy and paste  **glxgears **into the console. Now hit the enter key on the keyboard. The gears will turn and you will find the fps rate below where you pasted **glxgears.**
kh
I did that, and it really won't don anything, the gears come up but the fps won't.

---

