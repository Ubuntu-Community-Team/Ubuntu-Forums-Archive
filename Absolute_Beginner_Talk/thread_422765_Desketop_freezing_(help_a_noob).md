---
title: "Desketop freezing (help a noob)"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by morkiehan on 2007-04-25
Hi we are to freinds who is trying to find an alternativ OS to MS, So we have both installed ubuntu on our machines, i havent got mush problems, but my friends computer keep freezing, with no apartent reason or system, som times it take long before it does it other times it comes fast. 

We have tryed to install ubuntu 6.1 then updating to 7.04. then 7.04 (64 bit) one and then just 7.04. It has a swap of 2048 mb and 100 G harddisk space. 

The machine has dual ram and sata harddisk, can anyof them be the problem ?.
 
We tryed looking through the systemlog and found an error,  date+ creating missing directory "/var/run/cups/certs" we were told that thsi has to do with the printer, sow we disconnected it with no lock. 

Anyone have any idear, we dont ?

Sorry about misspells.

---

### Post by tgm4883 on 2007-04-25
Little hard to help without at least a few system specs.

So all I can do is point you here and hope that it pertains to your situation (and that it gets fixed soon)
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

---

### Post by kittyhawk63 on 2007-04-25
What video card does your friend have in his computer?

Try this:
			 				sudo dpkg-reconfigure xserver-xorg (This is typed in Terminal. If you do not know how to get to Temminal and use it, let us know.
kh

---

### Post by morkiehan on 2007-04-25
thanks, what spec would you like, and how do i get it ?

---

### Post by kittyhawk63 on 2007-04-25
> **morkiehan said:**
> thanks, what spec would you like, and how do i get it ?

Need to know the make and model. For instance, I have this card:

ATI Radeon 9200 SE

What card does your friend have?

kh

---

### Post by morkiehan on 2007-04-25
It is a Nvidia Fx5500

---

### Post by kittyhawk63 on 2007-04-25
> **morkiehan said:**
> It is a Nvidia Fx5500

Go back to my original reply and run the command in Terminal. You will have a pop up allowing you to set the card properly. Go through the instructions carefully. Don't guess. Use the autodetects when available or necessary. Leave blank when it is suggested to leave blank. These instructions will make sense when you start the program.

Make a backup of xorg.conf before you do this. If you get it to working make another backup xorg.conf.

Here is the command for making the backup. Copy and paste to avoid errors.

[B]sudo cp -i /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

[/B]If you can't get the card to working after running the program in my first post, and it will not start Linux, reboot into the **Restore Mode**. Type the following command when the lines stop writing and you are at the ~$.

[B]sudo cp -i /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

[/B]That will put you back to where you were before. Come here again and see if someone else has a solution. They may answer here now.

kh

---

### Post by morkiehan on 2007-04-25
> **kittyhawk63 said:**
> What video card does your friend have in his computer?

Try this:
			 				sudo dpkg-reconfigure xserver-xorg (This is typed in Terminal. If you do not know how to get to Temminal and use it, let us know.
kh

Okay that made my disktop disapper and my freind mouse does not work, is there any way to go back

---

### Post by kittyhawk63 on 2007-04-25
> **morkiehan said:**
> Okay that made my disktop disapper and my freind mouse does not work, is there any way to go back

Read my last post. I gave you a way to restore what you had. Did you follow my instructions?

If you did not and you are locked out, it may require reinstalling. That sometimes is the way to get things back as they should be, especially if your friend has been doing a lot of changes.

I have no other suggestions.
kh

---

### Post by morkiehan on 2007-04-25
lol your instructions was abou 30 minuts late, but thank

---

### Post by Invius on 2007-04-25
/etc/X11/xorg.conf /etc/X11/xorg.conf.bak...

In the future, when you cannot access the desktop, you can attempt to access the console via ctrl-alt-f1 (through f6, f7 returns to xorg) then logging in with the same account info you use for the desktop, then renaming the above file to xorg.conf

---

### Post by morkiehan on 2007-04-25
Okay thanks, Im still working on my xorg. could my freind problem be his mouse and keyboard. 
He can see his screen and everything but hi click on anything ? it came as a set

---

### Post by morkiehan on 2007-04-25
Lol, that was fun. Try and error. Got it working with a better result. We all learn from our mistakes (i most be a genius). 

Still thanks

---

