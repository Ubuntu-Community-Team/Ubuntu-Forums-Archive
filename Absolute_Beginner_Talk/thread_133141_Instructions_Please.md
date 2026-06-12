---
title: "Instructions Please"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by jasrog on 2006-02-19
I am once again trying to get my dual boot successfully done with full read and write capabilities I have 2 partitions set up, windows is on 1 and partition 2 is available and unformatted...how exactly step by step do I Install Ubuntu 5.10 with full read and write capabilities? Windows is in NTFS....

---

### Post by nalmeth on 2006-02-19
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) 
for dual booting with windows
you won't have full read/write ability from ubuntu to your windows partition, because ntfs is only readable by non MS systems --> and this ability was reverse-engineered.
If you just installed windows fresh again, you may want to consider creating a fat32 partition for it instead, which ubuntu can fully read/write. Then when installing windows, tell it to use your created fat32 partition. 

[http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu](http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu) this video may be of use to you.

---

### Post by jasrog on 2006-02-19
I tried that with gparted from ubuntu live cd and windows partition manager could not recognize.... do you know of a partition editor that windows can recognize?

---

### Post by nalmeth on 2006-02-19
hmm hmm
i wish I knew more about partitioning, but since I don't own windows, I only run ubuntu, and have never need to partition anything...
I don't think it makes a difference what app you're using to create the fat32 partition, but I wouldn't be suprised at windows wanting one made with a windows app. Can you get partition magic? I hear that is really good, but don't know if its free

that video is really good, if  you're looking for step by step instructions, although their setup may not be what you're looking for.. 

Also, I think you could create a third partition (best be a fat32) to share all personal data between ubuntu and windows. maybe this would work better for you.

EDIT:
Remember windows won't even acknowledge the existence of ubuntu, so you won't be able to see ubuntu's files from windows.

---

### Post by jasrog on 2006-02-19
without full read/write capabilities from ubuntu to windows what exactly will I not be able to do? Does that harm the way Ubuntu runs?

---

### Post by nalmeth on 2006-02-19
> without full read/write capabilities from ubuntu to windows what exactly will I not be able to do? Does that harm the way Ubuntu runs?

It doesn't harm anything, it just means you won't be able to save anything onto your windows partition, or change anyfiles on the windows partition. You can't even rename an mp3. You will be able to play that mp3 though, and copy it over to your ubuntu partition.

From windows though, you won't even be able to see your ubuntu. ANYWHERE <-- i stand corrected [http://www.fs-driver.org/](http://www.fs-driver.org/)
I haven't used it myself obviously, but looks interesting

---

