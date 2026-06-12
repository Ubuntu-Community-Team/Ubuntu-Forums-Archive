---
title: "Install Problem withj 6.06LTS"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by 613 on 2007-02-10
I am trying to install, on another machine, the Ubuntu 6.06LTS from one of the free disks. I'm over writing another Linux system, SuSE Linux 7.3. I chose to wipe the whole disk and do a complete install over the whole machine. Problem is everything goes OK until the actual install is going on in step 6 and I get an error that it can't create the file system and strops at 15%  and keeps trying to "detect" the file system.

Where do I go from here?

Ric

---

### Post by jvc26 on 2007-02-10
Have you md5 checksummed the download and have you checked the cd for errors?
Il

---

### Post by 613 on 2007-02-10
No, how would I do this? Any help would be appreciated.

---

### Post by dckirba on 2007-02-10
To check the disc for errors:

When you put the cd in and reboot, there is an option for checking the disc for errors. Just use the arrow keys to highlight that option and check it.

If you've downloaded the iso, then open a terminal and type:
```
md5sum nameoffile.iso
```
where nameoffile is the name of the iso that you downloaded. It will generate a number that should match the one listed on the site you downloaded from.

There are free utilities to check md5 sums on windows, but I'm not sure what they are. I'm sure googling md5sum+windows will give you what you need.

Hope this helps,
cheers,
David

---

### Post by 613 on 2007-02-10
Thanks David. I will try this and see what happens.:)

---

### Post by jvc26 on 2007-02-10
Apologies for the late response went to grab myself a bite to eat I'd check out here for windows methods of md5checksumming the download:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)
And to check the cd the steps at the start of here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Il

---

### Post by 613 on 2007-02-10
OK, I got it to take the full install all the way up to where it says to restart the machine. When I do that it hangs up with a black screen and the worb GRUB with blinking cursor after it. It has been hung up for 15 minutes now.

What have I done wrong?

Ric

---

### Post by dckirba on 2007-02-11
Hi again,

Did you check the cd for defects? and the guide Illuvator mentioned above is really step-by-step and detailed. Did you follow that?

I'm not an expert, but I think some more information would be useful. How exactly did you go through the install? Maybe that'll help us know what went wrong and where.

Cheers,
David K

---

### Post by 613 on 2007-02-11
Hi. Sorry to be so long getting back to this I just got home from a night of dancing.

I just did the install again this time with a fresh disk. I got 5 free ones so I used another one. I did the check for defects first on it and there were none. It did the whole install process again and when it said to remove the CD and reboot it just went to a black screen and the word GRUB and the cursor flashing after it and nothing can be done from there. it is stuck.

Ric

---

### Post by dckirba on 2007-02-11
Hey ric,

I'm new to linux myself. Cna't really think of anything except maybe reinstalling grub. Take a look here: [http://www.ubuntuforums.org/showthread.php?t=224351]("http://www.ubuntuforums.org/showthread.php?t=224351")

But I'd recommend maybe waiting a bit to see if someone more experienced has another suggestion.

Cheers,
David

---

### Post by 613 on 2007-02-11
Thanks David
I'll try that.
I'll let you know what happens.

Ric

---

### Post by dckirba on 2007-02-12
Any luck?

---

