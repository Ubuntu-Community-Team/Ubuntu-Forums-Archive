---
title: "first boot problem - unable to start X server"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by Qwik on 2006-02-18
Hi,

Just finished installing Ubuntu...but when I boot into it, the load screen with the logo displays fine, then it drops to command prompt login for a moment, chokes for a second, looks like its trying to pull up a gui, but then craps out again and gives me an error message that it "failed to start x server"...is there some configuration or installation I need to do before gnome will work for me?

anyone?

---

### Post by codejunkie on 2006-02-18
[QUOTE=Qwik]Hi,

Just finished installing Ubuntu...but when I boot into it, the load screen with the logo displays fine, then it drops to command prompt login for a moment, chokes for a second, looks like its trying to pull up a gui, but then craps out again and gives me an error message that it "failed to start x server"...is there some configuration or installation I need to do before gnome will work for me?

anyone?[/QUOTE]
what kind of video card do you have?

---

### Post by Qwik on 2006-02-18
intel 915gm/gms on my toshiba m65-s9063 laptop...man I could've sworn this thing had an nvidia >_<

Am I SOL?

---

### Post by nalmeth on 2006-02-18
hmm I have an intel 915g on my computer, not sure if its different than yours.

Can you confirm you have a net connection, and ubuntu was fully installed? Is your processor 64bit, and if so, are you using the general i386 kernel or the amd64 kernel?

I believe, but can't totally confirm that your driver should be the i810 driver, included in the kernel.

type:
sudo dpkg-reconfigure xserver-xorg

follow defaults to your liking, and when it picks the video driver try i810, and if in the end this doesn't work, go back in and pick the 'vesa' driver.

post results!

---

### Post by Qwik on 2006-02-18
Sweet, thanks so much for the help, sadly, my wireless router didn't like ubuntu, wouldnt let it connect during the install config so I said I'd config it later when I could hardwire.  Not a 64bit chip, using the i386 kernel.

I'll give that a shot right now, and post results.

Thanks!

---

### Post by Qwik on 2006-02-18
ah!
The vesa driver worked :]
Now off to config with me :]
...is there any further info I should post to help anyone else with a similar problem who might stumble across the thread?
Thanks!

---

### Post by nalmeth on 2006-02-18
what was the driver set to originally? note that you won't have 3d acceleration with the vesa driver

---

### Post by Qwik on 2006-02-18
was originally set to i386...and yes, I'm noticing the lack of 3d accel :-x

Think I'm gonna take another stab at getting i386 to work...

I must confess, I've spent all this time rummaging through screensavers :/

I'm a tool.

---

