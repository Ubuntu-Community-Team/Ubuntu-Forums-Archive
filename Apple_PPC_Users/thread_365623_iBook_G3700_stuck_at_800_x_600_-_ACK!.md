---
title: "iBook G3/700 stuck at 800 x 600 - ACK!"
date: 2007-02-19
forum: Apple PPC Users
---

### Post by ebeyer on 2007-02-19
I'm a relative linux newbie, in that my debugging skills are weak.  Your insight and help are appreciated.

I got dapper running on an old iBook G3/700/Combo.  Everything seems to work except the screen resolution maxes out at 800 x 600.  In OS X I'm getting 1024 x 768.  I looked at the /etc/X11/xorg.conf and I see that 1024x768 is indeed listed as a supported resolution.

So where do I begin?  800 x 600 is not gonna cut it for basic computing.

Thanks again.

EB

---

### Post by teaker1s on 2007-02-19
terminal[COLOR="Red"]
sudo dpkg-reconfigure xserver-xorg[/COLOR] and manually work through choices and select desired resolutions

---

### Post by ebeyer on 2007-02-20
So I tried entering a bunch of changes and rebooted -- only to be locked down to 640 x 480 -- double ACK!  Fortunately, my original xorg.conf was backed up and I was able to get back.

I'm speculating that the refresh rate specified for my LCD was wrong - would that make this happen?

Has anyone else had this particular issue configuring xorg.conf for a G3 iBook?  If yes, maybe you could give me some pointers?  Better still, maybe somebody with a G3 iBook could paste their xorg.conf here and I could try it for myself.  

Thanks again.

EB

---

### Post by maggot_brain on 2007-02-20
I've had exactly the same problem but I got it working.  If you send me a personal message with your e-mail address I'll send you my xorg.conf file.  I have exactly the same model as you.

Ananda

---

### Post by jazzman on 2007-02-22
Edit your /etc/X11/xorg.conf.

go to the DefaultDepth line and change it to 16.

This works great on all my G3s.

Jazz

---

### Post by saracen on 2007-05-24
tried that and it didn't work for me.  I'm still stuck at 800x600 :(

---

### Post by Gen2ly on 2007-05-24
Backup your xorg.conf and try "X --configure".  I don't have my Ubuntu Box with me so I haven't tried this with Ubuntu, at may be that the program isn't there but is worth a try.

---

