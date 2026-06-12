---
title: "Can I recover data from a WinXP hard drive"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2007-12-06
My wife's XP computer has a hard drive going bad, evidently. (According to some program during boot up.) I have another HD ready to go, but don't know the best way to save it. I'll likely be using my computer (Ubuntu 6.07) to do it. Any ideas or suggestions?

---

### Post by blu3ness on 2007-12-06
mount the hard drive and copy the files over? :X

---

### Post by aysiu on 2007-12-06
Boot the live CD on your wife's XP computer

Go to Places > Home

In the left sidebar, double-click your wife's hard drive

Authenticate with a password

Copy the important files over

---

### Post by Jerry N on 2007-12-06
You should be able to boot the Ubuntu 7.10 (Gutsy) live CD and access the files on your hard drive.  You could then copy them to an USB external drive or other USB storage device.  I did this successfully for a friend a few weeks ago.  There are other Linux distributions that could do this as well but they would need to have NTFS read access, assuming you HD is formatted for NTFS of course.  I don't know if your older version of Ubuntu can read NTFS or not.

Jerry

---

### Post by lespaul_rentals on 2007-12-06
Yup, just what aysui said.  If you mean the hard drive is literally dying (as in click*click*click) you might need to try to freezer trick.

---

### Post by ReverendJ1 on 2007-12-06
If the failing hard drive is the one with Windows on it you will want to do something called 'ghosting' so that windows can boot from that drive. Otherwise you will have a drive with a bunch of files on it that can't do anything. Try using G4L,[here]("http://bhavesh.freeshell.org/cloninghd.html") are some instructions.

---

### Post by ReverendJ1 on 2007-12-06
I forgot to mention this, but G4L will copy windows and all programs, etc. so that you will not have to set anything up on the new drive. What other people are describing would be good choices if there are just some files on the drive you need, i.e. the dying hard drive is a second hard drive on your computer that stores all your music and pictures and nothing else.

---

### Post by aysiu on 2007-12-06
> **ReverendJ1 said:**
> I forgot to mention this, but G4L will copy windows and all programs, etc. so that you will not have to set anything up on the new drive. What other people are describing would be good choices if there are just some files on the drive you need, i.e. the dying hard drive is a second hard drive on your computer that stores all your music and pictures and nothing else.
Well if Windows is having trouble booting up, would you really want to copy over the programs and Windows, too?

---

### Post by ReverendJ1 on 2007-12-06
@aysiu - From the first post, I would assume that it is some sort of [S.M.A.R.T.]("http://en.wikipedia.org/wiki/Self-Monitoring,_Analysis,_and_Reporting_Technology")  error/notification that is popping up as it said that the hard drive is going bad. I would not think this is actually a Windows problem given what was said in the first post.

---

### Post by Papa-san on 2007-12-06
Thank you all! Wow... One more reason I love this community!

It is a secondary drive, but has some program data on it. 
It isn't the drive with grub on it, so it boots OK. It also isn't freezer ready :-) I think I'm catching it early enough.

It was formatted in NTFS, so I have that limitation. Again, thank you all!

Oh, and it is a S.M.A.R.T notification...

---

### Post by lespaul_rentals on 2007-12-06
Yup, a Gutsy LiveCD will be able to mount your NTFS hard drive.  Just boot up the LiveCD, point your file browser to the drive, and you should be good to go.  Good luck.  Let us know if you need any more help.

---

### Post by bobpur on 2007-12-06
I have Ubuntu 7.10 dualbooting with XP and I, sometimes, slip over into XP from Ubuntu after a wallpaper or a pdf file. I don't see why you shouldn't be able slave that drive to Ubuntu abd get your stuff.

Good Luck!

---

