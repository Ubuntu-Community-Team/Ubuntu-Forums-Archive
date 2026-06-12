---
title: "Install Ubuntu to 2nd HDD, leave WindowsXP on C:/"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by WebJoel on 2006-12-21
I have read some posts and FAQs, :-k  -I *almost* have my answer... but want confirmation and I do require explicit-verbose confirmation, -before I make the plunge and add Ubuntu to make a duel-boot system..

My stats:
  I have WINDOWS_XP on my (80-GB) C:/ drive. I have a second, smaller internal HDD (20-GB) called "D:/". I want to have Ubuntu installed on D:/, but on-startup, have the C:/ drive show a choice between "WindowsXP" or "Ubuntu", and otherwise default to startup C:/ ("WindowsXP") because my wife uses/needs this for when she works at home.

 I am not a totally new Linux user, -I have "Puppy Linux" installed on my 2nd HDD, and when I first boot, a dialoge box comes up giving me 15-seconds to choose between normal-WindowsXP launch on C:/, or Puppy Linux on D:/. THAT is what I want to do with Ubuntu, -have it on the 2nd hard-drive, -AWAY from WINDOWS. 

 I have the Ubuntu 6.06.1 .ISO, -I am just afraid, -or hesitant, -to go ahead and INSTALL, fearing that I will over-write something on C:/ that I will need to keep. Does the *ISO give you the ability to install on a drive other than "C:/" and present a start-up menu to choose from?? I intend to have ONLY Linux stuff on the 2nd HDD, so I can 'wipe D:/' clean if it calls for it, but I must preserve the integrity and functionality of my C:/-drive.

 Bomdard me with step-by-step how-to, -make me assured that I can do this.  In the few months of playing around with Linux distros I have become a huge fan and be it not for my wife absolutely requiring Windows-XP remain intact, I'd have nothing further to do with M$...

 Gratitudes,
 -Joel

---

### Post by aysiu on 2006-12-21
Yes, you have the choice of where to install Ubuntu. 

Of course, during the installation process, your two drives won't show up as C:\ and D:\ They will probably show up as /dev/hda1 and /dev/hdb1. You will easily be able to tell that the 80 GB one is the one **not** to reformat and then 20 GB one is the one to reformat.

This will give you a blow by blow (with screenshots) of the installation process:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

After you've installed Ubuntu, you'll get a choice to boot up Windows or Ubuntu, but Ubuntu will be the default. We can help you make Windows the default after you get everything installed okay.

---

### Post by gn2 on 2006-12-21
This may help: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by WebJoel on 2006-12-21
Okaaay... I have tried three times to install from the CD, -the farthest I got was selecting my City (successful) and Time Zone (**un**successful). The latter is where everything seemed to just hang... I sat for about 20-minutes, listening to the CD-drive grind away and not respond to changing the clock to my local time, -had almost no control over the pointer tool (would not respond, and when it did, the pointer would disappear for a few minutes and re-appear on other side of screen).
  I ended up having to bail using the I/O button and yanking the *ISO out of the tray before re-boot (I hate doing that... it's so, ... *Windows*! [-(  ).

 Thanks both aysiu and gn2 for replying so soon. -Both of you gave links which would be helpful, -if I could visit them. They currently are not available (tried several times an hour ago, and again just now... both series of attempts the server seems to not be able to show me anything. -Might be busy, link might be spelled incorrectly (says the browser help screen), etc.)

 Grr...

 I will try this again tomorrow. I am not getting off to too impressive a start I think.  ](*,)   
 I suppose anything worth having shouldn't come too easily. >sigh...<
-Joel

---

### Post by jimrz on 2006-12-21
> **WebJoel said:**
> Okaaay... I have tried three times to install from the CD, -the farthest I got was selecting my City (successful) and Time Zone (**un**successful). The latter is where everything seemed to just hang... I sat for about 20-minutes, listening to the CD-drive grind away and not respond to changing the clock to my local time, -had almost no control over the pointer tool (would not respond, and when it did, the pointer would disappear for a few minutes and re-appear on other side of screen).
  I ended up having to bail using the I/O button and yanking the *ISO out of the tray before re-boot (I hate doing that... it's so, ... *Windows*! [-(  ).

 Thanks both aysiu and gn2 for replying so soon. -Both of you gave links which would be helpful, -if I could visit them. They currently are not available (tried several times an hour ago, and again just now... both series of attempts the server seems to not be able to show me anything. -Might be busy, link might be spelled incorrectly (says the browser help screen), etc.)

 Grr...

 I will try this again tomorrow. I am not getting off to too impressive a start I think.  ](*,)   
 I suppose anything worth having shouldn't come too easily. >sigh...<
-Joel

are you using the "live" cd GUI installer or the alternate cd?

Also, please post specs on your hardware...cpu /ram / video card, etc. This will help give an idea what steps need be taken to get you going.

Welcome...and hang in there, plenty of able assistance available here

---

### Post by WebJoel on 2006-12-22
-It seems that it was my Firewall preventing me reliably accessing the provided links. This morning, -same thing until 'suspended' the Firewall, -and got right to the posts.
 -Seems as if maybe temporarily disconnecting the Master HDD is the safer way to do a Ubuntu install on the Slave drive. The link provided didn't make me feel any more at ease installing, -if anything, it reinforced fears of wiping-out Windows. :-?  I'd like to install Ubuntu entirely on the Slave drive and not have to remove/disconnect the Master (too 'risky' for a self-proclaimed fat-fingered non-techy whose only real 'skill' is cleaning computer cases and possibly installing DIMM modules and that is about it). Heck, -I wouldn't really mind if Ubuntu came up as the 'default' OS, so long as WINDOWS-XP remains intact and un-disturbed. 

 Reply:
 I have a Celeron CPU, 2.40GHz, 224-MB RAM, with S3 Graphics ProSavageDDR (this is what you wanted to know?). Have "live" CD-installer, downloaded & burnt-to-disk myself.
 Current 'Master' HDD is 80-GB, 'Slave' is 20-GB. -Would it be recommended do you think, to format 'Slave' *first*, or will install *ISO not mind/or give me option to do so? Nothing on Slave drive is needed to be kept (just dups of some stuff from Master), and distro of "Puppy Linux" which if I had Ubuntu, would not need but if left alone, might still use. In case you are wondering, I had found a "Puppy Linux installer" that installs WITHOUT touching anything Windows, and presents you with a start-up option of WINDOWS or PUPPY LINUX, and times-out to default Windows-start-up. -THAT (smile!) is what I want to do with Ubuntu. :mrgreen:  Heck, -would be nice if I could get Ubuntu listed right alone with Puppy and WIN-XP for my start-up options...
-Joel

---

### Post by Bartender on 2006-12-22
> **WebJoel said:**
> 
 I have 2.40GHz, 224-MB RAM, with S3 Graphics ProSavageDDR (this is what you wanted to know?). Have "live" CD-installer, downloaded & burnt-to-disk myself.

Anything less than 256 MB RAM quickly gets you into trouble with a LiveCD.  Better off to start over with an alternate install CD.  Also, that video may give you grief....

---

### Post by WebJoel on 2006-12-22
Plan to double (or more) my RAM shortly anyway. -Either add 512-MB more, or add a Gig module. So, I'll just wait a bit then on installing Ubuntu, and just stick to learning Linux with 'Live CD" and use Puppy Linux for now (-I cringe every time I say "Puppy Linux"...).

---

### Post by punx45 on 2006-12-22
I have precisely the setup you described.   I have windows on master C: (hda) and ubuntu on slave E: (hdb).   The installation was painless.  if you already have puppy linux on the slave then identifying it when it comes time to partition during the install process wont be as scary as you think.   Windows will be identified as NTFS and puppy likely will be EXT3.

and grub is able to identify both systems without having to do anything to the windows disc at all.

---

### Post by nmincone on 2006-12-22
[How-to_dual-boot_ubuntu]("http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu")
This is an excellent post on this subject- works like a charm!!!!

---

### Post by WebJoel on 2006-12-22
Thank you punx45 and nmincone. -Confidence level rising. :)   And correction: I seem to have 256-MB of RAM, not 224-MB as I reported earlier. I can't quite get my head around that, but one 'System Report' tells me "224-MB" and another says that my computer has "256-MB onboard". Now, I should know this, eh? It was about a year ago my computer did a flaming wipe-out and I needed a new motherboard, and having mad cash that particular weekend, told my local Geek guy to slap in a new motherboard and didn't really care much about the specs. I just said "fast, powerful, and oh yeah, -I am not into 'gaming'" and he seemed to know what I would like for the price we discussed.
 I do have two DIMM slots and do plan to kick this mule up to a Gig at least, very soon. I will re-read the posts and visit the links you provided. I want to just  (shamelessly stealing the euphamism) "plug-and-play" this new OS and be done with it. That is what I like about Puppy Linux installer... just click & it was done. -there was no shame that the ease of doing this was comparable to installed something in Windows. 8)

---

### Post by WebJoel on 2006-12-22
MOD: -dbl post : okay to remove THIS.

---

### Post by maniac_X on 2006-12-22
Webjoel, here is something that might be a solution for you with regard to setting it up to give 
Windows as the default boot up after a time. [[COLOR="Red"]**GAG**[/COLOR]]("http://gag.sourceforge.net/") Hope it helps and i'll be in the trenches right next 
to you as I am also fairly new to Ubuntu. I found that link as I was perusing the forums the other day. :mrgreen:

---

### Post by nmincone on 2007-01-03
GAG is a bit over kill, just edit the #/boot/grub/menu.lst, there are some flexible settings that can be made right there without any additional add-ons.
This includes default booting, boot time countdown, customize the boot list....

---

### Post by igknighted on 2007-01-03
I thnik the RAM issue is because your graphics shares that 256 MBof memory, so only 244 are available to the system.  The alternate CD is better to install from anyways (I would never recommend the Dapper live install for dual boot, it doesn't let you choose anything about where grub gets installed).

---

