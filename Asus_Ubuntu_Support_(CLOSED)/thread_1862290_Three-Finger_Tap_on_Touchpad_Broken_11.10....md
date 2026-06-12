---
title: "Three-Finger Tap on Touchpad Broken 11.10..."
date: 2011-10-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by jrredho on 2011-10-16
Hey All,

I've got an ASUS 1015PN that I recently upgraded to Ubuntu 11.10 from 11.04. On the latter version, I had three finger tap support for my touchpad, which I'd mapped to a middle mouse click. However, once I upgraded, this capability no longer works.

I've done a fair bit of web (and soul :) ) searching, all to no avail. Now you might ask yourself why I care so much. Well, until this capability was taken away, I've forgotten how much I use all of the taps for the various mouse clicks.

Finally, fwiw, I've looked in all of the usual suspect places: /var/log/syslog and /var/log/Xorg.0.log with everything seeming normal, and running the command synclient, which reports that a tapbutton3 should report a middle mouse click. I've also checked this with utilities like evtest and xev to see that, no matter what I do, I only get 'Button1' X events when I do a three finger tap.

I'm now at my wits end, and I simply cannot believe that I'm the only person worldwide that's experiencing this behavior.

Can anyone out there in Ubuntu-land offer any suggestions?

Many, many thanks in advance,
john

---

### Post by kiki298 on 2011-10-16
I don't have a solution for you, just adding my voice to say I've got this problem too. Hope someone figures out a solution to it soon!

---

### Post by MrJones on 2011-10-17
Yeah, sorry, no solution from me either, but it has happened to me too. I read somewhere there has been some heated debate about this thing, so I hope it's only a bug and no one has taken the functionality away. I use this a lot, and want it back :(

---

### Post by bu1ka on 2011-10-17
Hi. I have laptop asus k50ab and three-finger tap doesn't work for me too. In 11.04 all was OK.

---

### Post by indium on 2011-10-18
same here.

visually:
1-finger tap does what it should
2-finger tap as well
3-finger tap does nothing (see also xev below)
3-finger drag drags the window (though compiz is programmed for <alt>button2)
4-finger tap gives the 'dash' of Unity.

xev:
doing 'xev' in a terminal and moving the mouse in the small window that pops up, I see that one-finger works and is recognised and two-finger as well.  Three-finger is not recognized (no response what-so-ever).


I also noticed that combining the the 'real button' (beneath the touchpad surface) with two finger tap on the touchpad surface DOES do the paste!!!! 
Very uncomfortable, but at least something.

---

### Post by neora.rama on 2011-10-19
I think, 3 tap unable.. :)

but you can setting your mousepad at system setting.. :)

---

### Post by takahe69 on 2011-10-20
not the exact solution, but maybe even better :)  (who needs the right button there anyway ...)

2 finger-tap paste:
 ```
sudo synclient TapButton2=2
```

Source: [http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html?showComment=1259709343760#c3388829731545818024](http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html?showComment=1259709343760#c3388829731545818024)

---

### Post by StupidHaiku on 2011-10-20
I installed 11.10 on my EeePC 1000h today over my existing 10.04 install of quite awhile ago and ran into the same issue.  I managed to get it working again by following the instructions on [http://ubuntuforums.org/showthread.php?t=1615564](http://ubuntuforums.org/showthread.php?t=1615564).  Search for "jconti" on the page and start from there, about a third of the way through the page (the paragraph should mention some things about 3-finger tap).  I basically followed those directions but had to install fakeroot as well to get them working (sudo apt-get install fakeroot).

The instructions there are for a different computer than mine but the solution seems to be relatively universal.  No idea if this will break any future updates (or if future updates will break this), as this is a very unofficial patch from someone in the bug reporting forums, but it does get the tapping to work.

---

### Post by stevenswall on 2011-12-04
Here's what I've tried so far to get the functionality in 10.10 back in 11.10:

[http://www.google.com/url?sa=t&rct=j&q=middle%20clicking%20ubuntu%2011.10&source=web&cd=5&sqi=2&ved=0CDcQFjAE&url=http%3A%2F%2Fwww.google.com%2Furl%3Fsa%3Dt%26rct%3Dj%26q%3Dmiddle%2520clicking%2520ubuntu%252011.10%26source%3Dweb%26cd%3D5%26sqi%3D2%26ved%3D0CDcQFjAE%26url%3Dhttp%253A%252F%252Fgrepmonster.wordpress.com%252F2011%252F05%252F31%252Fubuntu-11-10-middle-mouse-button-emulation%252F%26ei%3DfjbbTvyxJYKJiAK54IGbDQ%26usg%3DAFQjCNEqCJ0RJ3DTdJTTwYR6CJLcfIAiFA%26cad%3Drja&ei=fjbbTvyxJYKJiAK54IGbDQ&usg=AFQjCNEqCJ0RJ3DTdJTTwYR6CJLcfIAiFA&cad=rja](http://www.google.com/url?sa=t&rct=j&q=middle%20clicking%20ubuntu%2011.10&source=web&cd=5&sqi=2&ved=0CDcQFjAE&url=http%3A%2F%2Fwww.google.com%2Furl%3Fsa%3Dt%26rct%3Dj%26q%3Dmiddle%2520clicking%2520ubuntu%252011.10%26source%3Dweb%26cd%3D5%26sqi%3D2%26ved%3D0CDcQFjAE%26url%3Dhttp%253A%252F%252Fgrepmonster.wordpress.com%252F2011%252F05%252F31%252Fubuntu-11-10-middle-mouse-button-emulation%252F%26ei%3DfjbbTvyxJYKJiAK54IGbDQ%26usg%3DAFQjCNEqCJ0RJ3DTdJTTwYR6CJLcfIAiFA%26cad%3Drja&ei=fjbbTvyxJYKJiAK54IGbDQ&usg=AFQjCNEqCJ0RJ3DTdJTTwYR6CJLcfIAiFA&cad=rja)

[http://tombuntu.com/index.php/2011/11/06/persistent-touchpad-configuration-in-ubuntu-11-10/](http://tombuntu.com/index.php/2011/11/06/persistent-touchpad-configuration-in-ubuntu-11-10/)

[http://tombuntu.com/index.php/2011/11/04/how-to-swap-two-and-three-finger-tap-gestures/](http://tombuntu.com/index.php/2011/11/04/how-to-swap-two-and-three-finger-tap-gestures/)

None of this has worked, and beyond those solutions, I put up a question with $50 on it on justanswers.com.

If anyone in the community is able to fix this for everyone on Ubuntu 11.10, I will gladly pay them the same (through paypal.)

I am sick of getting functionality taken away from me with updated of Ubuntu.

...I no longer have a brightness applet, Ok, I can manage.
...I don't have a system monitor in the gnome panel, ok, I guess I can deal with that.
...I have to use an ugly dock with no customisation, fine.
...My entire system is slow, and the OS takes up more system resources than any other version of Linux I know of. That really sucks, but I guess if it works...

...I can't middle click on my laptop touchpad. Not fine in any way. What's next, no right clicking? 

It seems like Ubuntu is making sacrifices for the good of the 'touch' experience on tablets that don't exist, and phones that don't run it. I'm sick of it and have been since 11.04. Ironic isn't it? I'm willing to pay to fix something free... maybe I should just look for a paid OS like Windows and start trying to fix that dunghill.

 Anyway, I hope we can find the answer soon guys, as I've asked on Ubuntustack, Google+, and Diaspora. Good luck guys!

---

### Post by r_mano on 2011-12-04
Just to add to the (sad) list of stevenwall...

...they have ditched emblems and background in nautilus "because nobody used them" (sigh) 

(admittedly, the last one is a gnome decision, no Ubuntu, but still..)

---

### Post by stevenswall on 2011-12-10
Another week and still no solutions found. I guess I'll have to see where 12.04 takes things... hopefully in the right direction.

---

### Post by indium on 2011-12-13
In reply to Stevenswall #9:

I have precisely this sentiment! Slowly Ubuntu is turning into a Windows system that forbids you to change anything.

I had to install Ubuntu, Ubuntu-2D, Ubuntu-no-effects, Gnome-3, Gnome-2 and finally even Fluxbox to get back to a working system.

After MORE THAN 6 WEEKS, the Ubuntu standard interface MAKES MY COMPUTER CRASH! No reply from ubuntu, no fix.

The solution at the moment is to run GNOME-2.

Maybe a revert to Debian or Slackware is the only possibility?

---

### Post by henriquemaia on 2012-01-07
I also have this problem. I'm running Lubuntu Oneiric with 3.0.0-15-generic kernel on a eeepc 1000HE (elantech touchpad). 

I have tried many suggestions but I can't seem to get the 3 finger tapping working.

xev output shows that 3 finger tapping is recognized as a normal button 1 command.

The output:
```
ButtonPress event, serial 41, synthetic NO, window 0x3200001,
    root 0xaa, subw 0x3200002, time 23010536, (21,28), root:(649,238),
    state 0x0, **button 1**, same_screen YES

```

Any ideas on where to look further for a solution?

---

### Post by ryszka3 on 2012-01-12
The problem is with the ubuntu patches against xserver-xorg-input-synaptics package.

The solution to the problem is simple - just replace the ubuntu-provided package with one without those patches.

Here's how:

Download the appropriate Debian package from this site: (choose your architecture, either i386 or amd64)

[http://packages.debian.org/squeeze-backports/x11/xserver-xorg-input-synaptics]("http://packages.debian.org/squeeze-backports/x11/xserver-xorg-input-synaptics")

Then remove the original package from your system and replace it with the one downloaded.
Reboot the system and 3-finger tapping should be working again.

---

### Post by kventin-le--mans on 2012-01-15
Please, help to install the downloaded  package. I've extracted the package and it contains:[files]("http://i.imgur.com/HUruT.png")
 I've typed in the terminal: *./configure && make* 

When I've typed:  *make install* 

And got the message: *make: *** No rule to make target `install'.  Stop.*
  Please, give me right steps to install this package.

---

### Post by ryszka3 on 2012-01-17
First of all remove the original package
```
sudo apt-get remove xserver-xorg-input-synaptics
```
Do not extract the contents of the .deb file. Just type the command:
```
sudo dpkg -i xserver-xorg-input-synaptics_1.4.1-1~bpo60+1_amd64.deb
```
then restart.

There's one more thing. The update manager will try to replace it back. If you have synaptic package manager, find the newly installed package and "lock version" (there's an option in the menu, once you select the appropriate package)

---

### Post by OliverN on 2012-01-21
> **ryszka3 said:**
> The problem is with the ubuntu patches against xserver-xorg-input-synaptics package.

The solution to the problem is simple - just replace the ubuntu-provided package with one without those patches.

Here's how:

Download the appropriate Debian package from this site: (choose your architecture, either i386 or amd64)

[http://packages.debian.org/squeeze-backports/x11/xserver-xorg-input-synaptics]("http://packages.debian.org/squeeze-backports/x11/xserver-xorg-input-synaptics")

Then remove the original package from your system and replace it with the one downloaded.
Reboot the system and 3-finger tapping should be working again.

that sounds good, but won't it break some other Ubuntu specific feature? Do you know what we're missing by not using the default package?

---

### Post by hus787 on 2012-01-29
okay! i do not have the complete solution to this - as i'm currently facing the very same problem - but i know one thing for sure that 3 finger tap is enabled. but there is some predefined setting in 11.10 that grabs the event. proof try doing it inside a window that is not maxmized.
as i'm relative newbie to ubuntu so i can't offer a solution this. but here's a clue if anyone figure it out

---

### Post by hus787 on 2012-01-29
Thanks for the solution. But could u please explain what was causing  this? cuz as i previously stated that 3 taps are being detected but are  extracted by some predefined function/settings
plus if u have experienced this, u might be knowing the name of that  feature which used to pop-up when i 3-finger tapped inside an  unmaximized window providing me with 4 resize option (one at each  corners) and a move option in the center?

---

### Post by hus787 on 2012-01-30
This the feature i'm talking about don't know its name though:icon_frown:

---

### Post by acqant on 2012-02-10
This worked for me, thank you!

Before I would never get a Touchpad tab in settings but it worked.  It was just 4finger middle click and 3finger right click.  Odd




> **ryszka3 said:**
> The problem is with the ubuntu patches against xserver-xorg-input-synaptics package.

The solution to the problem is simple - just replace the ubuntu-provided package with one without those patches.

Here's how:

Download the appropriate Debian package from this site: (choose your architecture, either i386 or amd64)

[http://packages.debian.org/squeeze-backports/x11/xserver-xorg-input-synaptics]("http://packages.debian.org/squeeze-backports/x11/xserver-xorg-input-synaptics")

Then remove the original package from your system and replace it with the one downloaded.
Reboot the system and 3-finger tapping should be working again.

---

### Post by hardnrg on 2012-02-22
> **ryszka3 said:**
> First of all remove the original package
```
sudo apt-get remove xserver-xorg-input-synaptics
```Do not extract the contents of the .deb file. Just type the command:
```
sudo dpkg -i xserver-xorg-input-synaptics_1.4.1-1~bpo60+1_amd64.deb
```then restart.

There's one more thing. The update manager will try to replace it back. If you have synaptic package manager, find the newly installed package and "lock version" (there's an option in the menu, once you select the appropriate package)

Excellent concise directions!  Thanks, solved :)

---

### Post by darkvad0r on 2012-05-17
Installing a deb from a different distribution seems overkill when you can apt-get install compizconfig-settings-manager and disable "unity MT grab handles" plugin (it worked for me, even if it made ccsm and unity crash just after deactivating it)
After that all you have to do to get 3-finger tap working as middle-click is synclient TapButton3=2
BTW, I'm on precise, not on oneiric.

---

### Post by wayfarer_boy on 2012-05-24
Have to say, darkvad0r, that was an *excellent* suggestion.  I'm on Xubuntu, and after a recent update my 3-finger tap (middle-click) no longer worked.  I've now added

```
synclient TapButton3=2
```

to *Application Autostart* in *Session and Startup* system settings, and middle-click is reinstated every time on startup.  A *lot* easier than previous suggestions (and future-proof, too).

---

### Post by brakarb on 2012-06-16
> **wayfarer_boy said:**
> Have to say, darkvad0r, that was an *excellent* suggestion.  I'm on Xubuntu, and after a recent update my 3-finger tap (middle-click) no longer worked.  I've now added

```
synclient TapButton3=2
```

to *Application Autostart* in *Session and Startup* system settings, and middle-click is reinstated every time on startup.  A *lot* easier than previous suggestions (and future-proof, too).

Thank you! Worked perfectly without any messy installs. 

Just a quick word: you can enter this at the command prompt [with prefacing sudo] to test if it will work on yoru machine before putting it on the Application Autostart list.

---

### Post by screaminj3sus on 2012-07-10
> **wayfarer_boy said:**
> Have to say, darkvad0r, that was an *excellent* suggestion.  I'm on Xubuntu, and after a recent update my 3-finger tap (middle-click) no longer worked.  I've now added

```
synclient TapButton3=2
```

to *Application Autostart* in *Session and Startup* system settings, and middle-click is reinstated every time on startup.  A *lot* easier than previous suggestions (and future-proof, too).

Here's a nicer way to make this setting persistant :)
[http://www.reddit.com/r/linux/comments/v1yx5/how_to_reenable_3fingers_tapping_in_precise/c50lnj1](http://www.reddit.com/r/linux/comments/v1yx5/how_to_reenable_3fingers_tapping_in_precise/c50lnj1)

Using this method avoids issues like gnome overwriting the synclient setting after suspend/resume.

---

### Post by jahja on 2012-12-06
I always want to have two finger click does the middle mouse button, and three finger does right click, so I modified the line to look like this


synclient TapButton2=2 TapButton3=3

then how you make it persistent is your choice, hope this helps!

---

