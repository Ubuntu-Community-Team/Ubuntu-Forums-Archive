---
title: "Please help - hard disk or other error?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by sleepless_in_vancouver on 2008-04-08
Hello,

new ubuntu convert here.  I recently decided to upgrade my mom's laptop (Toshiba Satellite Pro 6000) with ubuntu.

To say it was a learning experience is understating it, but it was actually quite an interesting challenge and learning opportunity.  I had lots of trouble with getting the distributions, terminal use and nvidia drivers, but i was impressed by the help in the forum and on the www.  (Not that you care, but i'm not in IT, just a beginner that has an interest in technology and the ability to read FAQs.)

But now I got a new problem that I couldn't find the answer to.  I suspect my HD might have crashed or be failing to cause this problem - which occurred immediately after i spent 10 hours learning and installing ubuntu.  natch.

When i boot up the laptop now, it goes to the splash screen then halts and goes to an automatic "fsck" which then fails.

I manually fsck the disk and goes through the process and spits out reports along the vein of:
[212.920000] ata1.00: exception emask 0x0 SAct 0x0 Serr 0x) action 0x0
[230.16800000 gibberish
[230.1920000] buffer i/o error on device sda1, logical block 1343583 error reading block 134583 (attempt to read blcok from filesystem resulted in short read) while getting next inode from scan.  ignore error <y>

- i select "y" and force rewrite is presented, which i say "y" again

it goes through several permutations with different values but never seems to finish.

from my limited knowledge, i think ata1 is the HD?  

i'm wondering if the HD is gone?  or is there another way to proceed?

should i reformat the drive and reinstall? or is that futile?

any help or comments is greatly appreciated!

Thanks,

Ed

---

### Post by Soundman2 on 2008-04-08
You may indeed have a bad hard disk.  Here are several things you can do to diagnose it:

1. Boot to the Ubuntu Live CD.
2. Open a terminal (Applications->Accessories->Terminal)
3. Type: ```
fdisk -l
``` to show a list of drives on your system.  I expect you will only see one - the internal hard disk.  Note its name like /dev/sda or /dev/hda.  For the purposes of this discussion, I will assume your drive is /dev/sda.
4. Type: ```
sudo apt-get install smartmontools
```
5. Now, read the hard disk's diagnostic data: ```
sudo smartctl -a /dev/sda
```.
Read through the results and look for signs of trouble.  If it doesn't make sense, google for smartctl or post your results here.  Also, smartctl allows you to command the drive to do a self-test.  There is a short and long version that takes 2 minutes or over an hour.  After the test, smartctl -a /dev/sda will show the most recent test results.

I have found that, sometimes, the smart data will indicate that the drive is OK even though it is really bad.  Therefore, if the smart data and self-tests run OK, then proceed to test further....
6. Try to read all the data off the block device.  A convenient command called "badblocks" will do this. Type into the terminal window:
```
sudo badblocks -s /dev/sda
```
This command will only read from the disk, so it is not destructive.  The -s option tells it to report progress as it goes.  If you start seeing errors, then your disk is probably bad.  (NOTE: I'm not sure whether the sudo is necessary for this command when booted from a live CD. It would be under a normal boot).

Now, some hard disks fail in such a way that you can read their current contents, but writing to them makes them hang or otherwise fail.  You can test the whole disk with a variation of the badkblocks command.  This will read a few blocks, write a test pattern to it, read it back to ensure that it is correct, then write the original data to it.  This makes it *theoretically* non-destructive.  However, if your disk is failing, it may cause further damage to its filesystem because it could be unable to replace the original data.  So, assume this command may destroy all the data on every partition of the disk (even though it attempts not to):
```
sudo badblocks -s -n /dev/sda
```

If it gets through that without a hitch, I would say that your drive it OK.  Your data may have gotten corrupted by some transient error.  Since fsck does not seem to be able to solve it, you probably need to start over.  You may be able to mount the filesystem readonly first and copy any desired files off of it:  Here are some commands to do this, assuming the drive had 3 partitions, which is pretty typical for a Ubuntu install.  Adjust this up or down according to the partitions listed in the "fdisk -l" command above.
```
mkdir /mnt/1 /mnt/2 /mnt/3
sudo mount -o ro /dev/sda1 /mnt/1
sudo mount -o ro /dev/sda1 /mnt/2
sudo mount -o ro /dev/sda1 /mnt/3

```

Copy data off from the mountpoints under /mnt that you created above.

Hope this helps,
Soundman2

---

### Post by sleepless_in_vancouver on 2008-04-09
Thanks soundman2!

i'm going to try that tonight and see if i can get it to work.  

Cheers,

Ed

---

