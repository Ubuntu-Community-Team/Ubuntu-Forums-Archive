---
title: "Chaning Resolution. HELP!"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by xkiddiegrinders on 2005-12-22
When I try to go into the system tools and change the resolution through the screen resolution thing it only gives me up to 1024x768 and I KNOW my card can hit 1600x1200. Any ideas?

---

### Post by Perfect Storm on 2005-12-22
If you have your monitor specs:

```
sudo gedit /etc/X11/xorg.conf
```

find the **Section "Monitor"**

change:
[b]HorizSync
VertRefresh[/b]

with your monitor specs.

reboot.

Warning: Make sure it's the right number, or there's a chance you'll ruin your monitor.

---

### Post by xkiddiegrinders on 2005-12-22
How do I find those specs?

---

### Post by Perfect Storm on 2005-12-22
In your monitor manual or a google search.

---

### Post by xkiddiegrinders on 2005-12-22
This is what its showing me. and rhe horizsync and vertrefresh are correct...but it seems that it doesnt want to use resolutions about 1024x768. Under mac OS X I can get 1600x1200 @ 60hz....Im sorry if I sound like an idiot but its just not working...

> [SIZE="1"]Section "Monitor"
	Identifier	"DELL P780"
	Option		"DPMS"
	HorizSync	30-85
	VertRefresh	48-120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 7200 (R100 QD)"
	Monitor		"DELL P780"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "960x960" "960x720" "800x600" "760x608" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "960x960" "960x720" "800x600" "760x608" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "960x960" "960x720" "800x600" "760x608" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "960x960" "960x720" "800x600" "760x608" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "960x960" "960x720" "800x600" "760x608" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "960x960" "960x720" "800x600" "760x608" "720x400" "640x480"
	EndSubSection[/SIZE]

---

### Post by nolan- on 2005-12-22
Hi,
I think what you need to do mate is just edit the config to have these resolutions.
So your new cfg will look like this :
```
 Depth 24
Modes "1600x1200" "1024x768" "960x960" "960x720" "800x600" "760x608" "720x400" "640x480"
EndSubSection
```

You simply add the resolutions that you KNOW work. Add "1600x1200" before each instance of "1024x768".

Hope this helps

---

### Post by xkiddiegrinders on 2005-12-22
Awesome, thank you soooo much everybody, that did it.

---

### Post by patrick295767 on 2005-12-22
or :
```
dpkg-reconfigure xserver-xorg
```  
  
Then, u may reconfigure easily the resolution ... 
select and click enter !
If you dont know, just leave default value !
  
Let me know if u managed !
 
Greetz

pat

---

### Post by chinaski on 2005-12-22
I have an integrated video card on the K8V-MX Asus MoBo and there is no HorizSync/VertRefresh field in xorg.conf

should I manually add it according to monitor (CRT) specs even if I have no particular issue?

---

### Post by bscbrit on 2005-12-22
chinaski - if its working why change it?  Is there something that you think it should do but doesn't?

---

### Post by chinaski on 2005-12-22
no, I just wondered for curiosity 

I wanted to try add, but do not want to damage the monitor, that's why I asked. and to learn a little

---

### Post by bscbrit on 2005-12-22
I wouldn't recommend changing xorg.conf unless you know what you are doing, or at least what you hope to achieve.  If you corrupt it you can end up stuck with only a terminal to work from.  Its not the end of the world but it can be quite intimidating for someone who has not done much terminal work in the past to get a system up and running again.  And if you have no desktop - you will not have access to this forum, at least from the broken machine.
I suggest that you read everything you can about xorg.conf - try Googling for it.  And if you do not know what that means then come back here and someone will explain.  Or, in a terminal, type the following:

man xorg.conf

Don't be put off by the format.  Try to understand what it is saying.  Use Page Up and Page Down as usual, and press 'q' when you want to quit.  Google and the man pages contain a wealth of information, as do the wiki pages and other links at the top of this screen.  Plus you have the links that are below my signature.  Read these but please do not tamper with your xorg.conf.

---

### Post by ronb on 2005-12-23
[QUOTE=patrick295767]or :
```
dpkg-reconfigure xserver-xorg
```  
  
Then, u may reconfigure easily the resolution ... 
select and click enter !
If you dont know, just leave default value !
  
Let me know if u managed !
[/QUOTE]

Thanks Pat.  I tried the code, and it worked great.  Ron

---

