---
title: "Adjusting brightness without Fn-button"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by janki on 2007-04-03
I have a laptop with Breezy Badger installed. The Fn-button doesn't work, and I can't find a way to adjust the brightness of the display. Does anybody have any tips? Thanks!

---

### Post by NikoC on 2007-04-03
Which video card do you use? In case of Nvidia there is a small app that lets you set brightness via terminal
```
sudo apt-get install nvclock
```

For example to set brightness to 100% just type:
```
nvclock -S 100
```

My function keys do work (Feisty) but I don't use them anymore, way quicker in terminal ;)

Edit: there is also a way to manually configuring the function keys, just do a search on the forum

---

### Post by janki on 2007-04-03
When I tried running nvclock it told me I don't have an Nvidia card. Stupid question, but how can I check which card I have?

But isn't there a simple command from the terminal or an applet that lets me adjust the brightness independent of which video-card I have?

---

### Post by pxwpxw on 2007-04-03
to check video card:
```

lspci | grep VGA
#### or just
lspci
### or 
sudo lshw | less

```

---

### Post by NikoC on 2007-04-04
You might want to do a search in title  on the forum typing  'shortcut keys' or 'brightness'. Depending on the brand of your laptop different solutions are offered.

---

### Post by janki on 2007-04-06
I ran the command given by *pxwpxw* and found out which video card I have:
```
ATI Technologies Inc Radeon R250 Lf [Radeon Mobility 9000 M9] (rev 01)
```

But I still haven't been able to resolve the problem of adjusting the brightness without using the Fn-button. Isn't there an easy way to adjust brightnes in Ubuntu?

---

### Post by freebird54 on 2007-04-06
I haven't heard of an OS with a means of adjusting brightness - in my experience it is a hardware function of the monitor.  However - what we probably need is a way of getting the Fn key to work!  

What laptop is it?  Difficult to search for solutions without being able to narrow it down a little....

---

### Post by pxwpxw on 2007-04-06
In xubuntu610 there is a Display settings gamma control that does it for
my applemac ibookg4 with ATI card.I don't remmember what is in Breezy.

Search for "screen brightness" finds several threads in the 
 Hardware & Laptops forum

[http://ubuntuforums.org/forumdisplay.php?f=135](http://ubuntuforums.org/forumdisplay.php?f=135)

a good one:

[http://ubuntuforums.org/showthread.php?t=149539&highlight=screen+brightness](http://ubuntuforums.org/showthread.php?t=149539&highlight=screen+brightness)

Use the search.:)

---

### Post by Bashed on 2007-05-10
Can someone help me enable 32bit on my laptop please?

chad@Secured:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

I have a Sony Vaio laptop with 1280x800 widescreen

---

### Post by lambfrier on 2007-06-16
Here's a solution that I'm using at the moment.  It may be a little complex for "Absolute Beginner Talk", but could be good for learning...

I have an Asus laptop and from a fresh Feisty install, not all of the hotkeys work.  The Fn combinations for volume control, sleep, etc. work, but the brightness keys don't.  I suspect it has something to do with the keyboard mapping as neither acpi_listen nor 'xkeybind -k' register keyboard events for these keys.

I was using Gnome Power Management (System->Preferences->Power Managerment) to adjust the brightness, but this was a little long-winded.  At the time, I don't believe the Brightness Applet worked for me so I looked for another solution.  I just tried the Brightness Applet again, and it works, so a simple solution to the problem would be:

- right click on the top panel
- select Add to Panel...
- select the Brightness Applet (under System & Hardware)
This should give you a brightness slider when you click on it.


Since I've started this reply, I may as well continue with my original solution which was to map keyboard shortcuts:

Firstly, I found somewhere on the forum how to get Gnome's brightness value via command line.  Try typing this in a terminal:
```
gconftool-2 --get /apps/gnome-power-manager/ac_brightness
```

I used Perl to create a small script which I named 'brightness-adjust':
```
#!/usr/bin/perl
$val = shift;
$b =`gconftool-2 --get /apps/gnome-power-manager/ac_brightness`;
$b += $val;
if (($b < 0) || ($b > 100)){exit}
`gconftool-2 --type int --set /apps/gnome-power-manager/ac_brightness $b`;
```

Note: the quotes are back-quotes, telling Perl to execute these commands

This file needs to be made executable:
```
chmod 755 brightness-adjust
```

Then you can supply it with a value to increment or decrement the brightness:
```
./brightness-adjust -20
```


The second part was to install xbindkeys to map keyboard combinations to this command:
```
sudo aptitude install xbindkeys
```

I copied 'brightness-adjust' to /usr/bin, and added the following lines to my ~/.xbindkeysrc file:
```
"/usr/bin/brightness-adjust -5"
  Mod4 + F5
"/usr/bin/brightness-adjust 5"
  Mod4 + F6
```

This mapped them to the <Meta>F5 and <Meta>F6 key combinations.  (The Meta key is also known as the Windows key or Super key so the combinations are very close to the <Fn>F5 and <Fn>F6 Hotkeys that Asus have specified on my laptop).  You can check your own combinations using 'xbindkeys -k'.  You also need to need to restart xbindkeys before your combinations come into effect:
```
killall xbindkeys
xbindkeys
```

For more info about the xbindkeys program, you get the 'manual' by typing:
```
man xbindkeys
```

Once this is working as you like it, you'll probably want to make sure xbindkeys starts every time you login:
System->Preferences->Sessions->New
type xbindkeys in both fields

That's about it.  
There are some changes you could make, e.g. changing the xbindkeys calls to increment by +/-10 if you think the changes are too gradual, or changing the code to also work when on battery power.

---

### Post by freebird54 on 2007-06-17
One suspects that some update or other affected the workings of the applet - so it was probably NOT you that misinterpreted its workings.. :)

Exellent job of creating (and documenting) a workaround - and I think this *IS* the place for it.  Thanks....

---

### Post by Peacepunk on 2008-04-19
thanks lambfrier

that worked like a charm on my Vaio VGN-T17GP running... Fedora7 :)

Now. let's get picky: **How do I get visual feedback, sound-applet-like, of this script?**
[Bug or feature, the Gnome-Brightness-Applet doesn't get updated & shows the previous value until manually refreshed]

for anyone interested, here is the code to make it work both on battery and on power:

```

#!/usr/bin/perl
$val = shift;
$a =`gconftool-2 --get /apps/gnome-power-manager/ac_brightness`;
$b =`gconftool-2 --get /apps/gnome-power-manager/battery_brightness`;
$a += $val;
$b += $val;
if (($a < 0) || ($a > 100) || ($b < 0) || ($b > 100)){exit}
`gconftool-2 --type int --set /apps/gnome-power-manager/ac_brightness $a`;
`gconftool-2 --type int --set /apps/gnome-power-manager/battery_brightness $b`;
```

---

