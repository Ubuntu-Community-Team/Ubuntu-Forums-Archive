---
title: "Ubuntu now completely dead."
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by Kouki on 2006-10-24
Strange, my first post was only about half an hour ago re a SPM problem.  Whilst trying to fix it I thought I'd mount my windows drive manually using terminal to listen to some music.  I did this and ubuntu became unresponsive.  I couldn't open the terminal to type in the suggestions on how to fix SPM from the original thread.  So I restarted.

Well, now I'm back in Windows, this was the result of my restart:

[IMG]http://i16.photobucket.com/albums/b15/stuarthyden/Image078.jpg[/IMG]

[IMG]http://i16.photobucket.com/albums/b15/stuarthyden/Image079.jpg[/IMG]

Er, almost trouble free since august then it springs two major problems on me.  I can't even get into Ubuntu now :-({|=

---

### Post by daemonoid on 2006-10-24
You should try doing pretty much what it says.

First enter your password to log in to command line as root.

then mount -n -o remount,rw /

then run fsck

report back with what you get from that.

---

### Post by ehird on 2006-10-24
run a manual fsck?

---

### Post by Bartender on 2006-10-24
You're not back in Windows.  That's all Linux on your screen.
EDIT: I'd guess hardware problems, maybe power supply failing.

---

### Post by Kouki on 2006-10-24
No, I mean I've had to reboot into windows from my other hard drive using grub now.  The screenshots above are the ones that come up when I try to start ubuntu.  Doubt its powersupply as I'm on the same computer now writing this, only in windows and my pc setup is only about 6 months old.

Just followed the instructions as suggested and it came up with this message that put me off.  Should I just run it?  All my important data is on my windows drive, so I've not got much to lose other than all my installed programs and a couple of songs.

[IMG]http://i16.photobucket.com/albums/b15/stuarthyden/Image081.jpg[/IMG]

---

### Post by bapoumba on 2006-10-24
Hi again,

your system needs some repairs. Enter your password, just as daemonoid said and check which partition is corrupted. Looks like it is your root partition, so **~#df -ht /** will make sure /dev/hdb1 is your / and that it is ext3.

You might prefer **~# e2fsck -f -y -C0  /dev/hdb1** if an ext2 or ext3 file system, or **~#fsck -f -y /dev/hdb1** which will check the file system type.
Have a look at **man fsck**.
This process might take some time.

Then, remount your partition **~# mount -n -o remount,rw / ** and **~# reboot**

edit : did not see your last message. fsck should not be done on a rw mounted partition.
To remount it read only **mount  -n -o remount,rw /**, but if you just entered your password, you should not have to do that.

---

### Post by Bartender on 2006-10-24
Jeez, that is a scary-looking warning there...
And it's all greek to this newb.  One question.  Are you sure you won't wipe out your Windows installation?  As long as your Windows data is safe you haven't got much to lose, eh?  How much of a hassle would it be to just reinstall Ubuntu from scratch?

---

### Post by Kouki on 2006-10-24
> **Bartender said:**
> One question.  Are you sure you won't wipe out your Windows installation?

In a word, No ](*,) 

I wouldn't mind learning how to fix it rather than just installing ubuntu again, just incase it pulls this trick on me at a later date.  I'll try unplugging the ide cable from the windows disk so that its safe and then running it.

---

### Post by frodon on 2006-10-24
Don't worry Kouki, i add this issue 1 years ago and it will be solved without any problems.
Run the fsck on the drive but don't mount the partition with write support before the fsck as daemonoid mistakenly suggested.

Just follow the text :
1- run the fsck command on the partition : fsck /dev/hdb1
2- mount it with write support : mount -n -o remount,rw /
3- reboot

If you need assistance on these steps we are here, and don't worry all will get back to normal after that.

---

### Post by Bartender on 2006-10-24
frodon -
Any thoughts on what could cause this?  If I were just getting into Linux and had to fix the installation I'd be freakin' out a little bit :confused:

---

### Post by Kouki on 2006-10-24
Excellent, good news - thanks.  Although I'm now using the live cd because after turning my pc off and pulling out the windows drive ide, I started up and my bios told me that I had no operating system installed.  So I switched off the pc and plugged it back in, turned it back on and still no operating system installed.  Basically, its not getting through to grub.  It did this once when I first installed it and I had to install ubuntu and grub again to fix it.

I don't intend having to do that now, so I'll try to work out the problem :)

---

### Post by frodon on 2006-10-24
Just to let you know that if you have a live CD, you can easily reinstall GRUB, instruction are there :
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Kouki on 2006-10-24
> **Bartender said:**
> frodon -
Any thoughts on what could cause this?  If I were just getting into Linux and had to fix the installation I'd be freakin' out a little bit :confused:

I'm pretty certain it was a problem that arose when I tried mounting my windows drive using the unofficial ubuntu guide.

---

### Post by frodon on 2006-10-24
You mean you partition corruption ?
I don't think so, harddrives which are more than 1 year old always start to lose some clusters and if it is a cluster where datas are present then you get corruptions errors, I have to warn you that it could be a sign that your harddrive will die soon (maybe not) so if i were you i would start to backup important datas from this drive just in case.

---

### Post by Kouki on 2006-10-24
> **frodon said:**
> You mean you partition corruption ?
I don't think so, harddrives which are more than 1 year old always start to lose some clusters and if it is a cluster where datas are present then you get corruptions errors, I have to warn you that it could be a sign that your harddrive will die soon (maybe not) so if i were you i would start to backup important datas from this drive just in case.

Ok, I'll put anything important on my external drive, just in case.  I could do with a nice new raid drive now anyways, now that my motherboard supports them :)

---

### Post by Kouki on 2006-10-24
That went wrong! :shock:  since unplugging the hard drive and then plugging it back in I couldn't get back to the necessary screen to carry out the instructions.  I reinstalled grub, but whilst I could then boot to grub,  trying to boot any operating systems from there resulted in an error.

Luckily I've grown up with windows and managed to enter the recovery console and run chkdsk which returned 0 errors.  I then wrote a new startup sector, and then repaired the startup partitions master boot code.  So windows is back with all my files thank God!

Now I think I've screwed my ubuntu installation so badly that no one will be able to recover it.  Luckily there wasn't much on there so I'll start my ubuntu experience afresh.  At least now I know what to do and what not to do if this problem happens again.  

Thanks for the help, just a shame I unplugged the hard drive before receiving the advice.  I still don't know why doing that prevented anything from booting once reconnected, but it did.  Ah well, you live and learn.  Luckily I have xp pretty much mastered as I've built quite a few systems and had a few major xp failures in the past that I've learnt to fix when systems wouldn't boot.

To any other newbies who manage to screw their computers up in the same way as me so that nothing boots, here's how to get windows back.

Put in windows cd and reboot.
Follow instructions to bring up recovery console.
Type the number of the disk you want to repair, then hit enter.
Type in administrator password, hit enter.
Type 'fixboot', hit enter
Type 'Fixmbr', hit enter
Type exit and reboot.

You'll have windows back and can breath easy again.

---

### Post by gn2 on 2006-10-24
This may be interesting reading: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

