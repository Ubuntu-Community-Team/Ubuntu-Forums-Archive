---
title: "Is this font rendering the best we can get?"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by konungursvia on 2007-01-24
Well I think I've done just about everything the forums suggest to make my fonts look as good as in Windoze.

Here's what my Times 12 looks like, but it isn't so great. I love everything ELSE about linux, but I'm wondering... Is there an absoute font expert out there that can perhaps identify right away why this doesn't look so hot?

---

### Post by Shatrat on 2007-01-24
It used to look a lot worse, let me tell ya.
That looks fine to me, but im not a typesetophile type.  
If I can read it and it isnt terribly jaggedy I am not too picky.

---

### Post by hscottyh on 2007-01-24
Was ubuntu installed on a CRT and moved to LCD or vise versa?

It does make a difference how xorg is configured for each.

---

### Post by hscottyh on 2007-01-24
I'm no expert, but my fonts seem smoother than windows......
Actually they are so smooth, I want to slide them off the monitor and rub them over my entire body. :D Just kidding I read that once in an ubuntu review a while back and thought it was hilarious.

---

### Post by konungursvia on 2007-01-24
It was installed on LCD, but I had to install the legacy NVIDIA driver to use the monitor's native 1280x1024. I believe xorg.conf has nice settings now, but funny enough, my old acer next to this Dell is 1024x768 and the native Ubuntu fonts look better there by far than the smoothed, tweaked sexed up fonts here on this.

Here is the relevant bit of my xorg.conf:

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 440 Go]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
 	Option 		"NoLogo" "1"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
	Option		"DPI"   "96 x 96"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 440 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "1024x1024" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "1024x1024" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "1024x1024" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "1024x1024" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "1024x1024" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "1024x1024" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by hscottyh on 2007-01-24
I've never had to use:
Option "DPI" "96 x 96"

I'm getting to tired to look it up. I assume you put it there on purpose? Can you tell a difference with it commented out.

Have you played around with the different defaults in:
System -> Preferences -> Fonts

My friends dad's monitor's default was 1600x1200. I made them all larger, which really made them crisp. He's close to 70.... He feel in love with it the minute he saw the desktop. That seemed to be when he really seem like... "hey I'm gonna like this!"

Sorry for the ramble....

If I remember correctly when you reconfigure xorg it ask some questions that make a difference to having an LCD or not. I'm not sure if the results to some of those answers make it into the xorg.conf and are set somewhere else. 

Backup your xorg.conf and thin
sudo dpkg-reconfigure xserver-xorg

Read it all carefully... Seems like you are well versed enough to make the correct choices, and notice anything revelant.

**NOTICE: ** Anyone unsure of this advice. Ask for more details before trying! You can lock yourself out of the GUI!!! Recoverable, but a pain to look up how if this is your only computer.

---

### Post by Bachstelze on 2007-01-24
```
sudo apt-get install gsfonts-x11
```

can help, too :)

---

### Post by mahiyar on 2007-01-25
For good browser fonts try Opera, imho it looks better than firefox.

---

### Post by kerry_s on 2007-01-25
Try using the verdana fonts their designed for readabilty and are the most common fastest fonts used, you might even notice web pages will load faster using them. The recommended size is 14.

---

### Post by ardchoille42 on 2007-01-25
> **konungursvia said:**
> Well I think I've done just about everything the forums suggest to make my fonts look as good as in Windoze.

Here's what my Times 12 looks like, but it isn't so great. I love everything ELSE about linux, but I'm wondering... Is there an absoute font expert out there that can perhaps identify right away why this doesn't look so hot?

To offense, but your fonts aren't very pretty - just my opinion. Here's a screenshot of my Ubuntu after a fresh install. I think it looks quite good :)

---

### Post by riven0 on 2007-01-25
I don't know... that looks mighty weird. I've posted a pic on how my fonts look. Pretty nice, eh? :D 

Anyway, I've got gsfonts-x11, msttcorefonts, xfonts-100dpi and xfonts-75dpi installed. Under the Font section I use Subpixel (LCDs) under Smoothing and Medium under Hinting and my Subpixel order is RGB. 

My default applications font is Arial. Not sure if you've already done all that, but I figured it couldn't hurt.

---

### Post by dwblas on 2007-01-25
I installed xfs and xfstt in order to use Verdana as it is a truetype font.  Is this no longer necessary in xorg, or is that why the original post couldn't get decent fonts.  I don't know.  I've been using Linux for over 10 years and just installed it because I always have.

---

### Post by Josh1 on 2007-01-25
My fonts are the ones that came default with Ubuntu, they look the same as Windows!

---

### Post by kerry_s on 2007-01-25
Okay since everyone else gets to do a pic :D ->

---

### Post by konungursvia on 2007-01-25
> **HymnToLife said:**
> ```
sudo apt-get install gsfonts-x11
```

can help, too :)

Thanks, got them already too. Made resolution 96x96 because it was stuck at 95x96, and looked a bit worse.

---

### Post by konungursvia on 2007-01-25
> **kerry_s said:**
> Okay since everyone else gets to do a pic :D ->

Wow, that's what I want my fonts to look like. It seems there is no real font smoothing in mine. Could it be because I have a laptop (Dell Inspiron 8200) and I'm using an external Phillips 17" lcd monitor instead of the strange native 1400x1500 of the dell? Also, xfstt seems to have helped the sans serif fonts a bit, thanks! But Times still seems really weak and spotty. Also, xfs wouldn't install because of a conflict with flashplugin-nonfree. I'll try a different resolution for this conflict...

---

### Post by Darko Beta on 2007-01-25
My fonts look really nice after following these instructions in the Ubuntu guide:

gedit ~/.fonts.conf

    * Paste in this text: 

<?xml version=&#8221;1.0&#8221; ?>
<!DOCTYPE fontconfig SYSTEM &#8220;fonts.dtd&#8221;>
<fontconfig>
<match target=&#8221;font&#8221;>
<edit name=&#8221;autohint&#8221; mode=&#8221;assign&#8221;>
<bool>true</bool>
</edit>
</match>
</fontconfig>

    * You&#8217;ll have to log out and back in to see the difference.

---

### Post by konungursvia on 2007-01-25
> **Darko Beta said:**
> My fonts look really nice after following these instructions in the Ubuntu guide:

gedit ~/.fonts.conf

    * Paste in this text: 

<?xml version=”1.0” ?>
<!DOCTYPE fontconfig SYSTEM “fonts.dtd”>
<fontconfig>
<match target=”font”>
<edit name=”autohint” mode=”assign”>
<bool>true</bool>
</edit>
</match>
</fontconfig>

    * You’ll have to log out and back in to see the difference.


Thanks! I'll try this when I get home.

---

### Post by kerry_s on 2007-01-25
Try running these 2 lines to reset all your fonts, the first 1 lets you set up your fonts the second, cleans up the fonts.

sudo dpkg-reconfigure fontconfig-config
sudo dpkg-reconfigure fontconfig

---

### Post by kerry_s on 2007-01-25
> **Darko Beta said:**
> My fonts look really nice after following these instructions in the Ubuntu guide:

gedit ~/.fonts.conf

    * Paste in this text: 

<?xml version=&#8221;1.0&#8221; ?>
<!DOCTYPE fontconfig SYSTEM &#8220;fonts.dtd&#8221;>
<fontconfig>
<match target=&#8221;font&#8221;>
<edit name=&#8221;autohint&#8221; mode=&#8221;assign&#8221;>
<bool>true</bool>
</edit>
</match>
</fontconfig>

    * You&#8217;ll have to log out and back in to see the difference.

Damn, i tried this to see what it would do and it shrank all my fonts, now they won't go back. You wouldn't happen to know how to reverse it do you?
Edit: Nevermind i got it, it was a change i made in xorg.conf and never restarted X.

---

### Post by Patrick-Ruff on 2007-01-25
windows doesn't even anti-aliase fonts . . .

---

### Post by konungursvia on 2007-01-25
> **Darko Beta said:**
> My fonts look really nice after following these instructions in the Ubuntu guide:

gedit ~/.fonts.conf

    * Paste in this text: 

<?xml version=”1.0” ?>
<!DOCTYPE fontconfig SYSTEM “fonts.dtd”>
<fontconfig>
<match target=”font”>
<edit name=”autohint” mode=”assign”>
<bool>true</bool>
</edit>
</match>
</fontconfig>

    * You’ll have to log out and back in to see the difference.


Which fonts.conf file should I put this in? I found 2, and one says don't edit. The other seems to be an auto-generated log of the fonts installed, not settings. Thanks

---

### Post by konungursvia on 2007-01-25
> **kerry_s said:**
> Try running these 2 lines to reset all your fonts, the first 1 lets you set up your fonts the second, cleans up the fonts.

sudo dpkg-reconfigure fontconfig-config
sudo dpkg-reconfigure fontconfig

The first line gave an error message, saying fongconfig-config wasn't installed. The second took me through something I have been in before, so I changed to truetype.

---

### Post by Darko Beta on 2007-01-25
> Which fonts.conf file should I put this in? I found 2, and one says don't edit. The other seems to be an auto-generated log of the fonts installed, not settings. Thanks

When I carried out the first command, it opened gedit and I pasted the text in the editor.  Then I saved the file and closed gedit, and then restarted and voila.

---

### Post by Darko Beta on 2007-01-25
Note:

This is where I got the information:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_smooth_fonts](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_smooth_fonts)

---

### Post by Daveski on 2007-01-25
> **Patrick-Ruff said:**
> windows doesn't even anti-aliase fonts . . .

What about that ClearType thing Microsoft bang on about in XP then?

---

### Post by konungursvia on 2007-01-25
Finally, I got this stuff to work.  Unfortunately, I followed all of the suggestions, and can't be sure which one did it. Linux and Firefox fonts are nice now, but Opera's are still kind of sketchy. Does anyone know why this is?

---

### Post by mahiyar on 2007-01-25
I am going to book mark this thread, currently I'am satisfied with my fonts, but who knows when you might need this.

---

### Post by dwblas on 2007-01-25
I'm using Times New Roman in Opera and it looks fine on my machine.

---

