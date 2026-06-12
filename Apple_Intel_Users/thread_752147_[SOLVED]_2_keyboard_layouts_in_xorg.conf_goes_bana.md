---
title: "[SOLVED] 2 keyboard layouts in xorg.conf goes bananas...."
date: 2008-04-11
forum: Apple Intel Users
---

### Post by rytmisk on 2008-04-11
Now I am really confused. I have finally come around to installing ubuntu hardy on my macbook santa rosa and am in the process of configuring it. I need to use something other than gnome (because gnome handles windows strangely on a program I am depandant on), and I like icewm better anyway. One problem of not using gnome or kde is the lack of a proper keyboard switcher applet so I had to do it in xorg.conf.

Well I googled a lot and ended up with the following section in xorg.conf:```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se, no"
	Option		"XkbVariant"	"mac"
        Option         "XkbOptions" "grp:alt_shift_toggle" ##<-- Enables Alt+Shift

EndSection
```

I also added fbxkb to be abke to switch graphically as well as with keyboard. And it works - except tat the second language is garbled. In the above version of xorg.conf Swedish is working perfectly, but when I switch to Norwegian some of the keys give different letters/symbols. I think they might be third level letters. the top row of letters which should be "qwertyuiopå" is "@&#322;€®þ&#8592;&#8595;&#8594;œþ¨" 

The strange thing is that if I write "no" before "se" in the xorg.conf file,

```
	Option		"XkbLayout"	" no, se"
``` it is Swedish that is screwed up... The difference between the keyboard layouts are minor really, but there are 2 letters that are different, and these work - but this is useless since I have to switch keyboard layout from one letter to the next...

Does anyone have any idea of how to fix this??

Best regards
Ketil Thorgersen

---

### Post by cyberdork33 on 2008-04-11
I can't help directly, but I wanted to mention that gnome is not a window manager... you can use the gome environment with icewm as the window manager I think... By default gnome uses metacity as the window manager, but you can change that to icewm just like to change to compiz if you use that.

---

### Post by rytmisk on 2008-04-11
Hm 

I actually hadn't thought about that. I really do not want to go back to gnome, but if I can't solve this, I might give it a try.

Thanks!
Ketil

---

### Post by rytmisk on 2008-04-12
Please someone???

Ketil

---

### Post by rytmisk on 2008-04-15
Ok - I kind of fixed it. Through a workaround as usual...

I found a [thread]("http://ubuntu.sabza.org/2006/10/13/xubuntu-easily-switch-keyboard-layout/") which explained another way of switching between keyboard layouts by making an executable file /usr/bin/fixkeyboard containing the following code```
#!/bin/bash
setxkbmap -option grp:switch,grp:alts_toggle se,no
```
I put it in my &#733;/icewm/startup file after my ~.xmodmap (if the xmodmap is run after the fixkeyboard it won't work). I am now happily changing between the keyboard layouts with alt+shift. fbxkb - the gui changer from xfce is unfortunately not working though.

So not solved, but working:-)

Ketil

---

### Post by cyberdork33 on 2008-04-15
Please use the "thread tools" menu at the top to mark as solved.

---

