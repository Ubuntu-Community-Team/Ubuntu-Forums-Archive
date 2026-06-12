---
title: "[SOLVED] Key &amp;quot;sticking&amp;quot;"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by VorlonShadow on 2007-10-03
I just finished installing Ubuntu.  Things are going alright, except for the fact that while I'm talking, sometimes keys will "stick".  In other words, I may type "www.google.com", and it'll add an extra w, so I get wwww.google.com. This happens frequently.  I am running it inside of a Virtual PC environment, so I don't know if this makes a difference or not, but it seems that when I'm typing pretty quickly is when this happens.  If I slow down, it seems OK.  Any ideas?

Thanks,
Jesse

---

### Post by julian67 on 2007-10-03
> **VorlonShadow said:**
> I just finished installing Ubuntu.  Things are going alright, except for the fact that while I'm talking, sometimes keys will "stick".  In other words, I may type "www.google.com", and it'll add an extra w, so I get wwww.google.com. This happens frequently.  I am running it inside of a Virtual PC environment, so I don't know if this makes a difference or not, but it seems that when I'm typing pretty quickly is when this happens.  If I slow down, it seems OK.  Any ideas?

Thanks,
Jesse

It can be from the wrong keyboard being specified i.e. havng a 104 kbd in xorg.conf when really you use 105 key keyboard.

Or it can be food crumbs or gum under the keys.

---

### Post by VorlonShadow on 2007-10-03
The driver is most likely the problem.  It's set to 101/102 IBM Enhanced.  It's actually a 105 key Microsoft keyboard.

There's nothing physically wrong with the keyboard, because I use it in Windows, and it works perfectly.

So, I'm a newbie to this whole thing.  I'm used to Windows.  How do I change the driver to the right keyboard?

Thanks,
Jesse

---

### Post by julian67 on 2007-10-03
You need to edit /etc/X11/xorg.conf

1st back up your old xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Now you can use vim or  gedit or any other text editor

```
gksudo gedit /etc/X11/xorg.conf
```

and find 

Section "InputDevice"

under which you'll find your keyboard described. Mine is UK (gb) keyboard with 105 keys and the config looks like this:

 > Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
        Option          "XkbOptions"    "lv3:ralt_switch"


You should remove any reference to 101/102 IBM and instead make sure you have the line 

Option          "XkbModel"      "pc105"

Save the changes and then you will need to restart X. Ctrl-Alt-Backspace will do it

---

### Post by VorlonShadow on 2007-10-03
Just went through those steps. Things seemed to go well.  After changing it to read "105", and re-starting the GUI, I brought up a text edit and did some typing.  No go...

Rapid typing really seems to choke it down.  For instance, if I type [www.google.com](www.google.com), the "www" is typed very quickly,  in the text editor, I ended up with over 400 w's before it finally stopped.  It did the same thing with the "d" key the other day too.

Any other ideas?  Or will I simply have to learn to type slowly? (very hard thing to do for me).

Thanks,
Jesse

---

### Post by Nehvrook on 2007-10-03
I may be wrong, but aren't you all going for the most complex problems first. If you've just installed Ubuntu the chances are you haven't had chance to configure it and look around much. Have you tried going to 

System > Preferences > Keyboard

and played around with the delay under repeat keys? I had the same symptoms you had when I first started using Ubuntu, and that was the cause.

---

### Post by julian67 on 2007-10-03
I think reconfigure X. 

I'm assuming your old xorg.conf is still backed up and that evrything else worked (monitor, mouse etc), you'll be needing it.

Now reconfigure X

```
sudo dpkg-reconfigure xserver-xorg
```

Do it the best you can but don't worry too much about most of it, what we really want is the keyboard config, so get that right if you can. When it's done it will write the new xorg.conf and back up your current one (I think it will append the date to the filename).  Don't reboot or restart X yet. From the new xorg.conf copy the keyboard section (Section "InputDevice") and copy this over to your original xorg.conf.bak and save it.  Again you can "gksudo gedit" to do this. Now your xorg.conf.bak *should* be good for your monitor, mouse, keyboard etc, so

```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

Restart X Ctrl-Alt-Backspace and it should work......

---

### Post by julian67 on 2007-10-03
> **Nehvrook said:**
> I may be wrong, but aren't you all going for the most complex problems first. If you've just installed Ubuntu the chances are you haven't had chance to configure it and look around much. Have you tried going to 

System > Preferences > Keyboard

and played around with the delay under repeat keys? I had the same symptoms you had when I first started using Ubuntu, and that was the cause.

you might be right :lolflag:

---

### Post by VorlonShadow on 2007-10-03
> **Nehvrook said:**
> System > Preferences > Keyboard

and played around with the delay under repeat keys? I had the same symptoms you had when I first started using Ubuntu, and that was the cause.

That was it!! I increased the Delay for the repeat from short to about the middle of the bar, and it's working perfectly now.  Takes a little longer to kick in the repeat, but I'm Ok with that.

Thanks for the help!

Jesse

---

### Post by Nehvrook on 2007-10-03
Awesome, glad I could help :D

Mark the thread as Solved incase anyone is searching for similar things

Have fun with Ubuntu :)

---

### Post by remitaylor on 2007-10-25
> **Nehvrook said:**
> Awesome, glad I could help :D

Mark the thread as Solved incase anyone is searching for similar things

Have fun with Ubuntu :)

I don't think this is solved.

PLEASE un-mark this as solved and SOMEBODY *PLEASE HELP* ... I would do anything to fix this ...

I've been struggling with this problem for months and it's killing me.  After upgrading from Edgy to Feisty, this problem kicked in.  I tried to fix if for about 2 weeks and have to switch to another distro.  When Gutsy came around, I tried the LiveCD and had the same problem.  Then I randomly tried again andddddddddd (<-- perfect example)                     (<-- again!! the stupid space ...) and the LiveCD worked so I installed Gutsy.  Upon reboot ... the problem returned.

Note: I typed the above using the "FIX" that this thread provides.  Playing with the repeat makes this happen less, but the keyboard still sticks, even though it repeats less.  In other words ... I get less of thissssssssssssssssssssssss (<-- actually happened!) ... but I get more of this:

The quick fox jumps [hangs for a few seconds] zy dog.

Please.  I'll spend an hour a day trying to help users via the forums ... I'll send someeeeeeeeeeeeeeeeeeeeone flowers.  Better yet - cookies.

PLEASE  :(

---

### Post by remitaylor on 2007-10-25
Note, what I've tried before ... I've tried what this threaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaad says (changing the delay in prefs > keyboard).

Someone here [[http://ubuntuforums.org/showthread.php?t=185979]](http://ubuntuforums.org/showthread.php?t=185979]) saaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaid that this [[http://ubuntuforums.org/showthread.php?t=75281]](http://ubuntuforums.org/showthread.php?t=75281]) fixed it, for that person's hardware.

Incase it means anything, this is what the 32bit boot options did for me:

1) noapic nolapic
came up to login and i couldn't type at all.  after typing in the username box for awhile, a key was eventually recognizzzzzzzzzzzzzzzzzzzzzzzzzzzzed and it repeated that key, seemingly forever

2) noapic acpi=noirq
seemed ok - logged in - but i had repeat issues (as early as hitting alt+f2 to get a terminal to test in)

3) noapic acpi=off
same as 1)

4) noapictimer
"failed to set xfermode" during boot.  dropped to busybox

5) noapictimer irqpoll
same as 4)

6) noapic acpi=noirq nolapic
same as 1) and 3), except the system wouldn't even shutdown when i tried to restart from the login screen ... had to unplug the laptop and remove the battery.

Dunno if any of that means anything.  I'm just still desperately seeking a solution besides either going back to Edgy or                                    going back to using another distro.  I *love* Gutsy (have it on my other desktop machines) and hope I eventually find a solution for this box.

Incase this helps search queries ... this is a Fujitsu Lifebook N6010, Intel Pentium4 3.2GHz, with an ATI Mobility Radeon 9700.  Problem present in Feisty & Gutsy 32bit i386 desktop.

**a few other threads with the same issue, for reference ...**
* [intermittent mad keyboard repeat] [http://ubuntuforums.org/showthread.php?t=467012](http://ubuntuforums.org/showthread.php?t=467012)
* [Keys repeat and get stuck on!] [http://ubuntuforums.org/showthread.php?t=432057](http://ubuntuforums.org/showthread.php?t=432057)
* [Keyboard input just went haywire] [http://ubuntuforums.org/showthread.php?t=315872](http://ubuntuforums.org/showthread.php?t=315872)
* [keyboard repeat problem] [http://ubuntuforums.org/showthread.php?t=170518](http://ubuntuforums.org/showthread.php?t=170518)
* (older) [Keyboard repeat/delay :: PLEASE HELP!! I don't want to leave Ubuntu!!!] [http://ubuntuforums.org/showthread.php?t=54171](http://ubuntuforums.org/showthread.php?t=54171)

launchpad bug reference (as mentioned in julian67's reply), for reference - [https://bugs.launchpad.net/ubuntu/+bug/124406](https://bugs.launchpad.net/ubuntu/+bug/124406)

**all potential matches from launchpad**
* [Keyboard keys stuck using Feisty + Xgl + Compiz Fusion] [https://bugs.launchpad.net/ubuntu/+bug/124406](https://bugs.launchpad.net/ubuntu/+bug/124406)
* [Keyboard random repeat and dropped key presses] [https://bugs.launchpad.net/ubuntu/+bug/39315](https://bugs.launchpad.net/ubuntu/+bug/39315)
* [spurious keyboard events] [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63024](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63024)
* [Erratic keyboard repeat] [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/55843](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/55843)
* [keyboard strokes registered repeatedly or not registered at all] [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/65249](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/65249)
* [[rt61] Lockups running Feisty on x86-64] [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90243](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90243)
* [repeate rate problem, sometimes repeats character many times while typing.] [https://bugs.launchpad.net/ubuntu/+bug/92594](https://bugs.launchpad.net/ubuntu/+bug/92594)
* [[Feisty] Keyboard repeats keystrokes like tttthiiiiiiiiiiiissss] [https://bugs.launchpad.net/ubuntu/+bug/99356](https://bugs.launchpad.net/ubuntu/+bug/99356)
* [Randomly repeating mousestrokes/keystrokes in Gutsy RC1 under KDE] [https://bugs.launchpad.net/ubuntu/+bug/153024](https://bugs.launchpad.net/ubuntu/+bug/153024)
* [keyboard keys repeat in GNOME for single keypress] [https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/11143](https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/11143)

**Fixes to try ...**
* start with ec_intr=0, per [#99356]("https://launchpad.net/ubuntu/+bug/99356") [,per [kernel problem on thinkpad r40e]("http://ubuntuforums.org/showthread.php?t=402926")]
* start with acpi=off, per [#99356]("https://launchpad.net/ubuntu/+bug/99356")
* remove i8kutils, per [#63024]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63024")
* start with notsc, per [#99356]("https://bugs.launchpad.net/ubuntu/+bug/99356")
* start dbus before acpid, per [#99356]("https://bugs.launchpad.net/ubuntu/+bug/99356")

---

### Post by julian67 on 2007-10-25
If your problem is part of the bug referenced at lauchpad then you would be better off going back to edgy for the moment, assuming this was the last version of Ubuntu which was satisfactory for you.  Meanwhile you can subscribe to the bug report and be automatically updated of any progress.

I would try one more thing though. I'm assuming Edgy worked OK and you still have, or can get, and Edgy live CD. My suggestion is to boot the live Edgy CD and note down any changes between the xorg.conf that works in Edgy and the xorg.conf in your non-working system.  When you boot back into your regular OS apply any relevant changes, making sure correct modules are loaded if needed, and reboot. Perhaps the best way is to run ```
sudo dpkg-reconfigure xserver-xorg
``` using your edgy xorg.conf as a guide. 

If this failed I would go back to edgy or dapper for the moment, or if there are pressing reasons to be using something more recent then try out some live CDs from other distros and you might find one that works better for you. Mepis will feel reasonably familiar to an Ubuntu user. openSUSE and Mandriva latest releases are getting a lot of praise and are often an excellent choice for laptops.

---

### Post by remitaylor on 2007-11-06
A bit of news for this bug, if anyone is having this issue ... I posted a [$250 bounty]("https://launchpad.net/bounties/bug-124406-keyboard-hangs-repeats")

Subscribe to the bounty for updates.  I also keep updating my post here as a reference, trying to compile a list of bug reports.  There are multiple reports of this in launchpad, so the bug I have referenced here and in the bounty ([https://bugs.launchpad.net/ubuntu/+bug/124406](https://bugs.launchpad.net/ubuntu/+bug/124406)) may end up being a duplicate of another primary bug.

---

### Post by remitaylor on 2007-11-06
[ d'oh - duplicate post ... read above post for latest ([bounty]("https://launchpad.net/bounties/bug-124406-keyboard-hangs-repeats")) ]

Note: I'm not entirely sure that ubuntu bounties on launchpad are alive and kicking.  If not, ... anyone know where they currently live?

---

### Post by ben_staniford on 2007-12-29
I have just been reading this thread because I also had this probtlem with keyboard keys sticking when the system was under heavy load.  It's a guess but I suspect what is basically happening is that some keyboard interrupts are going missing and are not being processed by the kernel. In certain circumstances this could lead to the interrupt for "key up" being lost and so the key repeating for ever.  I've actually had another missing interrupt problem in the past related to this and to fix that problem I used the boot options:

noapic nolapic nosmp

I just tried this now and it seemed to fix the keyboard problem on my laptop quite effectively.  I'd be interested to hear if it works for you.  I should note that "nosmp" is not a good idea if you have a hyperthreading/multi cpu machine because it will mean you are only  using the first cpu core, however it is a good idea on non multi cpu machines and it was key for me in fixing my previous missing interrupt problem.

---

