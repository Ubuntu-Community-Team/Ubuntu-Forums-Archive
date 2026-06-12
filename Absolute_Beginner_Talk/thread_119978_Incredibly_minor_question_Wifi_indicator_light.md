---
title: "Incredibly minor question: Wifi indicator light"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by mohapi on 2006-01-20
I will understand completely if this post is ignored throughout eternity, but I thought I would ask.

I have a Dell XPS M170, and while the wireless (an Intel PRO 2200/BG) works perfectly out of the box, the indicator light never comes on.

I know, I know ... it's an infinitely stupid point. But I've spent about 20 minutes trying to search for something about it, but I can't seem to refine my search properly. And I'm one of those people that can't leave it alone. 

Anyone seen or know of a solution for this? Thanks in advance.

---

### Post by earobinson on 2006-01-20
I have a guess, a lot of hardware is [reverse engineered]("http://en.wikipedia.org/wiki/Reverse_engineering"), in linux It could be that whoever wrote the drivers for you card never figured out how to get the light blinking.

---

### Post by mohapi on 2006-01-20
That's okay. I can't complain because it works like a champ, even from the setup process. I thought I should ask though, if only to gratify my obsessive-compulsive tendencies. ... :-#

---

### Post by earobinson on 2006-01-20
Nothing wrong with asking at all, and infact you could file a [bug report]("https://launchpad.net/") just file it under a low priorty. Also that was just my guess I could be wrong, It happens a lot.

---

### Post by Sokraates on 2006-01-20
[quote=mohapi]I will understand completely if this post is ignored throughout eternity, but I thought I would ask.

I have a Dell XPS M170, and while the wireless (an Intel PRO 2200/BG) works perfectly out of the box, the indicator light never comes on.

I know, I know ... it's an infinitely stupid point. But I've spent about 20 minutes trying to search for something about it, but I can't seem to refine my search properly. And I'm one of those people that can't leave it alone. 

Anyone seen or know of a solution for this? Thanks in advance.[/quote]

Maybe a stupid question, but have you connected to a network via your wireless? On my HP nx6110 under windows the LED starts when WLAN is activated. Under linux it only starts, when an connection is made.

---

### Post by skirkpatrick on 2006-01-20
On my HP laptop, the light is on constantly when the wireless is active.  On my son's Acer laptop, the light flashes during activity.

---

### Post by matthew on 2006-01-20
Just thought I would chime in for data collection purposes...

On my AOpen laptop the light worked with Windows when I still used it. It has never worked under linux. However, the ipw2200 wireless internet connection is solid, consistent and fast.

---

### Post by mohapi on 2006-01-25
[QUOTE=matthew]Just thought I would chime in for data collection purposes...

On my AOpen laptop the light worked with Windows when I still used it. It has never worked under linux. However, the ipw2200 wireless internet connection is solid, consistent and fast.[/QUOTE]
This is identical to my experience. The wifi operates normally, with the exception of the indicator light. Under Windows, it is constantly lit unless I disable it via a function key, thereby shutting down the card completely. From my vantage, the  thing is more or less an idiot light for the card function, but irrelevant because of the onscreen indicator.

Anyways, I don't mind. It works fine.

---

### Post by earobinson on 2006-01-25
so I take it this means that the lights on your compuer are controled by sw instead of hw, I was always under the impresion that the lights that blinked on your computer just blinked whenever the card was used and was all hw

Guess I was wrong.

---

### Post by mohapi on 2006-01-25
I would have thought so too, but it seems there's some sort of software-trick that has to be triggered before it comes on.

---

### Post by earobinson on 2006-01-25
live and learn.... live and learn.... someone should write a program to make the lights dance lol

---

### Post by matthew on 2006-01-25
[quote=earobinson]so I take it this means that the lights on your compuer are controled by sw instead of hw, I was always under the impresion that the lights that blinked on your computer just blinked whenever the card was used and was all hw

Guess I was wrong.[/quote]Definitely software *controlled*. However, each laptop manufacturer has different hardware and under windows just installs a small software driver for their company's special hardware lights and buttons. Those drivers are not available for Linux, but occasionally some laptop owning computer stud reverse engineers their personal equipment and next thing you know a special button I have ends up working. Anyway, what I'm saying is that who knows? the little LED on my computer may start working someday under Linux as well as the special email button to the left of my keyboard just like some of my other special buttons already work.

---

### Post by earobinson on 2006-01-25
Ya I understand the HW problems

---

### Post by totfit on 2006-01-25
Well, one of my questions has been answered before I asked. I just installed Ubuntu dual booted with XP and am very happy. I was going to partition the whole drive of my laptop and make it Unbuntu only, but was worried about traveling and wireless. Sounds as if there aren't a whole lot of issues other than the light? Matter of fact I started to do it earlier and backed out. Guess I'll go ahead with it.

Gregg

---

### Post by David Corrales on 2006-02-01
I found out the answer to this problem searching the forums so here's it :) 

Go to the folder /etc/modprobe.d/ and create a file called **ipw2200** that contains:
```

options ipw2200 led=1

```

After rebooting my light is happily working :mrgreen:

---

### Post by mohapi on 2006-02-01
Ooh! Ooh! I must try NOW! :mrgreen:

(two minutes later)

Well, no love for me. That's OK. I'll learn to live with it. Somehow, I will carry on. ... :p

---

### Post by earobinson on 2006-02-01
lol thats really cool you have alight option. usefull for little kids using there computer late at night when they dont want mommie and daddy to know.

and maybe spies.....

it is because of things like that, that makes me love linux.

---

### Post by matthew on 2006-02-01
[quote=David Corrales]I found out the answer to this problem searching the forums so here's it :) 

Go to the folder /etc/modprobe.d/ and create a file called **ipw2200** that contains:
```

options ipw2200 led=1

``` 
After rebooting my light is happily working :mrgreen:[/quote]Darn. Didn't work for me. What laptop do you have? Mine is an [AOpen 1557gls]("http://www.geocities.com/ubuntumatthew/aopen1557gls.html")

---

### Post by David Corrales on 2006-02-01
It's a new Dell Inspiron 9300. You may have to reboot btw. My light is kinda weird though... sometimes it'll stay on, sometimes it does turn on/off but what the heck. I just like seeing the green thing there :mrgreen: 
I prefer to check the network applet on the panel to see if it's effectively on/off.

---

### Post by matthew on 2006-02-01
[quote=David Corrales]It's a new Dell Inspiron 9300. You may have to reboot btw. My light is kinda weird though... sometimes it'll stay on, sometimes it does turn on/off but what the heck. I just like seeing the green thing there :mrgreen: 
I prefer to check the network applet on the panel to see if it's effectively on/off.[/quote]Even after rebooting mine doesn't work. Oh, well. The wireless connection works perfectly and that's really what's important to me.

---

### Post by cbudden on 2006-02-01
David Corrales, thank you for the tip, my wireless light now works! (using Acer 4500 LMi)

---

### Post by Thorongil on 2006-02-24
Yeah, this rocks!

Just as a note: this should work on all Acer TM 4000, 4500, 2300 and Extensa 3000 models (these are essentially the same barebones)! :KS

---

### Post by tribaal on 2006-06-06
Man I've been trying to set this up for ages!

Mine wasn't working right after a reboot, but did once I turned the card off and then back on, for some reason (Fn-F2 twice on my Dell inspiron 9300).

Much love! Hurray! Cheers!

- trib'

---

### Post by CGW on 2006-08-04
This little fix also worked for my Dell 6000. Woo-hooo!!!

---

### Post by squigish on 2006-09-21
I created the /etc/modprobe.d/ipw2200 file, with the content "options ipw2200 led=1", but got no results, even after restarting and enabling/disabling my wireless.  I downloaded a new driver (although I didn't end up needing to install it) from [the ipw2200 sourceforge page]("http://ipw2200.sourceforge.net/index.php"), and read the readme file, which described the ability to set parameters for the driver using the modprobe command.

So,  I ran ```
sudo modprobe ipw2200 led=1
``` 

And then disabled/re-enabled my wireless card using the fn+f2 hardware switch.

Now my LED seems to work, although it seems it may be stuck on, even when the wireless card is disabled.  At any rate, running ```
sudo modprobe ipw2200 led=0
``` turns it off again.  I have no idea what will happen when I reboot.  

I'm using an Intel Pro Wireless 2200BG wireless card on my Dell Latitude D610 laptop.

---

### Post by ramcosca on 2006-09-21
> **earobinson said:**
> live and learn.... live and learn.... someone should write a program to make the lights dance lolYou know, I had that on Windows. It was a program that took control of the keyboard's LEDs (Num Lock, Caps Lock, Scroll Lock) and turned them on/off with music or when the HDD was accessed, RAM was accessed (turned on 99% of the time, lol) and... I don't recall the third one, though.


I use a WiFi dongle and the LED works wonderful. Turns on/off when communicating with my wireless modem. :p

---

### Post by arkangel on 2006-09-21
> **mohapi said:**
> I will understand completely if this post is ignored throughout eternity, but I thought I would ask.

I have a Dell XPS M170, and while the wireless (an Intel PRO 2200/BG) works perfectly out of the box, the indicator light never comes on.

I know, I know ... it's an infinitely stupid point. But I've spent about 20 minutes trying to search for something about it, but I can't seem to refine my search properly. And I'm one of those people that can't leave it alone. 

Anyone seen or know of a solution for this? Thanks in advance.



I have an asus A6va , all works like a charm too ,  but mine is always on :tongue: 

i do #cat /proc/acpi/asus/wled 
and i got 1 
so i assume some where must be a way to turn in off

---

### Post by sergiothatguy on 2007-08-31
> **Sokraates said:**
> Maybe a stupid question, but have you connected to a network via your wireless? On my HP nx6110 under windows the LED starts when WLAN is activated. Under linux it only starts, when an connection is made.

Yeah, same here. I was worried my wireless card driver was messed up, but the internet works fine. It is just that the blinking is so annoying while its not connected =P

---

### Post by zekonology on 2007-09-19
No luck here... I'm using Dell Inspiron 1420 running Gutsy tribe 5. wifi works like charm but no indicator. Last time i used Feisty and upgrade to 2.6.22-11 kernel, got the iwl4965 compiled the indicator works but after couples of seconds, my lappie stuck. i've to turn it off completely by pressing the power button. Any suggestion on this new Gutsy? the wifi card is intel 4965AGN.

---

### Post by isilmeraumo on 2008-01-27
A quick way to find out if your wifi driver supports the LED option is to just type this in a temrinal:
   modinfo <wifi driver>

i.e. modinfo iwl4965

What this does is get all information about the module, including any options it will take.  You can tell the options by the type "parm" that will be on the left and the option name and description will be to the right.  Anyways, good luck.  I am still trying to figure out how to turn the light on for my wifi in my thinkpad x61t.  I found an led option under proc but I am unsure of what it wants as input.  It seems to control at least 7/8 of the LEDs.  If anyone has had luck with this laptop, let me know.  I am also working on finding out how to turn the device back on after powering off.  It seems the switch turns it off but not back on.  I see the same functionality in Windows, but in Windows I can use the Lenovo software to "Activate" the radio.

---

