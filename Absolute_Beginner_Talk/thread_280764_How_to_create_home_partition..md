---
title: "How to create /home partition."
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by yman on 2006-10-20
I recently reinstalled Dapper and decided to create a partition for /home directory. All went well, but then I noticed that I really have two /home directories: 1 on the main partition where the root directory is, and 1 on the /home directory.

My questions:
[list=0]
[*]How do I do it correctly right from the begining?
[*]How do I create a /home partition now the system is installed?
[*]How do I correct the faulty situation in which all my data is saved twice?
[/list]

This is especialy important because I have a tiny HD (6.5 GB) and my system got stuck right after installing and running Audacity, which I assume has to do with having very little space on the / partition.

---

### Post by aysiu on 2006-10-20
I don't know what you mean about having two /home directories, but this can help you make a separate /home partition: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by confused57 on 2006-10-20
aysiu beat me to it...

---

### Post by Dr. Nick on 2006-10-20
on the reinstall did you erase your partitions? You may still have a /home that was on the root from an old install and then made a seperate partition on a recent install. The easiest fix may be a reinstall while formatting every partition. But you could probably fix it somehow and perserve the data

To fix it would require a few more partition specifics though

---

### Post by yman on 2006-10-20
Thanks, but it says there that It's for people who don't have a /home partition.

---

### Post by Dr. Nick on 2006-10-20
> **confused57 said:**
> Maybe this link can help:
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

Haha, that page is priceless. thanks for the good writeups aysiu

Its linked two times here, and I linked it in another thread just before viewing this one

---

### Post by yman on 2006-10-20
> **Dr. Nick said:**
> on the reinstall did you erase your partitions? You may still have a /home that was on the root from an old install and then made a seperate partition on a recent install. The easiest fix may be a reinstall while formatting every partition. But you could probably fix it somehow and perserve the data

To fix it would require a few more partition specifics though

I completely earased the HD when I reinstalled. I did it after a problem that accured while trying to resize partitions, the problem  was that ubuntu thought I hade a 100% full HD, even though it was far from it.

ubuntu treats both /home directories as /home. whatever is written to one is written to the other.

the /home partition is about 3.3 GB, the / is about 2.5 and then there is swap which is probably 6 or 7 GB.

---

### Post by wieman01 on 2006-10-20
> **yman said:**
> Thanks, but it says there that It's for people who don't have a /home partition.
Yes, that's true. But you simply have to skip the steps on **"creating a /home partition"**, then continue with **"editing /etc/fstab"**. That should do.

Once you have done that, you can delete **"/home"** on **"root"**. It's as simple as that. Just a bit of common sense, that's all. Post your **"/etc/fstab"** if you have problems.

---

### Post by wieman01 on 2006-10-20
> **yman said:**
> Ubuntu treats both /home directories as /home. whatever is written to one is written to the other.
This I find hard to believe... Is that really the case?

---

### Post by yman on 2006-10-20
> **wieman01 said:**
> This I find hard to believe... Is that really the case?

it very well seems so, since whenever I add stuff to the home, both partitions loose free space.

I can't really do anything on ubuntu, because all I can do is look at the clock and move the mouse pointer. if I try clicking, nothing happens. I'm hoping for a solution that doesn't require reinstalling. I'll see if I can do what the guide said.

but heres the problem: if I reinstall, I lose because I want to use linux without using primitive solutions like in windows. however, if I reinstall, I have no chance of loosing data.

if I go with such solutions, I win cause I did something the good/hackish way, but I may loose important data. I can't see myself doing it either, because ubuntu is not working properly as stated above, but I really want to do it this way.

---

### Post by wieman01 on 2006-10-20
The problem is the 2 /home partitions. I had a similar problem once after messing around with "fstab". 
 
Therefore you need to make the necessary changes in "fstab" first so that /home points to the other partition. Then you have to remove /home on "root". 

Do you know how to do that? Can you pull backups somehow? And how about entering the "recovery mode"? You need to enter the command line, the GUI won't help you in your case.

---

### Post by wieman01 on 2006-10-20
One more note: The best way to remove home is by moving it to another location (AFTER making the necessary changes in "fstab"!):
> cd /
> sudo mv /home /opt/
This command move your home folder to /opt.

---

### Post by yman on 2006-10-20
> **wieman01 said:**
> The problem is the 2 /home partitions. I had a similar problem once after messing around with "fstab". 
 
Therefore you need to make the necessary changes in "fstab" first so that /home points to the other partition. Then you have to remove /home on "root". 

Do you know how to do that? Can you pull backups somehow? And how about entering the "recovery mode"? You need to enter the command line, the GUI won't help you in your case.

how do I enter recovery mode? is changing fstab covered in that guide?

can I copy to a removeable device (old 256 MB MP3 player) from recovery mode?

in some aspects such as this I'm a complete newbe. I am familiar enough with the command line to follow orders, and I feel comfertable enough to do any experiments (this isn't my second install of ubuntu, more like the forth. I ruined it plenty of times while messing around).

---

### Post by aysiu on 2006-10-20
If you're more comfortable in the GUI than the command-line, I'd use a live CD instead of recovery mode.

---

### Post by yman on 2006-10-20
> **aysiu said:**
> If you're more comfortable in the GUI than the command-line, I'd use a live CD instead of recovery mode.

but I tried using a liveCD previously for other things, and it wouldn't mount the hard drive. (or open it. whatever it's called).

I like using the command line, I'm just not that familiar with it.

---

### Post by wieman01 on 2006-10-20
Ok, I need to hop off line. But I think Aysiu will be around for a while, right?

The process is:
1. Boot from Live CD
2. Mount root
3. Edit /etc/fstab to reflect the changes
4. Delete /home on root
5. Reboot

To mount root in the first place, do this (terminal windows - Live CD):
> sudo mount /dev/hda**[COLOR="Red"]x[/COLOR]** /mnt
**[COLOR="Red"]x[/COLOR]** stands for your root partition number.

---

### Post by yman on 2006-10-20
> **wieman01 said:**
> Ok, I need to hop off line. But I think Aysiu will be around for a while, right?

The process is:
1. Boot from Live CD
2. Mount root
3. Edit /etc/fstab to reflect the changes
4. Delete /home on root
5. Reboot

To mount root in the first place, do this (terminal windows - Live CD):

**[COLOR="Red"]x[/COLOR]** stands for your root partition number.

I mounted hda1 (root) & hda3 (/home). when I do
```
cd /home
ls
```
then I get
```
ubuntu
```
which means I'm looking in the liveCD. in order to backup /home and edit fstab I need to be on the HD. how do I do that?

can someone please make sense out of this for me? (it's from the manual you gave me):
> 
**[SIZE="2"]Using the new partition[/SIZE]**
Now, back in the terminal, I'm going to mount /dev/hda1 and /dev/hda7:
[COLOR="SeaGreen"]sudo mkdir /old
sudo mount -t ext3 /dev/hda1 /old
sudo mkdir /new
sudo mount -t ext3 /dev/hda7 /new[/COLOR]

Now we're going to back up the /home directory on the old partition and move it to the new partition:
[COLOR="SeaGreen"]cd /old/home
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
sudo mv /old/home /old/home_backup
sudo mkdir /old/home[/COLOR]

Yes, one of those lines looks really complicated--please type it as is--or, if you're unsure of your typing skills, copy and paste it into the terminal. Believe me--the command is necessary.

Next, we're going to specify to use the new home partition as /home:
[COLOR="SeaGreen"]sudo cp /old/etc/fstab /old/etc/fstab_backup
sudo nano /old/etc/fstab[/COLOR]

You'll then be taken to the nano text editor. Add in this line:
[COLOR="SeaGreen"]/dev/hda7 /home ext3 nodev,nosuid 0 2[/COLOR]

Then save (Control-X), confirm (Y), and exit (Enter)

After you reboot, you should be now using your new /home partition. 

---

### Post by wieman01 on 2006-10-20
Mount root:
> sudo mount /dev/**[COLOR="Red"]hda1[/COLOR]** /mnt
Then change directory to "/home" on "root":
> cd /mnt/home/
The copy your user's home folder to where you want to have it e.g. /mnt/opt/

---

### Post by yman on 2006-10-20
OK, Successfully mounted hda1 & hda3. now I want to back up hda3 unto an MP3 player but I don't have permissions. I tried chmod (I remmebered it from PHP) and it works great, except I have no idea how to make it do all sub-directories so it's apain in the neck. so: how do I change permissions for a directory and all it's sub-directories, or: how do I access my MP3 player from the command line.

---

### Post by aysiu on 2006-10-20
You need the *-r* option: ```
sudo chmod -r 755 /path/to/directory
```

---

### Post by yman on 2006-10-20
> **aysiu said:**
> You need the *-r* option: ```
sudo chmod -r 755 /path/to/directory
```

it gives me:
```
cannot access '755': no such file or directory
```

---

### Post by aysiu on 2006-10-20
I don't know if this makes a difference, but I think I gave you the wrong instructions. I think the *r* has to be capital: ```
sudo chmod -R 755 /path/to/directory
```

---

### Post by yman on 2006-10-20
> **aysiu said:**
> I don't know if this makes a difference, but I think I gave you the wrong instructions. I think the *r* has to be capital: ```
sudo chmod -R 755 /path/to/directory
```

Worked!

thank you alot!

now how do I tell it hda3 is /home?

---

### Post by aysiu on 2006-10-20
Shouldn't that be in your /etc/fstab?

---

### Post by yman on 2006-10-20
> **aysiu said:**
> Shouldn't that be in your /etc/fstab?

thats what wieman01 said, but how do I edit it? and what if it's fine and I shouldn't, how would I know? and what changes do I make?

---

### Post by aysiu on 2006-10-20
Doing this without a live CD is going to be tough.

Can you try the live CD and this tutorial I linked to earlier?
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by yman on 2006-10-20
> **aysiu said:**
> Doing this without a live CD is going to be tough.

Can you try the live CD and this tutorial I linked to earlier?
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I am using I liveCD. didn't I mention my system is totaly stuck and I can't do a thing?

do I just do this:
```
Next, we're going to specify to use the new home partition as /home:
sudo cp /old/etc/fstab /old/etc/fstab_backup
sudo nano /old/etc/fstab

You'll then be taken to the nano text editor. Add in this line:
/dev/hda7 /home ext3 nodev,nosuid 0 2 
```

---

### Post by aysiu on 2006-10-20
Yes, assuming that you have mounted your / partition to /old and that you change /dev/hda7 to /dev/hda3 (since that's what you want to be your /home)

---

### Post by wieman01 on 2006-10-20
You may have resolved your problem already as I see in the previous posts, but this will be what you have to do:

1. First of all... Boot from Live CD as before, then mount "hda1" (root):
> sudo  mount /dev/[COLOR="Red"]hda1[/COLOR] /mnt
2. Then open "fstab":
> sudo gedit [COLOR="Red"]/mnt[/COLOR]/etc/fstab
3. Add this line:
> /dev/hda3       /home           ext3    defaults        0       2
4. Now you can reboot.

This should resolve all your problems.

---

### Post by wieman01 on 2006-10-20
_**And one more thing:**_ Please make sure that there is only 1 line in "fstab" referring to /home. Delete all the others.

---

### Post by yman on 2006-10-21
thank you very much!

I haven't really got around yet to applying this, I'm still in the middle of backing up.

I said earlier that when I added to hda3 it added to hda1: well heres the weird thing, when I mounted hda1 and looked at /home it was emptey, so I really don't understand where all the extra data on hda1 came from. I only installed programs after I noticed this weird behavior. I also don't know why it tells me when I mount hda1 that it's 100% full even though when I look at it, the files is can read take only 2 GB out of a total of 2.4 GB.

---

### Post by yman on 2006-10-22
after going through all the trouble, I forgot to set the permitions on my home folder back to 644, and it all got blown. to top it all, I'm starting to think there wasn't any problem to begin with. to go through all this trouble for nothing...

this tierd me out, so I decided that now that I know how to do it, I can reinstall. I'll try to use a tip I just got to get my 3COM PC card working so I can finally fully enjoy Ubuntu, rather than struggle to learn how to do things the hard way.

thank you very much! you've been great help! I learned a lot, even if for the wrong reason, and thats great.

---

### Post by aum11 on 2006-12-13
I just tried the instructions and it failed. 

Message is , on rebooting, "Your home directory is listed as:
'/home/priya'
but does not appear to exist....

Is there a problem with using hdc1 and hdc6, as my equivalents for hda1 and hda7?  I cannot see what else could be the problem.

Thanks.

PS the recovery method mentioned in the howto also did not work.

---

### Post by wieman01 on 2006-12-13
Try only "/home" rather than "/home/priya". That should do.

---

### Post by aum11 on 2006-12-13
Thanks Wieman01. 

This message appears when I am logging on.  What command do I use to change the system to look for /home and not /home/priya as my home directory?

---

### Post by wieman01 on 2006-12-13
Where exactly does this error message appear? Does the graphical log-on screen load (GDM)?

---

### Post by aum11 on 2006-12-13
Yes, it appears just after entering user and password.

---

### Post by wieman01 on 2006-12-13
Can you briefly tell us what you have done recently? Could it be that the disk is full? Or have you made any changes in "fstab"?

---

### Post by aum11 on 2006-12-13
Yes, as mentioned earlier I followed the guidelines for creating a /home partition and copying the contents across from /root partition.

---

### Post by wieman01 on 2006-12-13
Alright... Have you got a Live CD on hand? You probably need to update "fstab"...

When you have booted, please try to switch to the terminal by pressing (ALT + F1). Then enter you username and password. Check "fstab" and see if there is an entry for "/home":
> cat /etc/fstab
Is the device name/number for your home-partition correct?

_**EDIT:**_
By the way... what is the "device name" of your future "/home" partition? "hdc1"?

---

### Post by aum11 on 2006-12-13
Thanks for Your help.

Root and swap are okay, but what should be hdc6 and /home, is showing up as hda and priya.

How to change this please?

---

### Post by wieman01 on 2006-12-13
To change this you can use "vi" text editor:
> sudo vi /etc/fstab
Then press "insert" to change the contents. Once you have changed the corresponding lines (please be very careful!), press "esc" and then "shift + zz" to save & exit. Here is a guide on "vi" if you need it:

[http://www.cs.rit.edu/~cslab/vi.html]("http://www.cs.rit.edu/~cslab/vi.html")

Post "fstab" if you need help.

---

### Post by aum11 on 2006-12-13
cannot get live cd to help because this machine has only 256meg and it cannot manage file editing.

However can run in terminal mode.

What /etc/fstab shows is (roughly transposed):


proc             /proc           proc     gefaults        0        0
# /dev/hdc1
UUID=laa08ia8-70al-4fe9-9f93-3e2a21ea1a8d /                 ext3
defaults,errors=remount-ro 0     1
# /dev/hdc5
UUID=5c9b1675-c482-492c-836b-d39698352b13 none              swap
sw        0      0
/dev/hda         /media/cdrom0   udf,iso9660 user,noauto      0       0  



Any suggestions?

I see no mention of /dev/hdc6 which is supposed to be /home partition.
Gparted shows hdc6 does have the data copied into it.

---

### Post by wieman01 on 2006-12-13
Well, your home partition is missing, no surprise you have a problem. Assuming that /home resides on "hdc6", you need to add this:
> /dev/**[COLOR="Red"]hdc6[/COLOR]**       /home           ext3    defaults        0       2
Then restart the computer.

Out of curiousity, what is the '#' key for? The '#' would basically disable the mounting of "/dev/hdc1" & "/dev/hdc5"... Is that what you want? I think something else might be wrong. How many harddisks have you got in your PC?

---

### Post by aum11 on 2006-12-13
Yes thanks that fixed it.

---

