---
title: "how get 1440x990 resolution on my iMac G4 17&quot; flat pane"
date: 2004-10-13
forum: Apple PPC Users
---

### Post by germanoob on 2004-10-13
hi there, i am quite new to linux in general and just tried the ubuntu installation on my beloved iMac.
everything worked really fine and i use my old "classic" partition (10 GB) for ubuntu now.
my printer and cardreader do work. internet via firefox works but is poorly slow, i am connected via dhcp-router to adsl, so it should be really fast, anybody an idea about this?
but my main problem is that i can't get the iMac's  17" widescreen tft panel to work with its native solution of 1440x900. i tried to change the »XF86Config-4« file, but this didn't help.
graphics card is the Nvidia Gforce 4MX 32MB. I would be thankfull for any help but keep in mind, that i am not a coding hero at all ;-)
BTW: my second monitor doesn't work either, what can i do?

Greetings from Germany

---

### Post by MikeJS on 2004-10-13
Hey! I have a 17" iMac too, and had a lot of trouble getting 1440x900 to work (maybe the Ubuntu team will fix this in a future version of the installer..?). After a lot of searching and trial and error, though, I came up with this, which seems to work great:

```
Section &quot;Device&quot;
	Identifier	&quot;NVIDIA Corporation NV17 &#91;GeForce4 440 Go&#93;&quot;
	Driver		&quot;nv&quot;
	BusID		&quot;PCI&#58;0&#58;16&#58;0&quot;
EndSection

Section &quot;Monitor&quot;
	Identifier	&quot;Generic Monitor&quot;
	HorizSync	28-70
	VertRefresh	43-72
	Option		&quot;DPMS&quot;
	Modeline &quot;1440x900&quot; 100.00 1440 1500 1508 1512 900 916 924 940 -hsync -vsync
EndSection

Section &quot;Screen&quot;
	Identifier	&quot;Default Screen&quot;
	Device		&quot;NVIDIA Corporation NV17 &#91;GeForce4 440 Go&#93;&quot;
	Monitor		&quot;Generic Monitor&quot;
	DefaultDepth	24
	SubSection &quot;Display&quot;
		Depth		24
		Modes		&quot;1440x900&quot;
	EndSubSection
EndSection

Section &quot;DRI&quot;
	Mode	0666
EndSection

```

Hope this help!

---

### Post by germanoob on 2004-10-13
You really made my day   :D 

i changed the file according to your instructions and what do i have to say: it works!   

now i no longer must hurt my eyes with this 640y480 view that made it nearly impossible to navigate through ubuntu...
on the other hand now the other things become obvious that still don't work satisfying:

- second monitor (which should also be just another change in the XF86Config-File, isuppose)
- terrible slow connection time to http-servers in Firefox (once connected to a site the next one on the same server goes rather quick)

i'll post some other issues later, for now i want to enjoy the success that you made possible, mike

i do really like this community, keep on the good work 
 :)

---

### Post by gilgamesh on 2004-10-31
well my connection via firefox and airport on iBook 500MHz works very well (128Ko/sec). It's even faster than on my dual 2GHz G5 and macosx.

Thanks 
G

---

### Post by Mikel on 2004-11-03
Would this configuration also work with the Revision A 17 inch PowerBook? I'm not 100% sure but I remember them having very similar graphics cards. Also, how can I edit the file, like when its booting up, is there anythying I can do so that I get access to the command line, before it even loads the gdm? that way i could nano or something and try editing that the way u guys have it. Thanks!  :-)

---

### Post by chascon on 2005-02-22
"is there anythying I can do so that I get access to the command line, before it even loads the gdm? that way i could nano"

yeah, cntrl-option-F1 at gdm switches you to console.

---

### Post by semonski on 2006-09-30
Ok, so here is the ultimate stupid question.

I'm such a "weekend" linux user that I do not know where to find the XF86Config file in order to edit it.  (I've used file search, I've poked around as well...)  I'm ok with editing it as root or as sudo or whatever I have to do to edit the file, but I could really use some assistance on the location of this config file using Ubuntu 6.06LTS.


thanks In Advance,


Kos

---

### Post by Pyr3 on 2006-09-30
> **semonski said:**
> Ok, so here is the ultimate stupid question.

I'm such a "weekend" linux user that I do not know where to find the XF86Config file in order to edit it.  (I've used file search, I've poked around as well...)  I'm ok with editing it as root or as sudo or whatever I have to do to edit the file, but I could really use some assistance on the location of this config file using Ubuntu 6.06LTS.


thanks In Advance,


Kos


If you're a "weekend" user, you probably did the default install.

It should be located at:

```
/etc/X11/xorg.conf
```

I would suggest a:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

before fiddling.

---

