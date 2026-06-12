---
title: "Full Access (Read and Write) to Internal NTFS Drive"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by SilverDragon on 2007-08-02
I tried following the guide at this link 

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

to be able to write to my NTFS internal drive.

The problem is the option to "Enable write support for internal device" is grayed out but "Enable write support for external device isn't.

It seems as if I'm halfway there.

I also looked at this thread for more insight into the problem but it did not seem to work.

[http://ubuntuforums.org/showthread.php?t=515972](http://ubuntuforums.org/showthread.php?t=515972)

p.s. I've uploaded a screenshot of what happens.

---

### Post by Rocket2DMn on 2007-08-02
Are you running a dual boot?  If so, boot back into windows, load the hard drive and run a check disk on it.  Then disconnect it from the Add/Remove Hardware and reboot into Ubuntu.  This problem can be caused by the hard drive being incorrectly disconnected from a windows system.

---

### Post by SilverDragon on 2007-08-02
Well I am running a dual-boot, but I think your making the assumption that Windows is on one hard drive and Ubuntu is on the other, because if you didn't wouldn't  disconnecting it not let me load up Ubuntu since the MBR(Master Boot Record? I'm not sure what its called?) is on the Windows' drive which is the Master Drive and its written to that to allow me to dual-boot?  (I do have it on seperate hard drives, but maybe this will help someone else if it was on the same one :-) )

Well either way wouldn't disconnecting it not allow me to write/read aka have full access to it? I still need to use it?

I'm rather confused. :-(

Well about a week ago I ran the scan disk on the hard drive and it just goes to a blank screen but I can still hit the del key to cancel it. This might be part of the problem.

---

### Post by Rocket2DMn on 2007-08-02
Oh yeah, internal drive, haha.  I was looking up some possible answers online then forgot it was internal.  I had this problem when I setup my dual boot for my internal AND external, but I can't remember for the life of me how I fixed the problem.  If I remember or run across the answer, I'll get back to you.
Until the, let's try this:
```
sudo apt-get autoremove ntfs-3g
sudo apt-get update
sudo apt-get build-dep ntfs-3g
```

---

### Post by SilverDragon on 2007-08-04
I tried the 3 lines in the terminal and I got the same result :-(

Thanks for the effort though :-)

---

### Post by kelvin spratt on 2007-08-04
You have to sort your Windows drive first before it will mount in Linux, the drive will not be read properly if it is not clean, their are umteen threads on this forum explaining how to go about it if you look, but basicly you need to do a forced disc check on windows then in bottom right hand corner of toolbar locate safely remove hardware double click on the screen click ok. shut down turn off  windows completely, then restart do this twice don't just restart as it does not turn of the system, boot up Linux then check your drive, if still not working remove and install ntfs3g turn off and restart this should mount the drive.

---

### Post by ashlakim on 2007-08-24
Hi there. I am a ubuntu FFawn newbie and i experience the 'greyed out' part of the enable read-write on internal ntfs. I absolutely have no idea how to fix this, i ve tried some of ur recommendations but still to no avail. the ehing is, i cannot copy downloaded plugins for softwares like amsn into the drive. Will you help me please???

---

### Post by TeaSwigger on 2007-08-24
> **ashlakim said:**
> Hi there. I am a ubuntu FFawn newbie and i experience the 'greyed out' part of the enable read-write on internal ntfs. I absolutely have no idea how to fix this, i ve tried some of ur recommendations but still to no avail. the ehing is, i cannot copy downloaded plugins for softwares like amsn into the drive. Will you help me please???

I just installed NTFS write support too, and experienced the behavior being described. But what I did was to close the app and reboot, then try it again. It worked correctly when I did and read-write on NTFS is working fine. Perhaps some sort of bug in the GUI of the app? No idea. May not solve it for anyone else but thought I'd offer the suggestion.

---

### Post by ashlakim on 2007-08-24
Thanks for the suggestion. So for now, i have installed the NTFS config. So all i have to do next is just reboot?

---

### Post by ashlakim on 2007-08-24
i have rebooted my ubuntu and still the 'enable read write internal drive' greyed out -> meaning i cannnot copy and paste plugins to my 'hard drive'...

To make sure, i have shut down and swith my machine back on and the results are the same.


I am now not on dual boot. My machine purely runs using ubuntu FFawn as iits OS.

How am i going to enable read write on internal drive? Though i enabled -read write on external drive i still unable to transfer things to my pendrive though i can read the contents.

Please help meout

---

### Post by albertmatyi on 2007-12-09
I had the same problem. 

Enable write support for internal devices grayed out.

The solution for my problem was:

run (alt+f2): gksu gedit /etc/fstab

and i added the lines:

/dev/hda1 /media/sys_xp ntfs-3g rw 0 0
/dev/hda5 /media/stuff ntfs-3g rw 0 0

after restart my partitions were automatically mounted, and 
the option Enable write support for internal devices was not grayed out anymore and it was selected.

hope this helps.

---

