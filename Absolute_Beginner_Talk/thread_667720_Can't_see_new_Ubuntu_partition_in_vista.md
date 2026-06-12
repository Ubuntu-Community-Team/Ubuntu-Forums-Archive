---
title: "Can't see new Ubuntu partition in vista"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by thedon_1 on 2008-01-14
Ok, so i have a 250Gb HDD. I partitioned 30gb. I have Vista on the larger chunk.

I installed Ubuntu, and when it said what partition to install on, i selected the option that was something like guided-largest free space, something like that, it was the 3rd or 4th option.

Now when i go into Vista, i can't find the Ubuntu hard partition in My computer.

Is an ubuntu dual boot install ubuntu supposed to be used on a partition, but all files saved on the larger part and run from that?

If so, how can i reclaim some of that 30gb? Or was there a much better way for me to approcah this?

Any help is appreciated.

Thanks

---

### Post by jflaker on 2008-01-14
Micro$soft does not play well with Linux partition.  Window$ can not see Linux Partitions

You should be able to see the Windows partition from Linux though.

---

### Post by edd07 on 2008-01-14
You can't see Ubuntu or other Linux partitions by default on windows because it doesn't support the ext3 file system. You can install the ext file system, however, and its pretty easy.

Go to [http://www.fs-driver.org/]("http://www.fs-driver.org/") under Windows and download the installer. After its finished, run it UNDER COMPATIBILITY MODE FOR WINDOWS XP, it won't install correctly if you don't. Do this by right clicking it > Properties > Compatibility. To install it just complete the wizard, in which you'll have to choose a drive letter for the Ubuntu partition.

I think you have to reboot to see it, I'm not sure. I'm running this thing on my Vista and it runs flawlessly, giving me write and read access to the Ubuntu partition.

Note: If you hibernate Ubuntu and log into Vista, you won't be able to see the partition, you need to shut down properly because of the journaling feature of the ext3 file system.

Hope this helps, and good luck with Ubuntu

---

### Post by thedon_1 on 2008-01-14
Oh ok, thanks for explaining that guys.

So do you think it would be a good idea to just save all my files and stuff on the Vista partition, but use them in Ubuntu? Does it matter that it is NTFS?

If so, should i look to make my Ubuntu partition less than 30gb?

---

### Post by zipperback on 2008-01-14
> **thedon_1 said:**
> 
Now when i go into Vista, i can't find the Ubuntu hard partition in My computer.

Is an ubuntu dual boot install ubuntu supposed to be used on a partition, but all files saved on the larger part and run from that?




Windows uses a different filesystem and in general does not see the Linux partitions.

If you want more information dual booting see this link.

[http://ubuntuforums.org/showthread.php?t=642627#6](http://ubuntuforums.org/showthread.php?t=642627#6)

- zipperback
:popcorn:

---

### Post by edd07 on 2008-01-14
As far as I know, it isn't 100% safe to write to a NTFS partition from Ubuntu, since the software that does that isn't finished. I could be completely wrong, though, you should get a second opinion on that.

What I have is a somewhat big Windows partition (I could never resize it :-(), then a 10GB Ubuntu (root) partition and a huge /home partition (where all my files are) formatted as ext3 (default on Ubuntu), and I use the Ext2 IFS (the software I told you about) to access them from Vista. The good thing about this setup is that you can reinstall the operating systems without losing any of your files.

But I guess it depends on what OS you use more frequently.

---

### Post by thelatinist on 2008-01-14
> **edd07 said:**
> As far as I know, it isn't 100% safe to write to a NTFS partition from Ubuntu, since the software that does that isn't finished. I could be completely wrong, though, you should get a second opinion on that.

I'm pretty sure that ntfs-3g is now quite good at writing NTFS. I used it for several months to read and write to my shared data partition (before I dropped Windows altogether) without any issues.  I didn't try to write my Windows system partition, though...

---

### Post by stchman on 2008-01-14
> **thedon_1 said:**
> Ok, so i have a 250Gb HDD. I partitioned 30gb. I have Vista on the larger chunk.

I installed Ubuntu, and when it said what partition to install on, i selected the option that was something like guided-largest free space, something like that, it was the 3rd or 4th option.

Now when i go into Vista, i can't find the Ubuntu hard partition in My computer.

Is an ubuntu dual boot install ubuntu supposed to be used on a partition, but all files saved on the larger part and run from that?

If so, how can i reclaim some of that 30gb? Or was there a much better way for me to approcah this?

Any help is appreciated.

Thanks

That is because M$ does not know how to read EXT3 file systems.  There is a 3rd party program to read Linux filesystems.  On the other hand Linux can read/write to NTFS file systems.

---

### Post by stchman on 2008-01-14
> **edd07 said:**
> As far as I know, it isn't 100% safe to write to a NTFS partition from Ubuntu, since the software that does that isn't finished. I could be completely wrong, though, you should get a second opinion on that.

What I have is a somewhat big Windows partition (I could never resize it :-(), then a 10GB Ubuntu (root) partition and a huge /home partition (where all my files are) formatted as ext3 (default on Ubuntu), and I use the Ext2 IFS (the software I told you about) to access them from Vista. The good thing about this setup is that you can reinstall the operating systems without losing any of your files.

But I guess it depends on what OS you use more frequently.

Never had a problem writing to NTFS using ntfs-3g.

---

### Post by thedon_1 on 2008-01-15
OK, thanks guys.

I think making a new partition for my files seems like a really good idea.


I need to downsize my main partition a little, and then take some space out of the 30gb ubuntu partition.
Could you please suggest the best way to do this?  
Also, should i make it NTFS, or FAt 32 just to be safe?

---

### Post by hyper_ch on 2008-01-15
> **stchman said:**
> Never had a problem writing to NTFS using ntfs-3g.

But if you encoutner a problem you might as well lose all your data on ntfs.

---

### Post by thedon_1 on 2008-01-15
So ok, right now i have this

250GB - 3 partitions

200GB = Windows
30 GB = Ubuntu
1.5GB = I think swap file, it was created when Linux was installed

I'm thinking of having the following

20GB = Windows
20GB = Ubuntu
1.5GB = Swap file
200GB = Files (FAT 32 for safety)

can a 200 GB partition be formated to FAT 32?
How can i achieve this?

Thanks

---

### Post by hyper_ch on 2008-01-15
I think it can be (up to 2 TB I think)... but you cannot store file larger thatn 4gb on the fat32 partition.

---

### Post by ByteJuggler on 2008-01-15
> **edd07 said:**
> As far as I know, it isn't 100% safe to write to a NTFS partition

It's pretty much 99.9999% safe in 7.10 (Gutsy) , thanks to NTFS-3G.

Edit: Never mind, see the same comment has already been made.   Seriously, NTFS-3G is safe enough for general use now.  Can anyone doubting this point to a horror story caused by it in since Gutsy's release?  No?  Didn't think so.    Canonical/The Ubuntu project would not have included the NTFS-3G driver for general (active by default) use if it wasn't safe.

Of course, the other way to look at it, is you could potentially even lose all your data by using Windows...   I once had to recover a Windows box who's NTFS filesystem had somehow become corrupted, and in fact crashed Windows on bootup inside the NTFS.sys driver.  So, on Windows, you were stuck up crap creek without a paddle, since you couldn't use the NTFS driver as the broken filesystem somehow caused the driver to break...and everything that wants to access the filesystem *has* to go through the driver....!!!   I ended up actually rescuing this disk using Linux, which still managed to mount the filesystem.  I actually managed to recover the system to a bootable state as well with some jiggery pokery.  

So, anyway, the chances of you losing *all* your data on NTFS by access from Linux is virtually nil now, with NTFS-3G.  Obiously the chances of you possibly losing *some* data somewhere (particularly written to by Linux) is arguably marginally larger but, arguably still negligible.

---

### Post by thedon_1 on 2008-01-15
Ok that's good to hear that it's almost 100% safe. 

The 4GB limit would have made FAT 32 not a very good option.

I will make a new thread about how to partition the drive.

Thanks a lot for the replies, appreciate it

---

