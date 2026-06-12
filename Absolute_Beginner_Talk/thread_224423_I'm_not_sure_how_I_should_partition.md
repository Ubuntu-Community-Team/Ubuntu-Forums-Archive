---
title: "I'm not sure how I should partition"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by JS Lemming on 2006-07-27
Hello. This is my scenario: I currently have win98 on my 40gig disk. The disk is almost completely full to the max, very old, and can't be trusted to last much longer. So, I have a fresh new 120gig disk and would like to clone the old 40gig disk onto it.

Now, I've never pilfered in Linux before (beyond recently fooling around with the Live CD) so I think I'll give Ubuntu a shot. I like it from what I've seen so far.

I've read through [this]("http://www.psychocats.net/ubuntu/partitioning.html") and I'm a bit confused. I've never partitioned anything in my life, I just don't want to screw anything up. I guess the best scenario from the site for me would be (even though I think win98 uses FAT32 instead of NTFS [that shouldn't effect me should it?]):
[IMG]http://www.psychocats.net/ubuntu/images/partitioning4.png[/IMG]

After reading through [this]("http://www.psychocats.net/ubuntu/installing.html"), I don't think I know enough to actually go in and create something like the picture above.

Can anyone give me a few pointers for when I get in there and am asked to partition?

---

### Post by grimmson on 2006-07-28
My suggestion is to clone your old hard drive to your new drive. I personally use Maxtor drives. The maxblast install cd should do this for you.
Step 1)READ THE DIRECTIONS. If you don't understand please ask us (your already on the right track.)
2)Copy old drive to new drive using a 60 gig partition if possable(They may want you to defrag first.)
3) DISCONNECT old drive to preserve it. If you move all your files to the new drive and disconnect the 4 pin power supply and ribbon cable to the old drive ,you can mess up your new drive, disconnect it, reconnect the old and be safe.
4) Boot on your new drive to make sure windows works well.
5) Read up on resizeing a windows partition,Boot the install cd, resize your windows so you have more space in windows.
6) install ubuntu on the second half of the new hard drive and play to your harts content because your old drive is still in your computer DISCONNECTED and safe.

to answer your questions: If you resize the new drive to 60 gig using the manufactures tools and copy windows to it and select the unpartitioned space for ubuntu there is an automatic option for the linux stuff. Your drive WILL differ from the picture.

Step one and 5 Both resize. If you can clone and resize your windows partition at the same time using "Your disk manufactures tools" then do it. If you cannot resize I've had linux resize a ntfs partition so you can do that in step 5.

---

### Post by srikat on 2006-07-28
You don't need to create swap, / and /home partitions.

After cloning your old disk to the new one, you can resize windows on the new disk and this will create unpartitioned space. Then partition it as ext3. You just point this new partition to the Ubuntu installer. It'll take care of the rest. 

(Others: correct me if am wrong..I am new to Linux myself)

---

### Post by Sef on 2006-07-28
> ou don't need to create swap, / and /home partitions.

You should create a swap if your ram is less than 1 gb.  A home partition is optional, but nice.  If you remember to back up your documents regularly then a home partition isn't that necessary.  However, if you're like me and don't always back them up on schedule, then a home partition is very nice to have.

---

### Post by grimmson on 2006-07-30
did it work?

---

