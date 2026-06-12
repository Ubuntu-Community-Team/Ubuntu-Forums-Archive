---
title: "Absolute Ubuntu beginner- And a problem!"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by Rhumpole on 2007-11-14
:) - Good morning. I am an absolute beginner in both Linux and Ubuntu. I have dual booted both Windows XP SP2 and Ubuntu 7.10 on my pc which worked well, until last night! - On opening Ubuntu, I decided to download 3D effects. This appeared to load correctly. However, on going back to add/remove programs it wouldn't access anything. Whilst the 3D effects was downloading a note appeared telling me that recovery memory was 96% and short of space. On rebooting, I got the log in screen and input both my username and password, however it was rejected and returned again to the log in screen - Several times. I stopped for fear of damaging something or other! - I have simply no idea how to proceed at all. Has anyone any ideas how to get out of this and how to ensure it logs in properly in the future?
Many thanks in advance for any help.

---

### Post by geirha on 2007-11-14
It sounds like your / partition is out of space. The easiest way to remedy that, is to boot the livecd, mount your ubuntu-partition there (just open nautilus and you should see your drives in the left frame for you to double-click), and delete something. Look for directories called, or starting with, .Trash and delete their content first.

---

### Post by Rhumpole on 2007-11-14
:) - Geirha, many thanks for the advice. I did all you said, but I'm afraid I still have the same problem...i.e at the log in screen, I input my user-name and password (And lol..yes, they are correct) the screen goes black for a second or two and then the log in screen appears again...And so on...So I'm afraid I'm now rather lost!...But thank you for trying to help me.

---

### Post by geirha on 2007-11-14
At the login screen, press CTRL+ALT+F1 and log in at the console. Are any other partition full? if you have a /home partition, it should not be full either. This command will display the space usage ```
df -h
```

---

### Post by Rhumpole on 2007-11-14
Hi Geirha - Thanks for sticking with me! - Okay, I did that and it reports this:

/dev/hda2   Size 2.3G  Used 2.2G  Avail 0 Use 100%

All the others have - or seem to have stacks of space. The hard drive is 168 GB - And I know that Windows etc has used approximately 19GB.

Where do I go from here please? And again, thank you.

---

### Post by bluedragon436 on 2007-11-14
I am thinking that you are going to need to reload Ubuntu, and give it a bigger partition...It sounds as if when  set up the partition for Ubuntu, you didn't give it any space at all....I guess it was easier for me since I just let it take my whole HD....I would say reload it with a bigger partition...but that is just my info...I have had a similar issue when installing it on another computer...

---

### Post by seachnasaigh on 2007-11-14
Wow, yes. You've got 168 GB of hd space, Windoze takes up 19 GB, and you have /dev/hda2 with only 2.3 GB? I think s/he is right ... you probably don't have enough space allocated to Ubuntu.  When partitioning, some tips:

Your /swap space should be roughly twice the RAM you have. If you have 2 GB RAM, allocate 4096 to /swap. If 1 GB, 2048, for example.

You can have only four primary partitions; keep that in mind. /dev/hda1 is probably your Windoze partition; /dev/hda2 is probably your Linux / (or root) partition. /dev/hda3 might be your Linux /boot partition, don't know since you didn't provide all of the output from df -h. /boot doesn't need to be huge, 500 MB is probably fine. /swap will take one primary partition, Windoze a second, your / (root) a third. You can have a fourth if you like but /boot often takes that up. Everything after that is a secondary partition (for example, /home as a secondary partition under /, or /opt as a secondary ... these are typical Linux partitions that are secondary).

You should probably allocate at least 20 GB to your Linux partition (more if you have 168 GB of space and Windoze is only taking 19 of them!). The installer for Ubuntu has a nice tool that lets it auto partition, you probably ought to take a look at that and see if it doesn't make a slightly saner partition map for you. I think, if you haven't thousands of files already on your computer, you should perhaps consider re-doing the install from scratch and mind your space a bit more.

--ckr

---

### Post by Kedster on 2007-11-14
im a beginner to so this maybe really retarded to say but couldn't his swap partition just be damaged or unwritable  i only say this because i remember reading a simlar post to this one and i think that what was wrong so if i am right (prob not) he could just reformat that partition and mont it as the swap and it might work

---

### Post by geirha on 2007-11-14
> **Rhumpole said:**
> Hi Geirha - Thanks for sticking with me! - Okay, I did that and it reports this:

/dev/hda2   Size 2.3G  Used 2.2G  Avail 0 Use 100%


Is that your / partition? Whichever partition it is, cd into it and try to figure out what's taking up all this space. "du" can be used for this:
```
cd /
sudo du -x --max-depth=1 | sort -g

```
du (short for disk usage) might take a little while. It will show how much space each directory contain. That output is then sorted ( | sort -g ) so that the largest are listed at the bottom.

Do you have your ubuntu installation seperated into several partitions? like /usr and /home? The output of mount would be of help.
```
mount
```

---

### Post by seachnasaigh on 2007-11-14
Good suggestion, actually! The login problem might just be related to that.

ckr

---

### Post by Rhumpole on 2007-11-21
First of all, thank you all for replying and for all the advice - Sorry I have been away (Work got in the way!) - I have tried all that you suggested but with no avail:(. I then downloaded GParted and tried that as well, which reported that there were 28 bad sectors on the volume - I ran CHKDSK which said everyhting was okay!  - As it suggested and rebooted twice, but again with the same result - So the net total is that I am still in the same position - Of course, I can get into Ubuntu recovery and use it but without administrative priviliges. - Soooo! - Any more advice? I'm sorry to be such a bother. I really really don't want to have to format the whole drive.....Many thanks, Rhumpy:)

---

### Post by Rhumpole on 2007-11-23
Thanks very much for all your help everyone. I have now found the bad sectors on the HDD..This it appears is just due to wear. I'm going to back up the the whole disc to an external drive and replace the HDD and then reconfigure Ubuntu - It was just one of those unfortunate things that the partition for Ubuntu came across them! Many thanks. Rhumpy:)

---

### Post by MozartlovesUbun2 on 2007-11-23
:) please mark as solved under "thread tools"

---

