---
title: "Really  new to linux"
date: 2005-07-06
forum: Absolute Beginner Talk
---

### Post by oobi on 2005-07-06
okay all, Ive never before touched a linux machine. all i've done is microsoft for 9 years and i'm ready for something new. I've tried to set up a machine with ubuntu, and imediatly after booting the screen goes blank... What have i done wrong?

---

### Post by poofyhairguy on 2005-07-06
[QUOTE=oobi]okay all, Ive never before touched a linux machine. all i've done is microsoft for 9 years and i'm ready for something new. I've tried to set up a machine with ubuntu, and imediatly after booting the screen goes blank... What have i done wrong?[/QUOTE]

Welcome

Can you describe "blank"?

Is it all black, white, or just a command line or something else. I'll try to help.

---

### Post by oobi on 2005-07-06
okay the screen goes black, and the processor keeps working, when i touch the keyboard the HD works

---

### Post by aysiu on 2005-07-06
You don't get a boot prompt or anything? I would assume something's wrong with the Ubuntu disk itself, not Ubuntu or your computer.

---

### Post by oobi on 2005-07-06
it seems to boot, as it starts to go into the gui, the screen goes black

---

### Post by Rita_Peta on 2005-07-06
What kind of machine?  I'm having trouble too (dell inspiron).

---

### Post by oobi on 2005-07-06
its a compaq presario, if that helps at all

---

### Post by poofyhairguy on 2005-07-06
Did the installer ever say it messed up?

Try hitting:

crtl+ alt+backspace 

and tell me what you see.

---

### Post by AsburyPark on 2005-07-06
[QUOTE=oobi]its a compaq presario, if that helps at all[/QUOTE]

Notebook?

---

### Post by P235 on 2005-07-07
Hi, my problem is not too different from the one noted above.  I installed Ubuntu on my HP Pavilion and decided to try Kubuntu by installing it via apt-get.  I was afraid of a fatal error if I closed the notebook so I decided to leave it open for a while, but after leaving it for approx. 10 minutes it had a black screen.  I thought it was a screen saver, but after moving the mouse and pressing a few keys there was no reaction.  Any ideas would be appreciated. ](*,)

---

### Post by oobi on 2005-07-07
I ve followed the advice, and after pressing control, alt backspace... my monitor light comes on but the screen itself is still blank

 I'm totally a fish out of water here, and help is absolutely appreciated

---

### Post by Lord Illidan on 2005-07-07
Ok....

From the boot screen, run ubuntu failsafe...

It should take you to a command prompt..

From there, run : sudo vi /etc/X11/xorg.conf

from there search through the document until you come to something which looks like this:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9200 Pro (RV280)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Now, press the Insert button to be able to edit the document.
Of course, for you it might be different, since you might not have an ATI graphics card, but change the Driver to "vesa", so it will look like this:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9200 Pro (RV280)"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Then press Escape, and in your lower left end of the screen you should see a colon :. Type wq.

Then reboot and go to the normal ubuntu... It should work..

(I explained how to use vi because I remember not knowing how to use it)

---

