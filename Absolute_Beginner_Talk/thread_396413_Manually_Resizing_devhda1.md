---
title: "Manually Resizing dev/hda1"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by c-breakdown on 2007-03-29
The setup always fails to partition the hard drive and I don't have the option to make a New partition in GParted.  I do have the option to resize dev/hda1 myself, but I don't want to destroy windows, yet.  So should I add free space in this screen to give me somewhere to partition? If I do this will Step 5 of installation work?

[Click Here For Screenshot](http://i17.photobucket.com/albums/b66/hoo1igan/Screenshot.png)

---

### Post by dstew on 2007-03-29
Yes, resize the partition. You can enter 10000 in the box that says Free Space Following, click Resize, then Apply. It should shrink the partition down without hurting your Windows file system, and leave 10Gb of unallocated space. Then, create the new partitions in the unallocated space.

---

### Post by compmodder26 on 2007-03-29
Before doing that, make sure you defragment the hard drive first.

---

### Post by c-breakdown on 2007-03-29
When I tried to do this it failed, here is the result:

[Click Here For Screenshot]("http://i17.photobucket.com/albums/b66/hoo1igan/Screenshot-1.png")

When I clicked close on that screen I was sent to this screen:

[Click Here For Screenshot]("http://i17.photobucket.com/albums/b66/hoo1igan/Screenshot-2.png")

I get the feeling if I continue there I will be over writing windows, am I mistaken?

---

### Post by compmodder26 on 2007-03-29
Did you defragment the disk first?

---

### Post by c-breakdown on 2007-03-29
Yes, I defragged twice.  However, there was some unmovable files when I defragged.  Showed up as a small green line almost all the way to the right of the spectrum.  Is that the root of my problems, and is there anything I can do to fix that if it is?

Could someone please tell me if I should cancel this install process because it will ruin windows?

---

### Post by mcduck on 2007-03-29
> **c-breakdown said:**
> Yes, I defragged twice.  However, there was some unmovable files when I defragged.  Showed up as a small green line almost all the way to the right of the spectrum.  Is that the root of my problems, and is there anything I can do to fix that if it is?

Could someone please tell me if I should cancel this install process because it will ruin windows?

You should boot Windows in safe mode and run defrag there so that it can move those files as well.

---

### Post by psusi on 2007-03-29
Have windows run a chkdsk.  Often there are minor inconsistencies in the volume that don't really cause any harm, but parted will refuse to mess with the volume to be safe.  Once chkdsk cleans it up, it should work.

---

### Post by c-breakdown on 2007-03-29
I have done the chkdsk twice and attempted to run defrag in safe mode twice, but both times it completely froze up on me.  I read the help file for the defrag tool and it says that it doesnt even attempt to move the green areas, so I'm not sure that would fix it.

---

### Post by dstew on 2007-03-29
You shouldn't have to shrink the partition past the green areas to make room for your linux partition. Just shrink by 10Gb, that should be enough.

Did you run chkdsk /f or just chkdsk? Without the /f switch it might not fix problems. Also, it is puzzling that defrag froze up. It might take a long time to defragment, maybe even overnight, but if it "freezes" it should give you an error.

One problem with defragmentation is that if other processes are running that use the disk from time to time, the defragmentation process is stopped and has to start over again.

You said you have tried defragmentation twice. Is the disk actually defragmented? That is, when you click Analyze on the defragmentation tool, does it show the files as only one blue block with green stripes? I don't think you need to be in safe mode to defragment, but it helps because it limits the number of processes running, and can help to get your disk through. However, if the defragmentation process stops, you have to look at your processes and eliminate any that try to use the disk.

---

### Post by c-breakdown on 2007-03-29
Okay, I have ran chkdsk /f multiple times.  I have defragged in Safe Mode and in regular windows twice.  I have tried the alternative install.  I have tried to partition the drive with GParted Live CD and it errors the same as the install.  

[Click Here For Screenshot]("http://i17.photobucket.com/albums/b66/hoo1igan/error.png")

Is there any hope for me or should I just give up? :confused:

---

### Post by mcduck on 2007-03-30
> **c-breakdown said:**
> Okay, I have ran chkdsk /f multiple times.  I have defragged in Safe Mode and in regular windows twice.  I have tried the alternative install.  I have tried to partition the drive with GParted Live CD and it errors the same as the install.  

[Click Here For Screenshot]("http://i17.photobucket.com/albums/b66/hoo1igan/error.png")

Is there any hope for me or should I just give up? :confused:
You could try disabling swap file in windows, although defrag _should_ be able to handle that in safe mode..

---

### Post by c-breakdown on 2007-03-30
Pardon my ignorance, but I have no idea what disabling swap files would do.  Are you saying that if I disable swap files in windows the ubuntu install will allow me to partition my drive?

---

