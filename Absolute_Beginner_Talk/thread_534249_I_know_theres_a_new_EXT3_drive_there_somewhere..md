---
title: "I know theres a new EXT3 drive there somewhere."
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by burritomaster on 2007-08-25
Leyt me give you a quick run down of my Set up.

200 GB Hard drive with a 20 GB EXT3 with Ubuntu installed here. Rest is NFTS
500GB hard drive with a 50GB EXT3, rest is NFTS

The 500GB is new, and was formatted in NFTS. I downloaded GParted, partitioned 50GB for Ubuntu, and left the rest for Windows. So In GParted it says I have a EXT3 partition, and a NFTS partition, but neither show up.  Below is a screenshot of GParted.  Im guessing the problem is that my drive isn't mounting, am I right and how do I get it to mount?

[http://bayimg.com/FAGPHaAbe]("http://bayimg.com/FAGPHaAbe")

---

### Post by mikeyphi on 2007-08-25
Places/computer   then right click appropriate disk icon and select mount
There is also a mount option under gparted - I just can't recall where exactly.

---

### Post by louieb on 2007-08-25
Also  you might want to look at [psychocats mount windows]("http://www.psychocats.net/ubuntu/mountwindows") page and add the partition to /etc/fstab to make it permanent. Just change the file system type from **ntfs** to **ext3** in the example and your all set.

---

### Post by alienexplorers on 2007-08-25
Did you assign a partition type for the partitions you made.  By this I mean did you assign a root (/), swap, or /home partition to the partitions you made.

---

### Post by burritomaster on 2007-08-25
No I did not assign a partition type because I didn't have the option. I got it mounted last night with an hour of tinkering, but now I cant write to the disk. Under properties an the permission tab says the owner is root.  Im thinking I have to change the owner to my username. How would I do this?

Update: I figured it out.  I found my answer [here]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fubuntuforums.org%2Farchive%2Findex.php%2Ft-480598.html&ei=OUnQRv7MGZG6gQPB35iVCA&usg=AFQjCNFPHpHpZFRlv-h26-2Kr8EiWXyLvQ&sig2=h9R2VPzR7OxttN98_YwImw"), but thanks for everyones replies.

---

