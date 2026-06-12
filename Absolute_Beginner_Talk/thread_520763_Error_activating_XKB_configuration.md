---
title: "Error activating XKB configuration"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by bugster on 2007-08-08
I've always had problems with the number lock not working on my keyboard and yesterday tried changing the keyboard type in  system>preferences>keyboard

I immediately got the error message below

[B]Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70101000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd[/B][/B]

This error message now comes up each time I boot.

Is this a bug and should I report it.

---

### Post by oilchangeguy on 2007-08-08
you should be able to change this in the bios. locate number lock at boot (or something like this) and enable it.

---

### Post by bugster on 2007-08-08
> **oilchangeguy said:**
> you should be able to change this in the bios. locate number lock at boot (or something like this) and enable it.

Thanks.  I tried last night and this must be the only bios I've seen that makes no mention of number lock. :confused:

---

### Post by bugster on 2007-08-20
I've googled this problem and there are pages of people with similar problems with XKB going back to Breezy.  One thread lasts from September 2005 to March 2007 and nobody seems to know the anwer.

Is there any point in continuing with Ubuntu if the developers can't fix it ?

---

### Post by bugster on 2007-08-20
Is there any point in continuing with Ubuntu when 2 year old problems appear to be unresolved?

[B][SIZE="3"]Error activating XKB configuration
[/SIZE][/B]
If you Google this there are hundreds of others with similar problems.  I've read many and they rarely end with a fix.  My keyboard problem seems to be just one more without a fix.

I can't use it after months of trying different fixes.  

I have just given up.  Shame as there are so many satisfied Ubuntu users - I would really like to have been another.  But I can't persuade my family to use a system where the right half of the keyboard doesn't work properly.

Thanks to everyone who helped me  get as far as I did.

---

### Post by raja on 2007-08-20
Why are you repeating yourself from [this post]("http://ubuntuforums.org/showthread.php?t=520763") ?

---

### Post by willskills on 2007-08-20
Simple answer; buy a new keyboard? I know it's not a nice solution, but come on, they cost next to nothing....

---

### Post by bugster on 2007-08-20
Thanks willskills.  I've tried 4 keyboards both PS/2 and USB.  None works properly.

Thanks raja.  Answer, frustration.

---

### Post by wolfen69 on 2007-08-20
it's obvious you have the worst luck in the world.

---

### Post by Paul133 on 2007-08-20
None work properly. Hmm...I'm using a lappy so I can't helpmyou there, but certainly some Ubuntu users are using desktops and can recommend a keyboard for you.

---

### Post by bugster on 2007-08-20
Thanks wolfen69.

I don't think it's just my luck.  Seems I am amongst hundreds with the same unresolved problem over the last 2 years.  Try googling 

Error activating XKB configuration

---

### Post by bugster on 2007-08-20
Thanks Paul133.  I would be delighted to know of a Ubuntu compatible keyboard.

---

### Post by aysiu on 2007-08-20
> **raja said:**
> Why are you repeating yourself from [this post]("http://ubuntuforums.org/showthread.php?t=520763") ?
I've merged the two threads.

---

### Post by wolfen69 on 2007-08-20
i dont know what the differences are, but have you tried (during install) setting it up as a US English keyboard?

---

### Post by bugster on 2007-08-20
Thanks aysiu.  Two heads are better than one :)

---

### Post by bugster on 2007-08-20
> **wolfen69 said:**
> i dont know what the differences are, but have you tried (during install) setting it up as a US English keyboard?

Yes I've tried that to no avail - thanks for your response.

---

### Post by bugster on 2007-08-20
This thread goes on for nearly 2 years but unfortunately doesn't solve my problem

[https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/21595](https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/21595)

Does anyone else have any ideas?

---

### Post by Paul133 on 2007-08-20
Start a thread in hardware asking what keyboard people are using and whetherit works. Buy keyboard reccomended by fellow Ubuntu-er. Achieve satisfaction with Ubuntu and working keyboard.

---

### Post by bugster on 2007-08-20
Valuable advice Paul133 - I will do that tomorrow as it's late here in UK.  

But it does inspire the question, "Do users of Ubuntu have to consult others before buying a keyboard which will work with their computer?"

Since this problem has been around for a couple of years apparently, shouldn't the Ubuntu developers have recognised and addressed it?  

Windows users would not be so tolerant would they?  They go to their PC Superstore and buy a system which works straight out of the box.

Why can't Ubuntu users enjoy the same compatibility?

---

### Post by bugster on 2007-08-21
> **Paul133 said:**
> Start a thread in hardware asking what keyboard people are using and whetherit works. Buy keyboard reccomended by fellow Ubuntu-er. Achieve satisfaction with Ubuntu and working keyboard.

Thanks Paul133.

I started a thread in Hardware and listed the 4 keyboards I've now tried which all have the Numbers Lock problem.  Hopefully this should help other users avoid them.  I've been recommended a good value keyboard that is known to work so I'll probably get one.

I'm still troubled though that if I select anything other than Generic in System>Preferences>Keyboard I get the error message 


[B]Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70101000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd[[/B]

Surely this is a system error and not hardware? Why would 4 keyboards that work perfectly in Windows not work in Ubuntu?

---

### Post by bugster on 2007-08-22
I used 

gksudo gedit /etc/X11/xorg.conf

and commented out 3 lines in the text below

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	#Option	    "XkbModel" "pc15"
	#Option	    "XkbLayout" "uk"
	#Option	    "XkbVariant" "uk"
EndSection

I have rebooted a couple of times and it seems to work fine now. :)

---

### Post by bouncingmolar on 2007-10-13
> **bugster said:**
> I used 

gksudo gedit /etc/X11/xorg.conf

and commented out 3 lines in the text below

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	#Option	    "XkbModel" "pc15"
	#Option	    "XkbLayout" "uk"
	#Option	    "XkbVariant" "uk"
EndSection

I have rebooted a couple of times and it seems to work fine now. :)

I had the same problem when selecting different keyboard layouts in System>Preferences>Keyboard / layouts

So i also commented out : 
```

    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
#    Option         "XkbModel" "pc105"
#    Option         "XkbLayout" "usus"


```

then i pushed Ctrl Alt Backspace to restart X and i got this message
> 
The X system keyboard settings differ from your current GNOME keyboard settings.

Expected was model "pc105", layout "usus" and no options, but the the following settings were found: model "pc105", layout "us" and no options.

Which set would you like to use? 

I chose keep Gnome settings. 

Now it works! so Thanks mate. Lucky we didn't get new keyboards.

---

### Post by pinkunicorn on 2007-11-10
I'm also getting this error.

The output from the commands listed is this:

hans@owl ~ :-) xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "pc105", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "pc105", "", ""

hans@owl ~ :-) gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 model = microsoftpro
 options = []
 overrideSettings = true

I haven't yet been able to figure out what the actual problem is (i.e. what doesn't work). I'm typing this with the keyboard that I guess it's complaining about. The only problem I've seen as yet is the error dialog... :confused:

---

