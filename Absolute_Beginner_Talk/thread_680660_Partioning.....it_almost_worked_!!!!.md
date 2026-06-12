---
title: "Partioning.....it almost worked !!!!"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Chris2169 on 2008-01-28
Hi folks,

Well I'm back again, having just got ubuntu working correctly and found replacement programs.....my laptop motherboard shorted out (not connected I hope !).  Anyhow one new laptop later and I'm back !  

Obviously one of the first things I've done is to convert it to dual boot, I've deliberatley not set up any of my apps in vista as I want to see if I can manage to do without it all together. Enough chat there is a question coming honestly.

The laptop is an Advent;

Dual Core
2gig Ram
120gig HDD

So I thought it would be a good idea to try and set it up as per psychocats advice here: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) (see I do read the advice I'm given here !!!)

I'm trying to achevie the three partion option, one for vista, one for ubuntu and a shared on for data.

So what I've finshed up with looks like this

in Vista; 	Vista (c:) 57.2Gb
		   Local disk(z:)

in Ubuntu;  Recovery 4Gb used-1.6Gb free
		 Vista 15.5Gb used-41.7Gb free
		 File system 2.3Gb used-2.6Gb free

Now those of you that have been paying attention will notice there is a huge chunk of HDD missing !  This is the bit represented by 'Z' on vista but ubuntu can't see it all.  I suspect this is because I haven't formatted it. But I understand it needs to be Fat32 to allow both ubuntu and vista to read and write to it ? ( is that correct ?).  This being the case vista won't allow me to format it as anything other than ntfs.

So the main question is can I format that section with something in ubuntu ? Will vista still be able to read and write to it ?  Have I acheived what I think I've achevied or have I unwittingly done something which is going to cause me a load of trouble later ?  If I have please be gentle with me, I'm right on the edge of my technical understanding doing this....

Apologies if this is a very long winded question but I have been gently advised to give more information in previous posts so this time you've got it all !!!  Many many thanks to anyone who's got this far and even more thanks to anyone who can contribute.

Chris

---

### Post by forestpixie on 2008-01-28
format it to ntfs - ubunut will use it fine - you could use partition editor from the livecd or use the vista disk management tool - I'd perhaps opt for the second

you'll probably need to use ntfs-config in ubuntu - but first steps first

---

### Post by CheShA on 2008-01-28
Check you have gparted installed then run 
System > Administration > Partition Editor

you can then use the gui to select the partition and format it to vfat 

or, from the command line, use the command 
```
mkfs.vfat /dev/hd?? 
```
Obviously, in this case "hd??" should be the location of the partition you wish to share.

---

### Post by CheShA on 2008-01-28
NTFS will largely work OK using  ntfs-3g (which, I think is installed by default on Gutsy) but ideally you still would need windows installed  e.g. if you ever needed to run chkdsk because Linux still can't do this properly (damn closed spec file system) , and if your drive ends up scheduled for a check then it won't mount properly until it has been checked.

Be a REAL man, format to ext3 and ditch the Windows partition for good ;)

---

### Post by bumanie on 2008-01-28
These days there is no real need to have a /shared partition as ubuntu (from 7.10) has ntfs-3g as part of the kernel which allows reading and writing to ntfs. There is also an opensource program (not sure of the name of it) that can be installed to windows that allows reading and writing to ext3. This seems to be the way of future (so to speak), I would look at utilising these tools if I were you.
I can't tell you how to use them as I have not found the need - I use ubuntu 99% of the time.

---

### Post by CheShA on 2008-01-28
> **bumanie said:**
>  There is also an opensource program (not sure of the name of it) that can be installed to windows that allows reading and writing to ext3. 

This is a kernel mode driver for Windows; for the record, since Vista 64 will only allow signed kernel mode drivers, this driver cannot be loaded in Vista 64.  If anyone's  planning to go this route, you'll need to find a hack round this.

---

