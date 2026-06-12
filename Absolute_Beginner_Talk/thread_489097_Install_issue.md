---
title: "Install issue"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by davjan4 on 2007-07-01
I just downloaded Ubuntu. How do I install it on my blank HDD? I have it in myCD drive, and I'm at the "R" prompt (cd drive is R). How do I get it installed??

---

### Post by Vajra Vrtti on 2007-07-01
You have to boot you computer from the CD-ROM. It will boot Ubuntu and the you will have an icon in the desktop to install it in the HDD.

---

### Post by paradoc on 2007-07-01
You may like to consider this, too

> Are you sure you have a bootable liveCD?
You did burn it as a iso and not as a bootable CD? As this confuses a lot of new users.
As an example in Nero there is create a bootable CD which is NOT what you want. You want to burn iso to cd.

Some laptops require you to press the C key to boot from cd drive

.............and!.......when you burn it, use a speed not exceeding x4
.............also(belt & braces tip)........use the 'check' facility with Nero, or  do a md5sum if you are able to

---

### Post by davidjmayo on 2007-07-01
try burning this way (the recommended way)

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by davjan4 on 2007-07-01
The disk is good... it works in another computer. I have it at the "A" prompt. can I load from dos?

---

### Post by bigken on 2007-07-01
go into your bios and set the boot order to cdrom 1st

---

### Post by davjan4 on 2007-07-01
Not sure how I cn do that. Since it's a blank HDD (although the bios does recognize it) I have to boot from the floppy, which has the driver on it for the CD drive. I got this disk from Fujitsu last night. They told me that if I put the floppy in with the file they sent me, then booted, it would load what I needed from the floppy then boot from the CD. It did boot and load some itmes from the floppy, and I do get a power light on the CD drive, it just does not boot. All I get on the screen is an "A" prompt. My CD drive is "R", so I do a DIR on it to see hwts there and it does read the CD disk. Just can't get it to boot from that disk. I do have this problem in with Fujitsu to see what they say...

---

### Post by bigken on 2007-07-01
can you give us the spec of your pc 
make and model

---

### Post by bigken on 2007-07-01
the bios has nothing to do with the hdd you need press F2 or delete to enter it 
when you power pc on

---

### Post by paradoc on 2007-07-01
a)It HAS to be a bootable CD (as we mentioned previously....perhaps Fuji supplied something else??)

b) Bigken suggests that you change the boot order to cdrom 1st, then perhaps floppy 2nd and hd0 3d (there are usually 3 choices ....you can always change the order to suit you later--nothing will be damaged or upset (I must have altered these BIOS settings on different PC's countless times over the years)

c)> The disk is good... it works in another computer. I have it at the "A" prompt. can I load from dos?
   ?what does it do in another computer? If it's a 'Live CD' it will boot up to Ubuntu without touching the "A" prompt. I guess from this that you are following the advice from Fuji, which links to the floppy they supplied,and I'm unfamiliar with this procedure, and you will need other help from someone who does it in this way!

However, if you have a live CD as above, and it loads 1st,> It will boot Ubuntu and the you will have an icon in the desktop to install it in the HDD.

Hope this gets you going!

---

### Post by paradoc on 2007-07-01
Add to that--just spotted this on another thread!>  Re: Installing (X)ubuntu from floppy.
You need a bootdisk. It's a floppy which hands over the the CD-Rom. So you can boot from the floppy first and use the CD.. You can either use a dedicated boot disk or run something like smartbootmanager - see [http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)
.............FURTHER HELP..ANYBODY?

---

### Post by paradoc on 2007-07-01
Bump

---

### Post by davjan4 on 2007-07-01
I tried re-arranging the boot order, but I can't get the CD to the top. When I go to the boot screen, all that  shows is the HDD and the floppy, CD is not a choice. When they sent me the bootable floppy I thought that would take care of that, as it does recognize the CD when I boot from that floppy, that is it lists that device as the R drive and I can do a "dir" and see whats on the disk. 
It is a live disk btw that can also be installed on the HDD. But on this computer it's just not working. I guess I'm stuck with spending the $$ on just getting it re-imaged.:(

---

