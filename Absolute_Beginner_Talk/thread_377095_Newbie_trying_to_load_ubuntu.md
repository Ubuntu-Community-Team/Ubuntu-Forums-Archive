---
title: "Newbie trying to load ubuntu"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by gharsh on 2007-03-05
I downloaded the OS from Purdue's site.  It seemed to download ok.  I burned it to a CD and tried to restart my computer with the CD and all I get is XP loading.  I am very new to this linux system and was wondering if I'm doing something wrong.  I have not checked the integrity of the disc yet.  I did notice that is downloads and burns as a Sonic file, does that make a difference?  Is so, how do I change that?  

Thanks for the help.

---

### Post by dosmode on 2007-03-05
Is your BIOS set to boot from CD first? When in Microsoft Windows and you load the CD does it load a window to try different software?

---

### Post by 67GTA on 2007-03-05
You have to download the ISO file and burn it to disc as an ISO image. What type of pc are you using? What are you using to burn it with, and what is the name of the file you downloaded? If none of this makes any sense, start here and post any questions you have: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

---

### Post by gharsh on 2007-03-06
I am using a Compaq computer.  I am using infra recorder to burn the CD.  I had used Sonic originally, but downloaded infra to try that to fix the problem, no avail.  I do not get a screen on startup to use a CD to load from.  When I download the OS, I am getting 698ish MBs.  However, I am not getting the files that the ubuntu's website shows that I should have.  I tried downloading the OS using torrent and I try to "open", "convert", the torrent file using the bittorrent software and I am still not getting the correct things.  

Rember, I'm very new to this.  I have gone into the BIOS and changed the booting order to use the CD driver first but that does not make a difference.  

I'll see what I can find in the help forum, but would like some direction here if at all possible.

Thanks.

---

### Post by esaym on 2007-03-06
> **gharsh said:**
> I am using a Compaq computer.  I am using infra recorder to burn the CD.  I had used Sonic originally, but downloaded infra to try that to fix the problem, no avail.  I do not get a screen on startup to use a CD to load from.  When I download the OS, I am getting 698ish MBs.  However, I am not getting the files that the ubuntu's website shows that I should have.  I tried downloading the OS using torrent and I try to "open", "convert", the torrent file using the bittorrent software and I am still not getting the correct things.  

Rember, I'm very new to this.  I have gone into the BIOS and changed the booting order to use the CD driver first but that does not make a difference.  

I'll see what I can find in the help forum, but would like some direction here if at all possible.

Thanks.


Well then it sounds like you did not burn the cd right.  I can't help you with the burner software you are using because they are all different in windows.  What I can say is that when you go to burn the disk you have to select to burn a disk image, not a data cd, or an audio cd.  Also I am not sure why you have having so much trouble getting an iso.  You just need the iso for the disk you want to make.  No need to try and open the iso file and "convert" it or anything.

Once you are done making the disk from the iso, if you explore the disk in windows it's contents should look something like this:
[[img]http://la.gg/thmb/screenshot6.png[/img]]("http://la.gg/upl/screenshot6.png")

Mind you that is a kubuntu cd.  Your contents might look alittle different but the main thing is that you should  have files and directories on the cd, not just a single iso file.  If there is just a single iso file on the cd then you burned the disk as a data cd and not a disk image cd.

---

### Post by dstew on 2007-03-06
What is the name of the file you downloaded? Did you verify the md5 sum (hash) of the .iso file? Did you carefully follow the burning instructions in [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) ? That is, did you use the Burn Image... option? When you finish burning, and explore the disk in Windows, you should see files and folders, not just the single .iso file, as esaym has said. See also [https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD). In your BIOS, are you sure the CD-ROM drive is ahead of the hard drive in the boot order? Do you have more than one CD-ROM drive?

---

### Post by gharsh on 2007-03-06
I was able to get the correct burn situation and was able to run the OS from the Live CD.  Everything seems to be working okay right now.  I have use of the mouse and keyboard and the OS recognizes my memory stick.

Now, internet access.  I tried to get online today, but did not have any luck.  I can't seem to find where to intput the WEP key and IP address info.  I'm going to head back into the website and see what I can find.

Thanks for the responses.

---

### Post by 67GTA on 2007-03-06
What type of internet connection do you have?

---

