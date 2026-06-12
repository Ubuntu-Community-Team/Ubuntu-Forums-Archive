---
title: "Installing"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by M0nk3yM4n on 2006-06-14
Hey can anyone tell me or redirect me to what I need to do in order to install Ubuntu? I used Partition Magic to create a 3 gig partition in between my two NTFS partitions that is Ext3 or whatever. When I tried to install Ubuntu it said that it needs a 256 mb swap partition so I told the Ubuntu thing to seperate 500 megs of space for another partition from that 3 gig partition. However when it was time to start it said that the data on all my partitions was going to be deleted!!! Did it just me that one 3 gig partitions or all of them? I'm really afraid of losing my data what should I do? What kind of file systems should I use? Paritition magic has ext 2 3 and another and then Ubuntu had like XFS and such.  Should I just use Paritition Magic again to split that 3 gig partition up?

---

### Post by bruce89 on 2006-06-14
You'll have to use manual mode in the installer, otherwise it will format the whole disk.

---

### Post by az on 2006-06-14
[QUOTE=M0nk3yM4n]However when it was time to start it said that the data on all my partitions was going to be deleted!!! ....  Should I just use Paritition Magic again to split that 3 gig partition up?[/QUOTE]


A lot of people have has issues with partition magic.  I find the built-in partitioner the most relable.  What you can do to be safe is to start the install, at the partitioning step, just go to the manula partitionner and then delete your ext3 partition.  Then go back to the beginning of the  partitioning step and it will offer to use the free space.

It will then create the two partitions for you.  That would be the easiest way to go.  Actually, the easiest thing would have been to not pre-partition, but just take the default which would have been for the ubuntu installer to shrink down one of your nfts partitions for you.

---

### Post by M0nk3yM4n on 2006-06-14
Ok I'm in Ubuntu right now running off the disc how do I take a snapshow of my desktop to show you where I am at? 

I used PM8.0 again to turn that 3 gig into a 2.5 ext3 and a 500 swap then when I select "/' to be the 2.5 gig and then swap to be the 502mb partition I click forward to step 6 and then it says...

"Partitioning:
  If you continue, the changes listed below will be written to the disks.
  Otherwise, you will be able to make further changes manually.

  WARNING: This will destroy all data on any partitions you have removed as
  well as on the partitions that are going to be formatted.
"
This does mean that my entire laptop hard drive will be gone correct? :sad:

---

### Post by bruce89 on 2006-06-14
[QUOTE=M0nk3yM4n]Ok I'm in Ubuntu right now running off the disc how do I take a snapshow of my desktop to show you where I am at? [/QUOTE]
Print Screen.  Also 2.5GiB sounds a bit small for a root partition.

---

### Post by M0nk3yM4n on 2006-06-14
[http://ubuntuforums.org/attachment.php?attachmentid=11223&stc=1&d=1150319403](http://ubuntuforums.org/attachment.php?attachmentid=11223&stc=1&d=1150319403)

So now check this out...I deleted the partition I made with PM and used the Manager in Ubuntu to make a swap and a ext3 and for some reason after it is done they turn into Unknowns?? 

I wish I had more space on my laptop!! :sad: :sad: :sad:

---

### Post by givré on 2006-06-14
NEVER using partition magic to fomat a partition in ext2 or ext3.

---

### Post by bruce89 on 2006-06-14
Why is there 2 NTFS partitions?  I'm not sure about the errors, it might have to do with the fact they are in an extended partition.  Another problem might be the fact that there is little free space.

---

### Post by M0nk3yM4n on 2006-06-14
There are two NTFS partitions because I have windows installed already on ten gig partition and just storage on the other ~70 gig partition. 

I used PM to take some free space from both drives to make the extended partition I was going to install Ubuntu on.  

I guess I'll just reformat my 10 gig format and split in half with no extended partitions for Ubuntu and Windows. I was just trying to get around this hassle =(

---

### Post by givré on 2006-06-14
[QUOTE=M0nk3yM4n]Ok I'm in Ubuntu right now running off the disc how do I take a snapshow of my desktop to show you where I am at? 

I used PM8.0 again to turn that 3 gig into a 2.5 ext3 and a 500 swap then when I select "/' to be the 2.5 gig and then swap to be the 502mb partition I click forward to step 6 and then it says...

"Partitioning:
  If you continue, the changes listed below will be written to the disks.
  Otherwise, you will be able to make further changes manually.

  WARNING: This will destroy all data on any partitions you have removed as
  well as on the partitions that are going to be formatted.
"
This does mean that my entire laptop hard drive will be gone correct? :sad:[/QUOTE]
That's sound correct, if you selected to format only sda6 and sda7, and if you set the good label (ie / for sda6 and swap for sda7) that should be ok

---

### Post by az on 2006-06-14
[QUOTE=M0nk3yM4n]I guess I'll just reformat my 10 gig format and split in half with no extended partitions for Ubuntu and Windows. I was just trying to get around this hassle =([/QUOTE]
No.  Just remove the partitions that PM8 screwed up for you.  You don't have to reformat.


Also, that error you quoted just means that the data on the partitions youselected wll be erased, not the entire disk!

---

### Post by az on 2006-06-14
[QUOTE=M0nk3yM4n]
"  WARNING: This will destroy all data on any partitions you have removed as
  well as on the partitions that are going to be formatted.
"
This does mean that my entire laptop hard drive will be gone correct? :sad:[/QUOTE]

It does not mention the partitions that you did not touch, so this is okay.  As long as you didn't tell it to delete your windows partitions....

---

