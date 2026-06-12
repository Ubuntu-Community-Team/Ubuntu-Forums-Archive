---
title: "X server error"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by FifeFlyer on 2007-02-19
Hi

First time of trying abuntu and liked the idea of trying from CD without installing.

However, burned cd ok (tried both 6.10 & 6.06 both have the same error!)

Booted pc with cd in drive, get abuntu load screen (orange bar fills to end of line), goes to black screen with flashing cursor _ top left hand corner.

Then error message:

"Failed to start the X server (your graphical interface). It is likely it is not set up correctly."

After going thru the next few screens I get 

"X server is now disabled. Restart GDM when it is configured correctly."

How do I configure it correctly (Graphics card is ATI X600 256mb HyperMemory)

Any help would be appreciated

Thanks

---

### Post by mikewhatever on 2007-02-19
You can try reconfiguring xserver while running a live session. If you get a prompt (Do you want to reconfigure ...) just follow it. The Tab button is to select OK. Try choosing different graphics drivers. Vesa is said to be the most universal, but perhaps ati will work. There is a lot more there, so check the link below for explanations.
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

If you do not get the prompt to reconfigure, then type 
> sudo dpkg-reconfigure xserver-xorg on the black screen. I really hope one of the drivers will work, but if not, there is an option of installing with an Alternate CD (text mode installer) and then trying envy program or manual driver installation.

---

### Post by nickoli_02 on 2007-02-19
```
sudo dpkg-reconfigure xserver-xorg
```

Go through the prompts and select the options that best suits your hardware. When it asks to specify the video driver to use select "vesa", not "ati". The default ati drivers won't work, for some reason. Once you're back to the terminal, type "startx" to get the gui running.

Now you'll want to get the fglrx driver installed so you have better graphics. Follow [this]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") guide if you installed 6.10. If you installed 6.06 you can still follow that guide, just don't do the step where it says to edit xorg.conf to disable composite, in section extensions.

---

