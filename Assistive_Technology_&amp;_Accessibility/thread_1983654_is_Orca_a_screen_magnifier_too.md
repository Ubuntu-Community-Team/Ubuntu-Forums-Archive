---
title: "is Orca a screen magnifier too?"
date: 2012-05-20
forum: Assistive Technology &amp; Accessibility
---

### Post by bubazoo on 2012-05-20
My name is Tom. I am a new user of Ubuntu 12.04
with very low eyesight. 

During the install, I couldn't get Orca to load at all either in screen magnifier or screen reader modes,  I have tried multiple machines with the same problem with no solution to think of.

With a SB audigy card, I was able to get Orca to speak after install, but not during the install process, and I haven't been able to find a screen magnifier at all.

Am using the 32-bit version of ubuntu 12.04 desktop
since I was told the 64-bit version of ubuntu is broken.

My machine at home uses a Rocketfish 5.1 PCI Sound Card I purchased at Best Buy about 4 or 5 years ago since Sound Blaster Cards are getting tougher and tougher to find these days.  I have looked, but have not been able to locate a sound blaster card anywhere for my PC at home, not something that costs less then $50-100 anyway...  you mean to tell me ubuntu ONLY supports Sound blaster sound cards?  common now!  lol 

I read in the ubuntu forums that Rocketfish is still a fairly new card.  I'm like wait a minute, I've had this RocketFish card for about 5 years now!  5 years isn't old to me! lol

and if I'm supposed to buy a Sound Zlaster audio card, or some other supported audio card, where would I get one of those at?  nobody sells Sound Blaster cards anymore unless your LUCKY enough to find one on ebay. what other audio card IS supported may I ask?

I wasn't able to locate a screen magnifier at all even after the install. I boot up Ubuntu and run orca but I see no options for screen magnification or high contrast options at all!  just voice options in the config thats all.

---

### Post by bubazoo on 2012-05-20
I mean, am I supposed to

apt-get install

something I'm missing? or what?  and if so, what?  lol

---

### Post by sdjernes on 2012-05-21
Orca is designed to use gnome-mag. To me it behaves very crappy. 

I myself use the enhanced zoom features in Compiz. I do not know what is needed to get it to work in 12.04 as I have not installed it yet.

---

### Post by bubazoo on 2012-05-28
anyone else know? 

I finally got sound in orca to work, just started working I don't know, but there are STILL no options for magnification in the orca preferences for screen magnification or color enhancements.

obviously ubuntu must come with it because it askes you for that during install. does anyone know how to enable all that after install? because I cannot find it anywhere

---

### Post by RockkFather on 2012-06-15
[SIZE=4][FONT=Comic Sans MS]im new to unbuntu and recently installed 12.04.im having hard time finding a magnifier too since im using a LED  32" tv screen as my monitor so i cant really read the small characters without a magnifier there an app called kMag but it drove me insane and then i have red in few places that there is another app called "virtual magnifier" but i couldnt get it installed propperly. guys i need help!![/FONT][/SIZE] 

[SIZE=4][FONT=Comic Sans MS]thank you in advance!!![/FONT][/SIZE]

---

### Post by ethanay on 2012-11-15
I'm not sure where the Orca screen magnifier went.  But it never behaved well.  Was very slow and unwieldy.  I find this magnifier is a much better alternative:
[http://magnifier.sourceforge.net/]("http://magnifier.sourceforge.net/")

It is easy to install, just follow the directions.  To make it easy to use, I use a custom launcher shortcut of ctrl - alt - m.

You can also put a custom launcher in the Unity launcher bar if you want:

create a file called magnifier.desktop and open it with gedit and paste in the following:

```
[Desktop Entry]
Type=Application
GenericName[en_US.UTF-8]=Launch a screen magnifier
Exec=vmg
Comment[en_US.UTF-8]=Terminal-based text-only web browser
Icon=/usr/share/icons/HighContrastInverse/48x48/stock/system-search.png
Categories=Accessories
Name[en_US]=Magnifier
```

Then save it on the desktop, and drag the file onto the launcher bar, or into /usr/share/applications (for all users) or ~/.local/share/applications (for a single user) via
```
sudo cp Desktop/magnifier.desktop /usr/share/applications/
``` or
```
sudo cp Desktop/magnifier.desktop .local/share/applications/
```

Too bad it's not in the repositories already!  Would be wonderful for Orca developers to integrate it in their project.

---

