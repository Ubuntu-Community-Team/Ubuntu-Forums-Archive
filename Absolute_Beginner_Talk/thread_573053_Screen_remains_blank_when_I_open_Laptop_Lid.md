---
title: "Screen remains blank when I open Laptop Lid"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by TWO on 2007-10-11
Admittedly, my laptop isn't the prettiest of them all. I have a Dell Inspiron 1300 and the specs probably aren't worth mentioning, but the problem is that whether or not I set Ubuntu to make a blank screen or not when I close the lid, the screen goes blank and nine times out of ten, no amount of button mashing will bring my screen back and I'm forced to reset. 

Does anybody have any suggestions as to what could be the problem?

And before you ask, yes I am a 'noob', or however you refer to newbies, but I've played with it to enough to have an understanding of the basics.

---

### Post by netventure on 2007-10-11
> **TWO said:**
>  whether or not I set Ubuntu to make a blank screen or not when I close the lid, the screen goes blank and nine times out of ten, no amount of button mashing will bring my screen back and I'm forced to reset. 

I have similar problems when I enable power saving, i.e., monitor standby or suspend. As a test, go to the Power Manager and disable system and monitor standby/suspend (move the slider to "never").


> **TWO said:**
> And before you ask, yes I am a 'noob', or however you refer to newbies, but I've played with it to enough to have an understanding of the basics.

It's actually great to see a newbie using linux. It's users like you and your questions that make the ubuntu team make improvements to usability.

--NV

---

### Post by cowkiller on 2007-10-11
hmmm I assume that the laptop keeps working... so, I would try to press the power on/off button... it may sound a stupid solution, but you never know. 
Another solution would be disabling the **acpi**... but I can't help you on that. Anyway, I'm sure that you'd find something useful about that on this forum or just searching in google

---

### Post by TWO on 2007-10-30
Yes, the laptop is still switched on but the screen remains blank.

I recently updated to Gutsy Gibbon and the blank screen issue doesn't seem to exist. However the downside was that there was a sound card issue and I have since reinstalled Feisty Fawn- which I'll keep until that issue is fixed.

I'll look into the suggestion about the 'acpi' thing that you mentioned though...

Oh yes, I did try your suggestion of moving the sliders in power management to never but the problem is still there...

Do you reckon that this is an issue with all Inspiron 1300s??

---

### Post by magicrobotmonkey on 2007-10-31
sometimes the screen just "forgets" to turn back on - i used to have that in feisty, try hitting ctrl+alt+F1 then ctrl+alt+F7

---

### Post by TWO on 2007-11-01
> **magicrobotmonkey said:**
> try hitting ctrl+alt+F1 then ctrl+alt+F7

The keyboard shortcut didn't work for me!! What is it supposed to do?

---

### Post by tw0shoes on 2007-11-01
ctrl-alt f1 goes to the command line
ctrl-alt f7 goes back to the GUI. 

I'm also having this problem. 
Mouse and Keys don't work. 

Check if it happens when your computer isn't on AC power. I think i remember it having something to do w/ laptop mode.

---

### Post by TWO on 2007-11-01
> **tw0shoes said:**
> 
Check if it happens when your computer isn't on AC power. I think i remember it having something to do w/ laptop mode.

You're right! I tried doing it with the AC disconnected and the screen reappeared fine!

Where did you read about that? Also, do you have any idea what I might need to configure to stop it from happening whilst on AC power?

---

### Post by LowSky on 2007-11-01
if its a dell laptop try the fuction key (Fn) + plus the key that has a monitor on it (mine is F7), press it one to three time and your monitor might come back up.
This little trick works on mine.

---

### Post by TWO on 2007-11-01
I tried the function key option on my Dell. I don't have a screen icon on my f7 but I tried that, and then the function key F8 which has CRT/LCD written on it but to no avail.

However, what I have discovered is that when the power management is set to 'do nothing' on AC power and you close the lid, my laptop goes blank anyway and doesn't return, however when I set it to 'blank screen' it appears with a locked screen. Success!

I'm not too sure why I hadn't tried that before, however I have reinstalled Ubuntu a couple of times when I was trying its different distros a few months ago and I am sure I had the option set yet had the same problem. 

Also discovered that in the event of the screen remaining blank, simply unplugging the laptop and opening and closing the lid once or twice, brings it back. 

I'm about to try the 'do nothing' setting on battery power and see if there is an issue with that particular setting as well.

It's a shame that the problem is there but at least the workaround isn't difficult -assuming everyone has the same symptoms. 

I suppose I could just update to the latest distro, but there is another issue on Gutsy with my laptop so Feisty is doing the job just fine!

---

### Post by TWO on 2007-11-01
> **TWO said:**
> 
I'm about to try the 'do nothing' setting on battery power and see if there is an issue with that particular setting as well.



OK, so I've just set ubuntu to 'do nothing' when I close my lid on battery power, and on opening the lid funnily enough I was presented with the infamous blank screen. 

It looks like- well for my laptop at least- that there is an issue with the 'do nothing' setting. Set both to 'blank screen' and the problem doesn't seem to be there. I feel a little silly for not having worked this out sooner, but it is funny at the same time because I believed that the 'blank screen' setting was the culprit (for obvious reasons!) 

Nice to know I can actually shut my lid and not have to worry about the screen reappearing, and equally nice to know that that's now one less reason to use my Window's partition!

---

### Post by tw0shoes on 2007-11-01
I didn't read about it anywhere. I had changed my settings so that my laptop was in laptop mode while on AC and noticed the change. So i figured that since your laptop is in laptop mode when it isn't plugged in that the same thing would happen. 
I don't think it's recommended that you keep your computer in laptop mode though while it's plugged in on account of the "aggressive power saving" features that some laptops come with. Someone will know better than me though about that.

---

### Post by charlie3684 on 2007-11-03
I have a Dell Inspiron 1300 and my screen would always go blank if I was in terminal and i closed the lid, then reopen it the screen will stay off.  I would have to go back to X using "CtrL ALT F7" to get the screen to turn back on.    

My friend accident helped me out on this and figured out it had to deal with the ACPI.  Back up this file first and try using this instead of what's in your lid.sh.   

```

#!/bin/bash

. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/policy-funcs
. /etc/default/acpi-support

grep -q open /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
vbetool dpms on
        fi
    done


```

Hopefully that helps out!

---

### Post by Jonathin on 2007-11-06
I have this issue with my Thinkpad. I have only tested it while my computer is connected to AC power.

I noticed, when I opened the lip, the monitor DOES come on, and some command prompt stuff runs very quickly down the screen, and then nothing happens. I noticed that after the text shows up, (it flashes quickly, I can't read it) and the screen goes blank, the light on my USB device shuts off.

---

### Post by jordanmthomas on 2007-11-06
A not-so-great "solution" is to bind a key on your keyboard to run this:
```
xset -display :0 dpms force on
```
I use the Menu key since basically useless anyway.

---

### Post by Jonathin on 2007-11-06
I just confirmed that my screen stays blank on both AC power and Battery power after I close the lid.

---

### Post by secularscope on 2007-11-06
> **charlie3684 said:**
> ..Back up this file first and try using this instead of what's in your lid.sh.   

```

#!/bin/bash

. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/policy-funcs
. /etc/default/acpi-support

grep -q open /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
vbetool dpms on
        fi
    done


```

Hopefully that helps out!

Thank you so much, this helped on my Dell Latitude D820.

---

### Post by charlie3684 on 2007-11-07
> **secularscope said:**
> Thank you so much, this helped on my Dell Latitude D820.

Np,  this seems to mostly work for Dell laptops.  I'm not sure about another brands.

---

### Post by TWO on 2007-11-08
> **Jonathin said:**
> I just confirmed that my screen stays blank on both AC power and Battery power after I close the lid.

Jonathin

Did you try to do this whilst having your power management set to "Blank Screen" on both AC power and Battery Power? I found that having the setting as "Do Nothing" was the cause of the problem, but I'm not really sure why...

---

### Post by axm on 2007-11-10
[_solution to the dell specific screen does not recover problem_]("http://ubuntuforums.org/showthread.php?t=358432")

---

