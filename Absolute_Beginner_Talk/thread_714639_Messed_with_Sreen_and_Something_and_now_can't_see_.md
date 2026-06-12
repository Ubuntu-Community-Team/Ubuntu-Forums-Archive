---
title: "Messed with Sreen and Something and now can't see anything"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Crusher16 on 2008-03-04
On my ASUS F3Jp with 7.10, I used the setting applet called Screen & 'Something' (Forgot the whole name) and set it to use my external monitor has my main display and it told me to restart. Well, I restarted and it doesn't use my external monitor as a display, nor does it use the laptop monitor as a display so I can't see anything. Is there a way I can set it back to default settings?

---

### Post by HereInOz on 2008-03-04
I have never been in this situation before, but what happens if you type CTRL-ALT-Backspace?  Does that bring up a text screen with an offer to log on?  

If not, try pressing Fn-F5 and see what that does for you.  It works on most Asus laptops to switch between the LCD and an external monitor, when using Windows at least.  It might work with Ubuntu, but as I said, I have never been here so I have no first hand information.

---

### Post by talsemgeest on 2008-03-04
Ok, to fix it, boot into recovery mode, which will bring you to a root terminal.

Simply type: ```
**sudo dpkg-reconfigure xserver-xorg
```**.

And press enter.

That should fix the problem by resetting graphics and such back to the default settings.

Hope this helps :)

---

### Post by Crusher16 on 2008-03-04
> **HereInOz said:**
> I have never been in this situation before, but what happens if you type CTRL-ALT-Backspace?  Does that bring up a text screen with an offer to log on?  

If not, try pressing Fn-F5 and see what that does for you.  It works on most Asus laptops to switch between the LCD and an external monitor, when using Windows at least.  It might work with Ubuntu, but as I said, I have never been here so I have no first hand information.

On my ASUS its Fn+F7 and that has never worked as far as I can remember in Ubuntu. When I hook up an external monitor it duplicates the laptop screen onto the external one automatically.

The CTRL+ALT+Backspace doesn't do anything unfortunately. Hmm...



> **talsemgeest said:**
> Ok, to fix it, boot into recovery mode, which will bring you to a root terminal.

Simply type: ```
**sudo dpkg-reconfigure xserver-xorg
```**.

And press enter.

That should fix the problem by resetting graphics and such back to the default settings.

Hope this helps :)

Thanks but I'd like to avoid that as much as possible, seeing as how I have Beryl running perfectly and don't want to go through the whole ordeal of getting working again. Would the the xorg file have the settings for the external monitor that I could just delete from the file or something?

---

### Post by talsemgeest on 2008-03-04
You could try that i suppose. Just try deleting the second monitor from it

---

### Post by graabein on 2008-03-04
You can probably edit the xorg.conf manually. See for example [The X Server Configuration HOWTO]("http://www.gentoo.org/doc/en/xorg-config.xml") on Gentoo for more information before you start editing. And do a backup before you start!

---

### Post by talsemgeest on 2008-03-04
Just go ```
sudo nano /etc/X11/xorg.conf
```

Then edit whatever you need to edit

---

### Post by Crusher16 on 2008-03-04
Alright. I'll give it a look when I get the chance to. Whats the command to backup the xorg file?

---

### Post by dondad on 2008-03-04
assuming that you are in a terminal:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak

(or any other extension that helps yo remember where to find the backup)

Note that it is case sensitive and the "X" is a capital

---

### Post by Crusher16 on 2008-03-04
I did the reconfigure xorg one and that didnt fix it. Still doesn't show anything on the laptop but the screen light is on.

---

### Post by talsemgeest on 2008-03-04
Well I can see absolutely no reason why it wouldnt work. But since it didnt... I guess you will have to edit it manually

---

### Post by Crusher16 on 2008-03-05
Tried editing it manually first. Got rid of the generic monitor entries. That didn't do the trick. Not sure what else to remove.

---

### Post by talsemgeest on 2008-03-05
There is a way to manually reconfigure the xorg, I've done it before but I cant find it anywhere

---

### Post by talsemgeest on 2008-03-05
Hey, can you please post your xorg.conf? It might help us to figure out what the problem is.

---

### Post by Crusher16 on 2008-03-05
IS there a way I can post it when I can only use recovery mode?

---

### Post by oedha on 2008-03-06
1. why dont you try :==> sudo dpkg-reconfigure -phigh xserver-xorg
you will be asked only your display driver.......and your beryl or compiz will be just like before....

2. you may manually edit your xorg.conf......"if you know what to edit"......

3. instead of editing...i suggest you to recall the last good xorg.conf.....
for example :
your configuration was messed 2 days ago...then 
go to /etc/X11......type ls -l
find out the xorg.something....with that date....replace the current xorg with this.....

from 1..2...3......now it's your call :)

---

### Post by talsemgeest on 2008-03-06
Wow, I just had one of those Eureka moments. It must be your driver, which I'm guessing has some other settings stored somewhere elsewhere than your xorg.conf. Make sure that your graphics driver is set back to mesa in your xorg.conf, which will let you get back onto a graphical install and fix your graphics settings

---

### Post by Crusher16 on 2008-04-03
> **talsemgeest said:**
> Wow, I just had one of those Eureka moments. It must be your driver, which I'm guessing has some other settings stored somewhere elsewhere than your xorg.conf. Make sure that your graphics driver is set back to mesa in your xorg.conf, which will let you get back onto a graphical install and fix your graphics settings

Where would this "mesa" setting thing be under in the xorg.conf/or where should it be? heh

---

### Post by talsemgeest on 2008-04-04
It should be under your "Device" section in your xorg.conf

---

### Post by Crusher16 on 2008-04-04
> **talsemgeest said:**
> It should be under your "Device" section in your xorg.conf

I can't find anything about it. Could you explain more please?

---

### Post by AustinC on 2008-04-04
You won't find anything about it in xorg.conf because it's probably not your current configuration. The idea is to edit /etc/X11/xorg.conf to replace your current configuration with mesa settings. As to how to do that I do not know.

---

### Post by talsemgeest on 2008-04-04
"Mesa" is the default graphics driver for ubuntu. It can work with almost any graphics card, so if it is enabled chances are it will work.

Under the "device" section, you should have "mesa", as that would mean that yoyr current graphics driver is mesa.

---

