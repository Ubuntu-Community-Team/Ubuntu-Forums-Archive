---
title: "Desperate need of help with uninstall or ?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by BigFatPapa on 2008-03-27
Hi,

I am an absolute noob!  I had just installed ubuntu to run dual boot with the live cd, worked wonderfully, just learning my way around.  I left my laptop open and my granddaughter thought she was helping and clicked on the install and ubuntu over wrote the windows and there was not partition.  I NEED MS windows for work, no and if or buts about it. 

It is Vista, I have a restore/back up disk as vista preinstalls do not come with a disk.  

What do I need to do to restore the windows.  Please be very specific as I am not computer savvy, I can get around them, but I know very little.

Can I uninstall, some how?
Can I partion ubuntu and install windows?

Please help!!! 

Thanks,
Tom

---

### Post by spiderbatdad on 2008-03-27
Ubuntu has to specifically be set to remove Vista. It does not happen by default. Are you sure Vista is gone? ```
sudo fdisk -l
```will show you.
Anyway there are 100's of posts regarding sticking your vista cd in and reinstalling vista.

---

### Post by BigFatPapa on 2008-03-27
Again, total noob, do not know a thing. 

Where and how do I put sudo fdisk -1 ?

Thanks again,
Tom

---

### Post by louieb on 2008-03-27
> **spiderbatdad said:**
> .. Are you sure Vista is gone?...
I agree grandkids can be fun,  play with them and send back to mom and dad. 
To post the fdisk output: Open **Applications>Accessories>terminal**. and type in the command spiderbatdad gave you. Cut and paste the output in your next post. Then we can see where you need to go from there.

---

### Post by BigFatPapa on 2008-03-27
[ sudo] password for me: 

I try to type password, nothing but a flashing cursor.


Yea, I love her to death and I feel bad that I got upset with her.

---

### Post by dummyhead3 on 2008-03-27
1- It is supposed to delete everything by default
2- I'm pretty sure Vista is gone and you will need to restore your system completley.. you must order some recovery CDs from the manufacturer of your PC or if you have the Vista CD you can use that as you did with the Live CD or there is usually a hidden recovery partition on most PCs..  when you start your PC it should say what to press in order to do a system recovery... or the best option in my opinion is stick to UBUNTU!! it is not very hard to learn.

---

### Post by BigFatPapa on 2008-03-27
fdisk: invalid option --1

Usage: fdisk [-b SSZ] [-u] DISK           Change partion table
            fdisk -l [-b SSZ] [-u] DISK         List partition table(s)
            fdisk -s PARTITION                  Give partition size (s) in block
            fdisk -v                                     Give fdisk version
Here DISK is somthing like /dev/hbd or /dev/sda
and PARTITION is something lik /dev/hda7
-u: give Start and End in sector  (instad of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


I typed the password, duh

---

### Post by BigFatPapa on 2008-03-27
> **dummyhead3 said:**
> 1- It is supposed to delete everything by default
2- I'm pretty sure Vista is gone and you will need to restore your system completley.. you must order some recovery CDs from the manufacturer of your PC or if you have the Vista CD you can use that as you did with the Live CD or there is usually a hidden recovery partition on most PCs..  when you start your PC it should say what to press in order to do a system recovery... or the best option in my opinion is stick to UBUNTU!! it is not very hard to learn.


I tried to do it like the live cd.  Nothing worked.  I have to have windows for work.

---

### Post by louieb on 2008-03-27
the command is ```
sudo fdisk -l
``` (lower case L)
Like to help but really need to see the output of the fdisk command.

---

### Post by ByteJuggler on 2008-03-27
> **BigFatPapa said:**
> fdisk: invalid option --1

Usage: fdisk [-b SSZ] [-u] DISK           Change partion table
            fdisk -l [-b SSZ] [-u] DISK         List partition table(s)
            fdisk -s PARTITION                  Give partition size (s) in block
            fdisk -v                                     Give fdisk version
Here DISK is somthing like /dev/hbd or /dev/sda
and PARTITION is something lik /dev/hda7
-u: give Start and End in sector  (instad of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


I typed the password, duh

It's -l not -1 (hyphen-lowercase-l, not hyphen-one).

---

### Post by 1875 on 2008-03-27
> **BigFatPapa said:**
> fdisk: invalid option --1


I typed the password, duh

Not 1 but l as in L little brother.:)

---

### Post by 1875 on 2008-03-27
> **ByteJuggler said:**
> It's -l not -1 (hyphen-lowercase-l, not hyphen-one).

Beat me to it.:lolflag:

---

### Post by BigFatPapa on 2008-03-27
louie

I am on the forum from my sons computer while looking at the ubuntu computer.

Here is what I got.

Disk /dev/sda 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units= cylinders of 16065 * 512 = 8225280 bytes
Disk identifierL 0x61c6b961

Device          boot   Start    End          Blocks        Id     System
/dev/sda1      *        1         18796 150978838+ 83      Linux
/dev/sda2            18797     19457     5309482+   5      Extended
/dev/sda5            18797     19457     5309451     82     Linux swap / Solaris

---

### Post by louieb on 2008-03-27
Windows is gone. Have you tried booting with your restore / backup disk?

Try that 1st.  
If that doesn't work then get back and I'll go over how to format the disk for windows.

---

### Post by BigFatPapa on 2008-03-27
louieb

Rebooting with the restore disk is the first thing I tried. Please show me how, I would like to keep the ubuntu installed or if not possible I would go back to using the live CD.  Which I just got.  

Thanks for all your help and patience with my l blunder and all :)

---

### Post by louieb on 2008-03-27
So it doesn't boot to the recovery CD? It should work the same as booting the Ubuntu Live CD.  
Acer recovery is the only one I've used. What kind of PC is it? Do you have the user manual?  I'd like to look at manufactures web site. 
 
The fdisk command list the partition table and it looks like it should after  doing an install using the entire disk. That why I said windows is gone. Does the laptop boot to Ubuntu? 

Its kinda time to slow down and take a deep breath.  If you can't get the recovery disk to boot  then your looking at getting one from the manufacture or buying a windows install CD. 

You just have to decide where you want to go from here.

---

### Post by BigFatPapa on 2008-03-27
Louie,

It is an Acer laptop. I will look at all the documents and send for recovery disk.  

This started about 10 this morning and I got frantic.  My granddaughter is 10 and she LOVES computers, in fact she is the one who turned me on to ubuntu, I think she uses beryl (?).   

I have been playing around and am enjoying the format, lots to learn, but I love to learn.  My last job was in local goverment and they used linux so there is a lot that makes sense to me, but I only could go where the admins let us and basically it was email, gimp, tipix. 

Could you tell me how to access the wireless device?

I do not know how to give you a public thanks, but thank you for your help.

Tom

---

### Post by louieb on 2008-03-27
The only Acer I have at the moment is the wifes and it run VISTA. 
I'll see if I can get wireless working on it with the live CD. 
Try going to System>Administration>Network and check the roaming box. Thats the quick and easy way when it works. 
If not then I'm not much help. I guess I just been lucky that my laptops wireless connection have worked out of the box. So I've haven't played with it much.

---

### Post by BigFatPapa on 2008-03-27
I get that the driver is propritary  software source bcm43xx-fwcutter is not enabled.

Maybe I should put out another thread on this or try downloading the driver.

Thanks again louie
Tom

---

### Post by louieb on 2008-03-27
Try System>Adminstration>Restricted Driver Manager.

If that doesn't work that I think a new thread would be the way to go.
Good Lock.
Lou

---

### Post by BigFatPapa on 2008-03-27
That is where I headed and found the restriction.  

I see you are from Texas, my sister in law is from there and my Dad is a Texas snowbird. 
Texans are above us cheeseheads in friendliness. The Mrs and I are thinking off checking the Corpus Christi area to move, I am finishing a degree for my third career and want to get out of the snow. 

Thanks again Lou

Tom

---

### Post by rkd on 2008-03-29
If you want to try to use the recovery disk that you have, we probably can help you here.  It would save you time getting Windows back onto the computer because you wouldn't have to wait for a new recovery disk to arrive.

Realize that using the restore disk will put the computer back to the state it was in when you got it.  Anything you did later won't be there.  You probably know that, but I wanted to be sure you understood that.  Your granddaughter must have clicked through three or four screens and told it to use the whole disk for Ubuntu. The Ubuntu install then wrote Ubuntu stuff over the Windows stuff that was there, so anything you put on there before is gone.  

If, before the Ubuntu install happened, you had saved any files onto an external hard disk, USB Flash drive, writable CD, etc., you'll be able to restore that data after you get Windows back.

When you use the restore disk, as far as I know, it won't be possible to save the Ubuntu installation -- the restore disk will wipe out anything on the disk and restore the original setup.  So you should treat any of the work you do getting things to work with Ubuntu as stuff you'll have to do over again, so make notes about it so it will be easier to do the second time.  

Perhaps the restore routine is more flexible than I imagine, but it would be prudent to plan to have to redo all the Ubuntu setup.  You certainly could save Ubuntu files onto an external drive or a writable CD disc before doing the restore, but unless you copy *all* of the Ubuntu files (which will be a very large number of files and a lot of space), you couldn't restore the Ubuntu setup from what you saved, so you'd have to do most of the install and setup over again, anyway.

After you get Windows back, you can put Ubuntu onto the computer as dual boot, just like you did before your granddaughter made the error.  (At least it seems that in the first post you said you had successfully set up the dual boot; if you didn't actually do that, we can help you with that, too.)

So, if you want to get going on using the restore disk that you have, I imagine that you just  boot from the recovery disk and then make a selection from a menu or two about exactly what you want it to do.  Each manufacturer has their own recovery procedure and I don't know what Acer's is.  It probably is described in some printed material that came with the computer.  If not, or if you don't still have the stuff that came with the computer, we probably can find the directions online if you tell us the exact model of the computer.

So if you want help with restoring Windows, tell us what the directions say about how to use the recovery disk, and we'll interpret whatever isn't clear for you.  (Or tell us the model number of your computer and we'll try to find the directions online.)

---

