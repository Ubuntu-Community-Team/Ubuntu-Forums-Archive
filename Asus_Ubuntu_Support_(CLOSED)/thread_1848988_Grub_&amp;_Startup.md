---
title: "Grub &amp; Startup"
date: 2011-09-23
forum: Asus Ubuntu Support (CLOSED)
---

### Post by GoffyGoober on 2011-09-23
My start up is buggy, and goes something like this:
[LIST=1]
[*]Press the powerbutton
[*]Grub opens
[*]Press enter
[*]Lots of black and white vertical lines with the actual text illegible and strange saying things like: %df~`0,d/          : (
[*](Yes the ": (" appears, maybe saying "false")
[*]Once it gets to the last line in the list, it kinda stop, and does nothing more in the way of startup
[*]I press reboot
[*]It reboots
[*]grub appears now with higher resolution, and a purple-ish background
[*]Press enter
[*]Wait a while, it starts up
[*]Ubuntu login opens
[*]I login
[*]I logout
[*]I login
[*](The second login is so that it doesn't log me out right in the middle of me using it, logging me out instantly without warning)
[/LIST]

Is there any way to make it normal, like it should?

---

### Post by MetalRider on 2011-10-05
I have the same problem since I took Windows XP off of my system.  When I had Ubuntu installed through Windows XP and selected to boot up using Ubuntu, everything was fine and I never had this problem.

---

### Post by JRV on 2011-10-05
I had this problem with an SIS graphics chip awhile back.

What version of Ubuntu are you using?
Do you have SIS graphics?

To get rid of vertical lines go to the terminal, CD to your root directory.
```

   sudo gedit etc/x11/xorg.conf

```
You can substitute the editor of your choice for gedit.

If you have an etc/x11/xorg.conf file add this to the device section:

```
Driver "vesa"
```

If the file is blank copy this text:

```

   Section "Device"
     Identifier    "Configured Video Device"
     Driver "vesa"
   EndSection

   Section "Monitor"
     Identifier    "Configured Monitor"
   EndSection

   Section "Screen"
     Identifier    "Default Screen"
     Monitor        "Configured Monitor"
     Device        "Configured Video Device"
   EndSection


```

If you absolutely can not see what you are doing to edit the file boot from a Puppy Linux Live CD to make the edits.

I hope this helps.

---

### Post by MetalRider on 2011-10-06
I'm using 11.04 myself.  Could you please break that down a little more for a guy that could basically be considered "plug 'n' play:  ;)

Ok.......I went to the terminal screen and entered the first code line, and got this as a response:

(gedit:1925): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.6XGR2V': No such file or directory

(gedit:1925): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

I did have a window titled etc/x11/xorg.conf open up, and there was nothing in it.  Am I correct in assuming that is where I should have then pasted the third code you gave qne then saved the file?

Now what?  My apologies  in advance.  I  have no real knowledge of Linus or Ubuntu as yet, and had precious little desire to do much of anything with Windows other than use it.

---

### Post by JRV on 2011-10-06
If you have SIS graphics the vesa driver is the only way to make it work.
Try pasting the code into the file.
I don't think there is any way it could make it worse.

---

### Post by MetalRider on 2011-10-07
Thanks!  I will give this a try this weekend when I have some time to play.  For right now, it is just a nuisance more than anything else.  Thank goodness for three day weekends, especially after coming off a 20 day straight work stretch.

---

### Post by JRV on 2011-10-07
The solution in this thread might also help:

[http://ubuntuforums.org/showthread.php?t=1852968](http://ubuntuforums.org/showthread.php?t=1852968)

---

### Post by GoffyGoober on 2011-10-07
The vesa driver? xorg.conf is using "nivida". Is there some unwritten rule that Linux doesn't like nivida graphics cards? Anyways it ONLY happens on startup, before login. Grub isn't even purple, like it should be, probably meaning it Grub isn't looking at all of it's setup files all the time...

---

### Post by MetalRider on 2011-10-09
Hmm, it just sank in this topic is for folks with ASUS computers.. I am running a home built with an ASUS A8N-E mobo.  Would the proposed solution still be applicable?

---

### Post by GoffyGoober on 2011-10-11
Actually, I haven't gotten an answer yet, except for that one which I questioned, and it is quite an old model. But I think it may have something to do with even new Asus computers.

---

### Post by GoffyGoober on 2011-10-14
Lately, I was just starting up my computer, and decided to press the F keys! It worked. When it brings up the loading screen I start, and go at a relaxed pace. There are still vertical bars but I now have to say this: who cares? And having the check disk thing, I think I will now let it do so, as I can't keep it to happen. I don't know if this will work every time as I have just done it a second time...

---

