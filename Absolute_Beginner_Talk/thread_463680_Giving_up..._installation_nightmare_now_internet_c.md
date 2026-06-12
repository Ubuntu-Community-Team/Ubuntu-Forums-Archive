---
title: "Giving up... installation nightmare now internet connection nightmare"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by sreed39 on 2007-06-03
I posted earlier regarding my problems... I really do want to use this OS, but it just does not seem to work right for me. I have downloaded SEVEN different files trying to get one to install. The seventh installed... but it took two days to get enough installed to even see the desktop.

Then, after finally getting to the desktop, I could not access the internet through Ubuntu. I have been working on this for 12 hours, and STILL cannot get access through Ubuntu. I get access when i reboot back into windows. Obviously I have checked to make sure everything is connected, and, since I have access through Windows OBVIOUSLY I have everything connected. I am using a DSL modem. Rather than letting it auto detect, I even went in and configured the IP addresses to what Windows used through this modem. That was a challenge in itself as sometimes I can get to Network Settings in Ubuntu and sometimes I cannot...

Then, when I STILL was not connecting, I logged off to check some other settings, when I logged back on, I got to the login screen just fine, entered username and password.... system froze.... tried it several tiems, including recovery mode, still cannot get back to the desktop.

I would try re-installing, but I do not have another week to get it running again. So, I give up. As much as I HATE Microsoft... I don't really have a choice. I cannot make linux run properly...

---

### Post by kevdog on 2007-06-03
Congrats on getting everything installed -- I know it can be seriously frustrating.

Take a breather for a moment with the ethernet connection.

First are you trying for a wired or wireless connection?

Please also post your /etc/network/interfaces file.  (The directory is /etc/network.  The file is interfaces).

Are you trying to go through knetworkmanager, or gnome applet, or how are you configuring your interface??

What about your router if you have one -- you said DSL.

Are you using dhcp or trying to establish a static IP.
If wireless are you using some type of encryption?

Please provide more details if possible.

---

### Post by kelvin spratt on 2007-06-03
sorry to hear your problems, it would help people to know some more details on what you are running makes and models type of graphics card how much ram etc as then people can try to help you, i bet u are frustrated and spent i lot of time trying to get up and running. Hopefully you can get some answers but please give as much info as possible.

---

### Post by pappapump on 2007-06-03
Sometimes a new thing like Ubuntu can be frustrating starting out, just take a look at some of my first posts.
But rather than giving up, which to me is unthinkable after having been in Ubuntu for almost 2 months now, I keep plodding ahead with tenacity and success.

Yous system specs would sure help out a lot in determining how to solve your problems as well as what os is pre-installed on your PC, if any.
After all my ranting and finally resolution to my problems thanx in large part to this forum, I'm more than ready to help where I can.
Going back to Winblows isn't an option.
I have been assimilated.

Now I'm Windows Free.

---

### Post by sreed39 on 2007-06-04
And it just gets worse...

I am not the "give up" kind of guy... so I gave it another shot last night, completely reinstalled from scratch (using a different install method from the menu). As part of this, since my XP is about to expire (long story, but this was my third re-install of XP and Microsoft would not allow me to re-activate with the same product key), I decided to go ahead and dump it completely anyway. Well, went through the install and at install it could not set up with DHCP. Using a DSL modem provided by a local phone company...not anyone you guys would know. So, FORTUNATELY, I had written down all of my IP addresses, Ubuntu asked for these at install and I was able to enter the information... at about midnight last night, it was fully installed AND the internet was working.

I was ecastatic. I went to bed finally feeling as if I could be completely away from Windows FOREVER. I turned off my monitor (computer in ebdroom, wife can't handle monitor being on all noght) and went to bed. Got up, ready to show my wife (she was NOT happy with her inability to check her email over the weekend as I was working on this problem) the great thing I had done..... oops, no internet access. Does not load any page; email won't work. Try to check a few things then BAM. Computer goes to command line and won't go back into desktop. I re-booted... get to login screen and enter username and password... back to black screen. Now I cannot get back in at all.

As for specs... let's see I am using an SMZ 10/100 ethernet card it is a wired connection to the aforementioned DSL modem. My computer is a compag with a new updated motherboard (when the computer crashed a month ago, I blew the motherboard too) and a pentium 4 processor. I installed 7.04 with the alternate cd 9regular desktop cd's would not burn without some error.... the checksums were always good, teh file trees looked right on the CD, but there was an error installing every time). As I said, I had to switch from automatic config to static IP... the static IP was working at 12:30 this morning, but now it's not... and since teh system won't let me back in (again) I can't even tell you what my interface is...

---

### Post by kevdog on 2007-06-04
Im really not sure if I can help you on this one!  When you say "black screen" you mean totally black and not the command line login correct??

As a side note you know software is available to change your MS Windows Activation code!??

---

### Post by BHelts on 2007-06-04
when your system crashed a month ago, you said you replaced the mobo... what else did you replace?  did you test your RAM and your Hard Drive(s)?  Sounds like a hardware issue to me.

---

### Post by sreed39 on 2007-06-04
Yes, RAM and hard drive are fine. And, yes, black screen. Not even to command line. Very frustrating to say the lease. And, no I did not know that there was software to circumvent the Product Key.

---

### Post by Wim Sturkenboom on 2007-06-04
Why are you sure that HD and RAM are OK? Did you run memtest and the utilities of the HD manufacturer?
I suggest that you install windows to check if everything still works.

And with regards to the internet connection:
if your provider gives you a dynamic address, there's a good chance that a static address will not work; you were just lucky that one time. My address changes every time I connect. Have you tried *pppoeconf* to configure your internet connection; after that you should be able to start the connection with *pon dsl-provider* and close it with *poff*. After the pon command, check till you get DNS server addresses using the *plog* command.

---

### Post by Chayak on 2007-06-04
Well one you can call the number and get an activation agent on the phone for XP, you'll have to tell them that yes it's only one one computer and they'll give you the activation code.  Ok, windows aside...

Just to try something... download a DSL disk [here]("http://www.damnsmalllinux.org/") and boot up the live CD (for time's sake as it's small).  Then boot off of it and check to see if you have internet connection.  Most ISPs won't give you a static address without paying some extra cash so you should be using DHCP to get your IP.

---

### Post by Josey on 2007-06-04
> **BHelts said:**
> when your system crashed a month ago, you said you replaced the mobo... what else did you replace?  did you test your RAM and your Hard Drive(s)?  Sounds like a hardware issue to me.

seconded.
If it was working and mysteriously stops working it sounds like you may have a bad piece of hardware.
If you stick with it we should be able to figure out which piece it might be.

---

