---
title: "HELP gutsy hangs on /etc/rc.local after trying to config dual monitors."
date: 2007-12-29
forum: Apple Intel Users
---

### Post by changuito on 2007-12-29
Hello-

I would be grateful if someone might be able to pin down what is wrong with my system. I wasnt expecting anything this drastic to happen, and so i only have some scattered recollection of what happened.

Breifly, yesterday, I had my external monitor mirroring my laptop screen in gutsy with minimal effort. Today I was using the system panel in admin mode and tried to set up a dual monitor system, which I decided against (because of the resoultion) and was trying to reconfigure as I had it working yesterday. Since I was having problems getting it to what I had yesterday, I decided to restart. Then the issues started. It was having issues logging in and i realized that it was probably xorg.conf that was to blame. Luckily, I had a backup of it already in place and copied it over. Then i rebooted and everything was fine. Now, I dont know what i did next, but for some reason I rebooted again and now gutsy always hangs while booting at local bootscripts /etc/rc.local. Hitting return and/or ctrl-c is fruitless (and i've read all the posts i could find on this topic). From here i do an alt-F1 and then login and then try to startx. I get (these seem to be the highlights)

EE  AIGLX: screen 0 is not DRI capable
EE PreInit returned NULL for "Configured Mouse"

and a bit further down:
X10: fatal 10 error 104

Any ideas? (All i really wanted to do today was get some work done.... arg)
Help is tremendously appreciated. Thanks.

---

### Post by Zaff on 2007-12-30
First, what kind of macbook do you have ? is it a intel-based or Sata-Rosa ? Is it MAc Book Pro ? the graphics card changes from one to the other and (I'm no expert in this) so can the solution.
From my own experience, you should never use Gutsy's Screen and Graphics dialog as it is not stable AT ALL. I got trouble with that once.
If you have an intel based macbook (not macbookpro) you can probably use my xorg.conf. I will attach it to this message.
As for the dual screen set up. I use xrandr. Check out : [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2), it should help you set it up with pretty much whatever resolution you want.
Hope this helps

---

### Post by changuito on 2007-12-30
Thanks Zaff-

I solved the problem, it was some lines i had previously added to my xorg.conf that was causing the problem because my backup wasnt the good one. Your xorg.conf file gave me enough to work with and figure it out. 

So the lesson here is backup your xorg.conf before trying trying anything with dual monitors from the system control panel.

---

### Post by changuito on 2007-12-30
nice, i am loving xrandr. seems wierd this isnt built into ubuntus manager.

i was trying to set the F7 key as per the instructions on 

[http://www.thinkwiki.org/wiki/Sample_Fn-F7_script]("http://www.thinkwiki.org/wiki/Sample_Fn-F7_script")

but it's not working. (no big deal, it's easy enough to just run a simple bash script...) but it's probably an easy deal if you not a total noob. I think the issue lies here:

> 
# echo enable,0x084e > /proc/acpi/ibm/hotkey 


since theres no such ibm directory on my system. i could not pin down any equivalent with my limited hacking.

thanks in advance

---

