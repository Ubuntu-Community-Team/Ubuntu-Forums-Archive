---
title: "update video driver on older machine"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by sagesparrow on 2007-06-23
I have xubuntu installed on an older laptop to get some useful life out of it.  It's got an 800Mhz processor, 128mb Ram, 30 Gig hd.  I've been having some hangups with Firefox, but i'll be doubling the Ram which i hope will take care of that problem.  I think an update to my video driver might help sharpen the screen.  The display is set to default resolution which i believe is 1024x768.

Will updating the driver help with sharpening the display?  If so, how do you update the video driver and how do you find out what the card is?

Thanks for your help.  The more simple the instructions are the easier I will be able to follow them.  I'm not too experienced at all this with Xubuntu or any other distro.

---

### Post by Brightbelt on 2007-06-23
Hi,
I'm not as familiar with Xubuntu - I use Feisty. But you may be able to run this command:

```
lspci
```
That's a small letter "L" spci" and your card should be listed in there if the command works in Xubuntu.

Also check to see if there's a restricted driver that can be enabled. Again, in Ubuntu, you can go to the System Menu/Administration/Restricted Drivers Manager and enable any drivers there that aren't currently installed.

That can help your resolution but it can also cause problems if it doesn't install correctly. But first and foremost, run 
'lspci' and post your findings here so we know what kind of graphics card you have.

I hope this helps,...Frank B.

---

### Post by sagesparrow on 2007-06-23
thanks
ran lspci
VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)

---

### Post by sagesparrow on 2007-06-23
xubuntu terminal is identical to ubuntu i believe

---

