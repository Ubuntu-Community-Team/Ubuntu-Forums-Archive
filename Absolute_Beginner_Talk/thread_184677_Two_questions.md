---
title: "Two questions:"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by Shelter417 on 2006-05-30
When using Firefox and viewing a site such as ytmnd.com, I get a message informing me that there are missing plugins; when I click "install missing plugins," it says that no suitable plugins were found. What should I do?

When attempting to play a CD I receive the message "registry is not present or it is corrupted. Please update it by running gst-register." How do I fix this?

---

### Post by aggiechemist on 2006-05-30
I looked at the website, and it appears to be flash media that you need.

I would suggest you go to [www.flash.com](www.flash.com) to get the right plugin (don't use the automatic one for Firefox, I hate that thing). Find the download section and you can download a flash player for linux. Save it to the desktop, and follow their instructions on the website. If you do exactly as they tell you, all will be well.

I see the stuff on the site just fine, by the way. 

I'm afraid I don't recognize you CD problem though. I'm not sure about that one.

Good luck!

---

### Post by Sef on 2006-05-30
> When using Firefox and viewing a site such as ytmnd.com, I get a message informing me that there are missing plugins; when I click "install missing plugins," it says that no suitable plugins were found. What should I do?

What plugins are missing? Check out [RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats") for flash and java.

> When attempting to play a CD I receive the message "registry is not present or it is corrupted. Please update it by running gst-register." How do I fix this?

Applications > Accessories > Terminal

sudo apt-get update

sudo aptitude install gst-register

> would suggest you go to [www.flash.com](www.flash.com) to get the right plugin (don't use the automatic one for Firefox, I hate that thing). Find the download section and you can download a flash player for linux. Save it to the desktop, and follow their instructions on the website. If you do exactly as they tell you, all will be well.

Restricted Formats is much easier to get flash from.

---

### Post by Shelter417 on 2006-05-30
I tried the sudo apt. commands and they didn't work.

Also, where's the command prompt for installing Flash?

---

### Post by az on 2006-05-30
> **Shelter417]When using Firefox and viewing a site such as ytmnd.com, I get a message informing me that there are missing plugins said:**
> 

*Captain*
*Jean-luc*
*Picard*
*From the*
*U-S-S*
*Enterprise*

To hear that, you need quicktime.  Most ytmnd sites use quicktime audio.  I don't know if there is a way to get firefox in linux to play quicktime.

You *can* install firefox for windows in wine and visit those sites.  That really *really* is a perfect waste of time...... :)  You can install the windows plugins and everything.  It just runs slow and is slightly crashy, I think.

[QUOTE=Shelter417]

When attempting to play a CD I receive the message "registry is not present or it is corrupted. Please update it by running gst-register." How do I fix this?

I have never heard of that.  Maybe try running
gst-register
from the command line.  Did you install gstreamer plugins and get errors upon installation?

Just for the heck of it, try running

sudo apt-get -f install

to see if you have some partially installed (failed install) packages and to try to fix them.

---

### Post by az on 2006-05-30
[QUOTE=Shelter417]I tried the sudo apt. commands and they didn't work.

Also, where's the command prompt for installing Flash?[/QUOTE]

Applications - Terminal

But just install the flashplayer-nonfree package from multiverse.

---

### Post by Shelter417 on 2006-05-30
[QUOTE=azz]*Captain*
*Jean-luc*
*Picard*
*From the*
*U-S-S*
*Enterprise*

To hear that, you need quicktime.  Most ytmnd sites use quicktime audio.  I don't know if there is a way to get firefox in linux to play quicktime.

You *can* install firefox for windows in wine and visit those sites.  That really *really* is a perfect waste of time...... :)  You can install the windows plugins and everything.  It just runs slow and is slightly crashy, I think.



I have never heard of that.  Maybe try running
gst-register
from the command line.  Did you install gstreamer plugins and get errors upon installation?

Just for the heck of it, try running

sudo apt-get -f install

to see if you have some partially installed (failed install) packages and to try to fix them.[/QUOTE]
That didn't work, for some reason.

Terminal also didn't work for running the Flash installation. What's multiverse?

---

### Post by RudolfMDLT on 2006-05-30
Hi!

Install easy ubuntu and see what happens! it's a really handy application it solved all my browser problems-including java and quicktime!

[http://placelibre.ath.cx/keyes/index.php/2005/10/27/65-easy-ubuntu-24-beta](http://placelibre.ath.cx/keyes/index.php/2005/10/27/65-easy-ubuntu-24-beta)

Hope this sorts you out!

PS: Just one thing, there is an option for installing new graphics drivers. If you display works, UNTICK this option.

---

### Post by aggiechemist on 2006-05-30
I have made QT play in firefox. Try the packages mplayer and mozilla-mplayer and you should be all set.

Might be good to also add in w32codecs to may it powerful.

---

### Post by Witty Name on 2006-07-01
[QUOTE=Shelter417]When using Firefox and viewing a site such as ytmnd.com, I get a message informing me that there are missing plugins; when I click "install missing plugins," it says that no suitable plugins were found. What should I do?[/QUOTE]

I speculate that this is caused by a missing wave-plugin.

Solution: 
1) Install [mplayerplug-in.sourceforge.net](mplayerplug-in.sourceforge.net)
2) Hack ~/.mozilla/pluginreg.dat
3) [Profit](http://lazytownworkit.ytmnsfw.com/).

EDIT: However, some ytmnd's seem to need rewriting.
For example [this](http://stansellseverything.ytmnd.com/) one.
Looking at the code:
```

var loader = new YTMNDLoader("http://content.ytmnd.com/content/9/4/4/944224615a43834320244c8411863831.gif", "http://content.ytmnd.com/content/d/2/0/d20e24c64966564d29640a9dcfef8b3a.mp3", "110E15", false, 0);   
	var is_vis = false;

```

We see that ideally, we would like to replace this.
For example with the javascript-way of looping sound for firefox, like this:
```

<script> 
function EvalSound(soundobj) { 
   var thissound= eval("document."+soundobj); thissound.Play();
} 
</script>
<embed src="http://content.ytmnd.com/content/d/2/0/d20e24c64966564d29640a9dcfef8b3a.mp3" 
   autostart=true 
   width=0 
   height=0 
   name="sound1" 
   enablejavascript="true" 
   loop="true"
>

```

This can be done with privoxy, as one example.

---

### Post by user1397 on 2006-07-01
[quote=Sef]sudo apt-get update

sudo aptitude install gst-register[/quote]well, for aptitude to really work, you need to **sudo aptitude update**.  you have to either use only apt-get or only aptitude.  i recommend aptitude though, it handles dependencies incredibly well.

---

