---
title: "How do I enable my DVD drive's eject button?"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Taxi on 2007-12-11
When I press the eject button on my DVD when it has a disc in it, it doesn't eject.  I understand this has to do with the drive being mounted, etc.  I'm wondering if there is a way to make it so that the software verifies that an optical drive is not actively in use (reading/writing or with data still waiting to be written) and then unmounts and ejects.  I am not trying to make it into an emergency override button that ejects no matter what it's doing (I see the value in asking for the OS's permission first).

I realize that it is pretty straightforward to eject from the command line or to make a launcher in the panel to do it or whatever, but I'd really just like to be able to use the built-in hardware button.  I tried to research this and came up with the following solution, but I don't know how it would work (if it would be the emergency override eject or just the friendlier kind), what it's actually changing and why, or (most importantly) how to undo it in case it doesn't do what I want it to.

> Open Terminal and type/ cut&paste

Code:
sudo sysctl dev.cdrom.lock=0

now your cd can be ejected by simply clicking on the eject button but if you restart it will no longer be available, to make it permanent,
then type

Code:
sudo sh -c 'echo "dev.cdrom.lock=0" >> /etc/sysctl.conf'

Now it will be permanent.

---

### Post by meborc on 2007-12-11
what version of ubuntu are you using? this feature has been enabled since dapper (i think)

---

### Post by Taxi on 2007-12-11
Fully updated Gutsy (upgraded from the original Feisty installation).  It shouldn't be the button, either, because it works in BIOS and in Windows and works for closing in Ubuntu, as well as opening with no disc (which I just checked).

---

### Post by rockinlinux on 2007-12-11
im not sure but i dont think you need to do anything. I have never heard of anyone having problems wih this botton unles it is broke. I have a notebook and the botton works fine. I also have a second sats DVD-RW that i use with a SATA to USB cable and that botton works fine (even when i only have the power plugged in and not the USB). Are you sure your botton is not broke? it seems like this is a hardware botton so you wont be able to change it with the os. i could be wrong. :)

---

### Post by rockinlinux on 2007-12-11
> **Taxi said:**
> Fully updated Gutsy (upgraded from the original Feisty installation).  It shouldn't be the button, either, because it works in BIOS and in Windows and works for closing in Ubuntu, as well as opening with no disc (which I just checked).

it sounds like you have a broken piece of hardware to me. but if it works in windows then ?????????

---

### Post by Taxi on 2007-12-11
The button not only works in BIOS and Windows, but also in Ubuntu when there is not a disc in the drive.  I believe you when you say that it should work, but the fact is that it is not working and it looks (at least to me) like it's a software issue.  Does anyone know of any settings or config options anywhere that could somehow have been set incorrectly?  Or does anyone have additional suggestions to help narrow down the problem?

---

### Post by meho_r on 2007-12-11
I have similar problem. My DVDRW drive opens correctly when I press eject button, but DVD drive doesn't. I'm pretty sure it is software problem, because I had the same problem in openSUSE, but I found (somewhere) a configuration option "Ignore drive lock" or something like that that made it work. Not sure how to do this in Ubuntu though :(

---

### Post by Taxi on 2007-12-11
> **meho_r said:**
> I have similar problem. My DVDRW drive opens correctly when I press eject button, but DVD drive doesn't. I'm pretty sure it is software problem, because I had the same problem in openSUSE, but I found (somewhere) a configuration option "Ignore drive lock" or something like that that made it work. Not sure how to do this in Ubuntu though :(
Thanks for the confirmation.  Does anyone know where this setting would be found in Ubuntu?  Also, would it still make sure the drive is not actively being used or is there another way that would be better?

---

### Post by Taxi on 2007-12-12
Does anybody have an idea what's wrong?

---

### Post by Taxi on 2007-12-13
Bump.

---

### Post by rockinlinux on 2007-12-13
well it does sound like a software issue i guess...i would start by looking in you hardware profiles and seeing if there is an option for what meho_r was talking about. And im not sure  is this is the answer to waht you asked but if you do this i think the drive will open no matter what, even if it should be busy.

---

### Post by TheLions on 2007-12-13
got similar problem here, to eject i need press on right click on dvd-drive and pick eject to eject the drive, but pressing on button does nothing

---

### Post by philinux on 2007-12-13
My DVD player and CDRW drives behave exactly the same. 

Once there is a DVD or CD disk in there the eject button does not work.

I have to right click on the desktop icon and select eject or unmount.

---

### Post by kajillin on 2007-12-13
i guess until a dev looks at this problem u guys are screwed, until then why not just use the emergency hole (as i call it), u know... take a pin stick it in unleash the load..... ;)

---

### Post by rockinlinux on 2007-12-13
has anyone filed a bug report?

---

### Post by philinux on 2007-12-13
I just thought it was a feature! :)

---

### Post by Taxi on 2007-12-14
Any developers or otherwise knowledgeable people out there with advice/suggestions?

---

### Post by Taxi on 2007-12-19
I would still love some input from developers / super knowledgeable types.

In the meantime, though, I have verified that the eject button on my other drive, a CD burner, does work, even with a disc in and mounted.  Maybe those of us experiencing this problem can compare hardware?

My DVD drive with the eject button problem is a
TOSHIBA DVD-ROM SD-M1212

---

### Post by Taxi on 2007-12-19
Bump.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-12-19
This is a feature something good i will look into however not devloper so will take some bashing to get it
no i gess i was wrong

---

### Post by Taxi on 2007-12-19
Thanks for trying.  However, if it's a "feature" I don't see why CD burners and other optical drives would behave differently.  One or the other's gotta be a bug, I guess.  And, for the record, I personally think it's more of a feature to have the button working, though I do prefer verification that the drive is not *actively* in use.

---

### Post by legend2440 on 2007-12-20
script

---

### Post by Taxi on 2007-12-23
Bump.

---

### Post by Taxi on 2007-12-25
Merry Christmas bump!

---

