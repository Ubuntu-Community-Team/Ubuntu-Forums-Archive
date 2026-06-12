---
title: "Installation - partitions"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by GoneWithTheWind on 2006-09-18
I've managed to d/l the iso file for Ubuntu, transferred it to cd, checked the integrity, and have been trying to install it for the last couple of days.  Preparing disk space wouldn't work on "Resize", so I went to manual editing, which I set up as follows:

#  19 gb  ntfs
#  47 gb  ext3
#   9 gb  ext3
#   1 mb  linux-swap

All looked well so I clicked to "Apply".  Then when it was done, bingo only one partition showed up, which was ntfs with all 75 gb and wouldn't allow any change.  I wondered if all was well anway and this was just a misnomer, but didn't want to take a chance and "cancelled" the installation.  In retrospect I should have continued, as the partitions had already been made (I wasn't sure about that).

Now my computer shows this:

Local Disk Total Capacity:  17.69 gb
Sum of Hard Disks ( C: )
  Used:  16.96 gb
  Free:  740.36 mg

So.... 

How can I tell if the other 3 partitions were indeed made properly, where they are, and how to get Ubuntu on them, with including Ubuntu as a boot?

Thanks much for your helpful responses.

---

### Post by cotcot on 2006-09-18
Download and burn the GParted liveCD. It is much better than the install CD.
Try also the Dapper alternate installCD.

---

### Post by bulldog on 2006-09-18
If you're in windows which I presume,right click on your My Computer icon.
Choose manage or something like that [long time ago] in the menu.

You should see an option disk management where all you're partitions should show up.
The only thing is Windows can't read ext3 so your linux partitions should be there as 'unknown'

So you can see if it's all there.

---

### Post by GoneWithTheWind on 2006-09-18
Thanks, I'll get GParted and try the Dapper alternate. 

Windows | my computer is showing only C: with 17.6 GB, nothing else.

---

### Post by GoneWithTheWind on 2006-09-18
The two isos are ready to burn.

Is it better to put them on the same disk or on two?

---

### Post by GoneWithTheWind on 2006-09-19
I put them on different CD's.

The GParted liveCD worked greattttt.. I love it when everything goes so smoothly.  :D 

The Dapper alternate installCD is excellent too.  At least it was until I got past partitions, then everything I clicked kept putting me back in partitions again.  I kept checking and double checking, everything was fine, then I'd try to move on and get flipped back in there again.  #-o 

I didn't know what software raid and multidisk volume manager were, so clicked "finish" and "leave" for those.  Then when I clicked "install the base system" it flipped me back to partitions.  I'll keep trying to figure this out but if anyone has any ideas please let me know.  

Other than not getting through the very last part, I like this dual alternative method "much" better than the regular way.

---

### Post by GoneWithTheWind on 2006-09-19
To clarify, I set the partitions up withGParted liveCD as follows:

#1-  17.5  ntfs  primary
#4-   5.0  ext3  primary
#5-  50.0  ext3  primary (wouldn't let me do logical)
#6-   1.0  linux-swap  primary . . (ditto)

This worked like a charm.

Then in the Dapper alternate installCD I changed the /'s to:

/windows
/
/home
swap

It was strange as GParted added up to 74.5546 GB, the same as usual, and the alternative CD showed 80.1 GB.  I wasn't supposed to format the partitions again because of putting the /'s in there was I?

---

### Post by tommcd on 2006-09-19
Ignore the "software raid" and "multidisk volume manager part". They are different options. Just select "resize existing partitions" to resize or "install on existing partition". (I think that's what the options are called, it's been a while since I seen them). At the end just select "finished editing" and it should let you go on. You need to select "linux swap" for the swap partition file type also, or it won't let you proceed.

---

### Post by GoneWithTheWind on 2006-09-19
Thanks.  

This morning I tried again and the same thing was happening.

While trying to get past partitions, I discovered that the screen went down farther at the bottom.  It looks like there is nothing more on there but there is.  So anyone trying this for the first time, be sure to see if the arrow keys move up anything else from the bottom.  I figured the issue was something on the partitions screen, possibly with the labels, so I experimented with those.   There is no linux swap, just swap file, but that worked okay.  Then qparted wouldn't let me change the ntfs one (I changed it to FAT2 and it wouldn't go back) so I rebooted and tried again.  

The qparted liveCD is great as it remembers your previous settings, and it's FAST!  

I got back in and the 4 partitions had reverted to /media/hda1, so I changed them all back as above, then thought hmm maybe that is the issue.  So I left the first one as /media/hda1 instead of /windows.  Viola!!!!  Now the screen progressed and all went quickly from there on.

Ubuntu is loaded!!!!  

I checked Firefox and a few other things.  All looks greattttt.  Next is to get the dual boot, tweak all the settings and start using it more.  I'm excited about this.  I've chatted with a few people in the meantime and it seems quite a few have tried linux but gave up on the installation.  In my opinion the qparted liveCD and Unbuntu alternative liveCD downloads and installs are the much better way to go.  

If anyone is having problems with the regular install, or just wants a much better, faster, and easier way to go about it, try these.

---

### Post by GoneWithTheWind on 2006-09-19
The partitions ended up this way:

ntfs  primary 17.5  /media/hda1
ext3  primary  5.0  /
ext3  primary 50.0  /home 
ext3  primary  1.0  swap 

The alternative install live CD showed the partitions as being a bit larger, but that didn't affect anything.  

The only things I changed were the htfs/ext3's and the /'s.

---

### Post by GoneWithTheWind on 2006-09-21
For those looking to find your ext3 partitions on a windows xp, take a look here:

start
control panel
administrative tasks
computer management (local)
storage
disk management

---

