---
title: "Is my install corrupted?"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by PopePaulZBT on 2008-03-28
Hi there, I have Kubuntu 6.1 installed on my computer. It was working fine, until I moved. Then, when I went to boot it up, it doesn't load the GUI, it just puts me into the shell (I think...it's black screen/white text asking me to login). I was able to login fine, but it still won't load the GUI. I tried "sudo start x", and it says "unknown command X".

I did swap the hard drive into another tower, but it boots up just fine, until it gets to the point where the UI is supposed to load.

Do I need to just do a total re-install, or is there anything else I can do?

Thanks for any help!

---

### Post by renfrew on 2008-03-28
to start the x server the comamnd is 'startx' without the quotes.  Try that and see if you can get the xserver running...  although it sounds like you might just be a ta virtual terminal prompt.   From that login prompt, try pressin CTRl-ALT-F7 all at the same time.. it should hopefully put you in to the GUI from there...

---

### Post by DBrocks on 2008-03-28
Take a look at this
[http://ubuntuforums.org/archive/index.php/t-98435.html](http://ubuntuforums.org/archive/index.php/t-98435.html)

---

### Post by Het Irv on 2008-03-28
Does the new tower have a very different graphics card?  If so that is probably the cause of your problem.

You can reset the settings by:```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Warning: You will lose all you configuration this way

BTW:
The command for starting the XServer is:```
sudo startx
```
No Space.

---

### Post by PopePaulZBT on 2008-03-28
First, thanks for the prompt replies!

I tried everything you've suggested...to no success. When I tried the right command to start the X server, I got this (after a bunch of stuff that looked mostly like standard startup stuff)

Fatal server error:
no screens found
XIO: Fatal IO error 104 (connection reset by peer) on X server ":0.0"
        After 0 requests (0 known processed) with 0 events remaining

Am I totally screwed, or is there anything else I can do?

---

### Post by DBrocks on 2008-03-28
Try a fresh reinstall. Sure you totally wipe the previous version. Try installing Hardy Heron. Thats the best advice I can give you.

---

### Post by PopePaulZBT on 2008-03-28
*sigh*

I'd hoped it wouldn't come to that. Thanks for the help, everyone.

It's not that I don't want to re-install/upgrade to Heron, but I don't want to lose everything on the hard drive. O well, it's my mistake.

Thanks again for all your help.

---

### Post by DBrocks on 2008-03-28
> **PopePaulZBT said:**
> *sigh*

I'd hoped it wouldn't come to that. Thanks for the help, everyone.

It's not that I don't want to re-install/upgrade to Heron, but I don't want to lose everything on the hard drive. O well, it's my mistake.

Thanks again for all your help.

What do you have on the hard drive?

---

### Post by DBrocks on 2008-03-28
Okay, don't do anything yet. I am going to keep researching. Stay posted!

---

### Post by DBrocks on 2008-03-28
[http://ubuntuforums.org/showthread.php?t=728235](http://ubuntuforums.org/showthread.php?t=728235)
Try this

---

### Post by equal on 2008-03-28
If you do end up reinstalling, try creating a separate partition for your /home folder. That way when you wipe an OS, you keep all your personal stuff.

---

### Post by DBrocks on 2008-03-28
> **equal said:**
> If you do end up reinstalling, try creating a separate partition for your /home folder. That way when you wipe an OS, you keep all your personal stuff.

Ah, well said. I was gonna suggest backing up to a CD, but your idea is much better!

---

### Post by PopePaulZBT on 2008-03-28
> **DBrocks said:**
> [http://ubuntuforums.org/showthread.php?t=728235](http://ubuntuforums.org/showthread.php?t=728235)
Try this

I checked it out and, though that is pretty much the same error I'm getting, linuxtoindia's suggestion isn't helping. I was able to do the reconfigure suggested earlier, but the rest of his post doesn't do anything. It's not recognizing the commands he's suggesting.

And it's that there's anything earth-shattering on the hard drive, it's just the fact that I'd lose everything I've written/saved over the past year. I'll probably do like equal suggested and partition like that.

---

### Post by DBrocks on 2008-03-28
Yes, thats the best idea. Then once you installed Hardy, you could then mount that partition with your /home, and copy everything over. Any more questions, do not hesitate to ask!

---

### Post by PopePaulZBT on 2008-03-28
Okay, I'm trying to make my own disc to reload Kubuntu (I gave away the one I used to load it in the first place, and don't want to wait up to 10 weeks for the shipit disc). I found a topic in the forums here about using Reconstructor to make a Live disc, but...I can't figure out how to do it. I'm using a Windows XP computer, if that changes things...

What's the quickest and easiest way to create a live/install CD?

Thanks!

---

### Post by Het Irv on 2008-03-28
If you have a good internet connection
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

I don't know if 6.10 is still avalible though.  7.10 is the latest and 8.04 will be out in a month.
8.04 is avalible as a beta.  The KDE variant comes in two versions, one with KDE 4 the other has... well whatever was in 7.10

---

### Post by PopePaulZBT on 2008-03-28
I've got the .iso file, I'm looking for how to convert that into a liveCD...sorry if I wasn't sufficiently clear on that point.

---

### Post by Het Irv on 2008-03-28
In XP... uhh hmm, do you have NERO or a program like that?  That would do the trick

---

