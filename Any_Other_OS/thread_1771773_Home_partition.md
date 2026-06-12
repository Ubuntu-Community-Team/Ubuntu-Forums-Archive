---
title: "Home partition"
date: 2011-05-30
forum: Any Other OS
---

### Post by rigel4 on 2011-05-30
Please help me out. I have took the plunge and ported out to Fedora 15, basically becasue Gnome 3 is there by default, and it marginally suits my needs better than Unity. I have taken the decision to do it now rather than later as the next release of Ubuntu will not include the any form of classic gnome. Therefore i will be forced to go with Gome 3 or Unity.

I need help with the following. I had my partions as such that i had the os on one partition and my home folder on another. I have Installed Fedora over the top of Ubuntu and at it boots nicely to the desktop.
My home partition is still there if a browse to it, but i would like some help in pointing the Ferdora directories
to my old Ubuntu home directory .

Thank you

---

### Post by rigel4 on 2011-05-30
anyone?

---

### Post by Hedgehog1 on 2011-05-30
I am burning a Fedora 15 CD right now, and will be installing it as one of my two 'test' installs (the other is the new very-earlier-not-yet-alpha 11.10 Ubuntu). So I will have a matching install before too long.

Until then, if you would post the contents of you /etc/fstab (**F**ile **S**ystem **TAB**le) file.

In the Terminal please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -lu
```

and post the output of it as well.

**The Hedge**

:KS

p.s. Rigel 4 - From Star Trek, Right?

---

### Post by rigel4 on 2011-05-30
> **Hedgehog1 said:**
> I am burning a Fedora 15 CD right now, and will be installing it as one of my two 'test' installs (the other is the new very-earlier-not-yet-alpha 11.10 Ubuntu). So I will have a matching install before too long.

Until then, if you would post the contents of you /etc/fstab (**F**ile **S**ystem **TAB**le) file.

In the Terminal please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -lu
```and post the output of it as well.

**The Hedge**

:KS

p.s. Rigel 4 - From Star Trek, Right?

Hey 

Thanks for posting back , this is a weebit out of my comfort zone and want to avoid a full reinstall if at all possible.
Yes, Rigel4 is indeed from Star Trek, the bestest ever series.

Here is the info you ask for.


> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000454ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   193359871    96678912   83  Linux
/dev/sda2       193361918  1953523711   880080897    5  Extended
/dev/sda5      1940946944  1953523711     6288384   82  Linux swap / Solaris
/dev/sda6       193361920  1940944895   873791488   83  Linux

Partition table entries are not in disk order


---

### Post by Hedgehog1 on 2011-05-30
We will also need the contents of your **/etc/fstab** file, please.

This is the file we will change to use the '/home' partion instead of the 'home' directoy in the '/' partition.

Here is an example of what we are going to change in your fstab file:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=204630d2-70c9-4b79-941c-20162dfa457f /           ext4    errors=remount-ro 0       1
[B][COLOR="Red"]# /home was on /dev/sda6 during installation
UUID=4aebc2c6-5984-47e3-b2ea-7fdfaf23343e /home       ext4    defaults        0       2[/COLOR][/B]
# swap was on /dev/sda5 during installation
UUID=cb0c7226-150e-45ca-ba5c-2e161dc10f6a none        swap    sw              0       0
```

Don't copy this exactly - your UUIDs for your partitions will be different.

---

### Post by rigel4 on 2011-05-30
> **Hedgehog1 said:**
> We will also need the contents of your **/etc/fstab** file, please.

This is the file we will change to use the '/home' partion instead of the 'home' directoy in the '/' partition.


I am sorry to keep you waiting , but i can't find etc/fstab in the etc folder!

---

### Post by Hedgehog1 on 2011-05-30
OK - That is where it ii placed for an Ubuntu install.  It may not be located there for a fedora install.

I think I need to install my test install of fedora and see where it actually goes.

This may take a bit.

***The Hedge***

:KS

---

### Post by rigel4 on 2011-05-30
Phew found it 




#
# /etc/fstab
# Created by anaconda on Mon May 30 21:11:49 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=19726af5-abaa-49b3-9914-bafa4667e6ef /                       ext4    defaults        1 1
UUID=0e660a7a-de9f-4fff-aa57-789351e5dfa7 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

---

### Post by Hedgehog1 on 2011-05-30
I just checked to documentation for Fedora, and that is the location for the file.

please try this to see it:

```
gksudo gedit /etc/fstab
```

---

### Post by Hedgehog1 on 2011-05-30
OK - we are almost there then.

Now do this to get the UUID of your partitions:

```
sudo blkid -o value -s UUID
```

---

### Post by rigel4 on 2011-05-30
Hedgy i really appreciate your help with this, as it looks a bit more complex than i bargained for.

But very educational.

[QUOTE[alex@U-BOX ~]$ sudo blkid -o value -s UUID
[sudo] password for alex: 
19726af5-abaa-49b3-9914-bafa4667e6ef
0e660a7a-de9f-4fff-aa57-789351e5dfa7
3efc8c6e-5b5b-44ab-b5c8-5a0711542b7a
][/QUOTE]

---

### Post by Hedgehog1 on 2011-05-30
So, here is the key part of your fstab file now:

```
UUID=19726af5-abaa-49b3-9914-bafa4667e6ef / ext4 defaults 1 1
UUID=0e660a7a-de9f-4fff-aa57-789351e5dfa7 swap swap defaults 0 0
```

And here are your UUIDs:

```
19726af5-abaa-49b3-9914-bafa4667e6ef
0e660a7a-de9f-4fff-aa57-789351e5dfa7
**[COLOR="Red"]3efc8c6e-5b5b-44ab-b5c8-5a0711542b7a[/COLOR]**
```

Two we already have ('/' or root and swap), so the last one ons is '/home'

```
UUID=19726af5-abaa-49b3-9914-bafa4667e6ef / ext4 defaults 1 1
**[COLOR="Red"]UUID=3efc8c6e-5b5b-44ab-b5c8-5a0711542b7a /home ext4 defaults 0 2[/COLOR]**
UUID=0e660a7a-de9f-4fff-aa57-789351e5dfa7 swap swap defaults 0 0
```

Use this command to add update the file:

```
gksudo gedit /etc/fstab
```

Also, if this line gives you any trouble, you can comment it out with the '#':

```
UUID=19726af5-abaa-49b3-9914-bafa4667e6ef / ext4 defaults 1 1
**[COLOR="Red"]#[/COLOR]**UUID=3efc8c6e-5b5b-44ab-b5c8-5a0711542b7a /home ext4 defaults 0 2
UUID=0e660a7a-de9f-4fff-aa57-789351e5dfa7 swap swap defaults 0 0
```

---

### Post by rigel4 on 2011-05-30
Hedgy i added the line, but nothing has changed , do i need to reboot?

---

### Post by Hedgehog1 on 2011-05-30
Sorry - I keep forgetting not everyone is a nerd (yet).

Yes, please reboot.  When you do, your real '/home' directory will be ignored (please don't delete it), and instead the '/home' partition will be used instead.

The only other step you may need to do is if the internal value for the first user is different from Ubuntu and Fedora (Ubuntu starts at 1000).

If that is the case, we will need to 'change owner' using: chown.

---

### Post by rigel4 on 2011-05-30
I rebooted and now i can't login
[FONT=monospace]
It says  "could not update    [/FONT][FONT=monospace]ICE[/FONT][FONT=monospace]authority file /home/alex/.ICEauthority[/FONT]
[FONT=monospace]
was me likely, but any advice would be appreciated.
[/FONT]

---

### Post by Hedgehog1 on 2011-05-30
Yikes.

We better but that '#' in front of that new line.

Please boot off of any LiveCD/LiveUSB you have (Ubuntu or Fedora) and get to the terminal.

Then do this:

```
sudo mount /dev/sd**a1** /mnt
```

```
gksudo gedit /mnt/etc/fstab
```

Put a '#' in front of that line for now, save and exit.

Then you can reboot.

Looks like you will need to do a **chown** on the data in that partiton before you change the fstab.

---

### Post by rigel4 on 2011-05-30
> **Hedgehog1 said:**
> Yikes.

We better but that '#' in front of that new line.

Please boot off of any LiveCD/LiveUSB you have (Ubuntu or Fedora) and get to the terminal.

Then do this:

```
sudo mount /dev/sd**a1** /mnt
``````
gksudo gedit /mnt/etc/fstab
```Put a '#' in front of that line for now, save and exit.

Then you can reboot.

Looks like you will need to do a **chown** on the data in that partiton before you change the fstab.


I'm doing that now Hedgy, you are a credit to the community, and i can only hope to know a fraction of what you do.[FONT=monospace][/FONT]

Thank you so very much for some expert support.

Rigel4

---

### Post by Hedgehog1 on 2011-05-30
Once you are booted up in Fedora from your hard disk, please do these two steps to change the ownership of all the files in the '/home' partition to you new user value in fedora.

This assumes your user is: **alex**

```
sudo mount /dev/sda6 /mnt
```

```
sudo chown -R **alex** /mnt/home/**alex**
```

With these files assigned the new internal value from fedora for your user, you can change the fstab file and reboot again.

p.s. Did you change your user name by any chance?  If you were '**alexanderthegreat**' before, and '**alex**' now, then we also need to change the name of your home directory from **/mnt/home/alexanderthegreat** to **/mnt/home/alex** :D

---

### Post by rigel4 on 2011-05-30
No ,they are both alex, i need to get out more. :):popcorn:

but on this occasion it's less work .

---

### Post by rigel4 on 2011-05-30
Hedgy I have a new problem, i can t see the old home directory anymore, according to the disk utility though
it is still there, but not in the file system , it just shows the new home dir.

the command you gave said no such file or directory.
So it is still there, but not showing.

I am so sorry to be a pain.

---

### Post by Hedgehog1 on 2011-05-30
OK - this is normal.

The command that mounts the '/home' partition in place of the '/home' directory does this.

SOOOO...

If you need to get your documents copied from the '/home' directory, you will need to:

Change fstab, reboot.

This will make '/home' in the root directory be the real one for now.

Then copy your documents from there to a safe place, or right into your '/home' partition by mounting it.

Then, once you have copied your documents, you can change fstab again and reboot.  See how handy that '#' is? It lets you toggle between the two /home's.

---

### Post by Hedgehog1 on 2011-05-30
By they way, I will be curious after you use Gnome Shell 3 in Fedora after a while if you think it is faster to use than Unity.

I find Gnome Shell 3 more intuitive, but Unity faster to use (less mouse movement between windows).

I would be interested to hear your observations after you use it for a bit.

---

### Post by rigel4 on 2011-05-30
you're  a wiz, I'll get on it now, but might need to leave it untill tomorrow evening. I am in the UK and have work tomorrow. Windows IT Guy lol. Soon to leave though for a job in development with electrical automation software. 

Thanks again hedgy. :KS:KS

---

### Post by rigel4 on 2011-05-30
> **Hedgehog1 said:**
> By they way, I will be curious after you use Gnome Shell 3 in Fedora after a while if you think it is faster to use than Unity.

I find Gnome Shell 3 more intuitive, but Unity faster to use (less mouse movement between windows).

I would be interested to hear your observations after you use it for a bit.

I will be sure to let you know, Unity may make a come back for me, but at the moment i just cant take to it.
I have always loved Gnome :D

---

### Post by Hedgehog1 on 2011-05-30
No problem.  See you if you need more help, umm, Whenever!

---

### Post by rigel4 on 2011-05-31
Hedgy
If your around , I am going round in circles. No access to my files, I would just reinstall if ican copy of my stuff. 118gb. but i can't even achieve that.

Stumped

I'm sure it all makes sense to you.:D

---

### Post by Morbius1 on 2011-05-31
Please post the output of the following commands:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
``````
mount
```For the benefit of the weekday crew please restate your requirements. You actually want to use your Ubuntu home partition in Fedora? Or do you want to copy over or link to or bind to the contents of the Ubuntu subdirectories ( Documents, pictures, etc ) over to Fedora?

Your username even if it is the same on both systems is not the same to each OS since your uid's are different. If you used the old home partition in Fedora I'm surprised you can boot into it..

---

### Post by rigel4 on 2011-05-31
It's worse now...
I opted to reinstall Ubuntu , using the do not format the home partition, and mounted it 
\home.
I have now logged into my new ubuntu install , and cant find my data ..
No ones fault but my own if its gone, but the original partition is still there.

> /dev/sda1: UUID="01c7146c-0754-4d0e-8729-1b40822febed" TYPE="ext4" 
/dev/sda3: UUID="80a4018d-4282-4327-baa7-a8f7c3febb93" TYPE="ext4" 
/dev/sda5: UUID="0e660a7a-de9f-4fff-aa57-789351e5dfa7" TYPE="swap"

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=01c7146c-0754-4d0e-8729-1b40822febed /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=80a4018d-4282-4327-baa7-a8f7c3febb93 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=0e660a7a-de9f-4fff-aa57-789351e5dfa7 none            swap    sw              0       0


> alex@U-BOX:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda3 on /home type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/alex/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alex)


Thank you for trying to help the ignorant :p

---

### Post by rigel4 on 2011-05-31
For those you just logging into this here is what i was originally trying to do

I wanted to use Gnome3 so i decided to install F15
I had Home partition on my hard drive that i wanted to use with F15
I couldn’t get it sorted out.

So now I reinstalled with \ubuntu choosing not to format the \home directory and mounting it \home.
I have logged into my desktop but can't find my data.. It could be lost.

So a warning to all, when messing with partitions, know exactly what your doing or wait for help.

Thank you

---

### Post by rigel4 on 2011-05-31
can anyone help me find out if my data is gone , so that i can move on and reinstall what data i have backed up.
Please.

---

### Post by rigel4 on 2011-05-31
I ran Gparted and it reported that there was over 16 gig of used space on my home partition,
but i cant see the data.

Any thoughts

---

### Post by Morbius1 on 2011-05-31
Post the output of :
```
ls -l /home/alex
```

---

### Post by Morbius1 on 2011-05-31
It's hard to follow this thread because you really should have run "sudo blkid -c /dev/null" from the beginning but I think we may have a problem.

The original uuid's of your partitions:
> **19726af5-abaa-49b3-9914-bafa4667e6ef**
0e660a7a-de9f-4fff-aa57-789351e5dfa7
[COLOR=Black]**3efc8c6e-5b5b-44ab-b5c8-5a0711542b7a**[/COLOR]Now it's this:
> /dev/sda1: UUID="**01c7146c-0754-4d0e-8729-1b40822febed**" TYPE="ext4" 
/dev/sda3: UUID="**80a4018d-4282-4327-baa7-a8f7c3febb93**" TYPE="ext4" 
/dev/sda5: UUID="0e660a7a-de9f-4fff-aa57-789351e5dfa7" TYPE="swap"                      It looks like sda1 (/) and sda3 (/home) are different. UUID's change when you reformat the partition so sda1 makes sense but sda3 should not have changed.

Run the "ls -l /home/alex" anyway since it doesn't explain why there is so much space being used.

---

### Post by Hedgehog1 on 2011-05-31
Greetings **Morbius1**!

Greetings **rigel4** (who cannot be left unattended! :D :D ).

Morbius1's observation of the new UUID's mean large changes were done to the Partitions is very correct.  The 16 gigs used when you had 118 gigs of data means that most of your data was lost (and likely all the data).

Please follow **Morbius1** request for a ```
ls -l /home/alex
```Right now that data will answer a few questions.

***The 'how did I get dragged into a Fedora install again?' Hedge***

:KS

---

### Post by rigel4 on 2011-06-01
> **Hedgehog1 said:**
> Greetings **Morbius1**!

Greetings **rigel4** (who cannot be left unattended! :D :D ).

Morbius1's observation of the new UUID's mean large changes were done to the Partitions is very correct.  The 16 gigs used when you had 118 gigs of data means that most of your data was lost (and likely all the data).

Please follow **Morbius1** request for a ```
ls -l /home/alex
```Right now that data will answer a few questions.

***The 'how did I get dragged into a Fedora install again?' Hedge***

:KS


Thank you all for your great support.
I have Reinstalled Ubuntu and will make do with "Unity" for now.
I would love to use Gnome 3, but I will need to wait until Ubuntu is ready for it.
This was the main reason that i was trying to port out to F15.

A special thank you to Hedghog1 for being such a great community member.

I have restored everything from back up other than my Installed programs and utilities.

Ps: I am such a noob :D

Peace.
Rigel4

---

### Post by Morbius1 on 2011-06-01
> Ps: I am such a noob :grin:In your defense you had the right idea to begin with:
> My home partition is still there if a browse to it, but i would like some help in pointing the Ferdora directories
to my old Ubuntu home directory .
Pointing the fedora subdirectories to the old Ubuntu subdirectories is completely different than the path you followed here. Here you attempted to make the Fedora home directory the old Ubuntu home partition. 

I set up a data partition at /mnt/Data. In that partition I create all the major subdirectories of a typical home directory ( i.e., Documents, Downloads, Music, Pictures, ... )

When I install a new OS I don't create a separate home partition. I allow it to create a home directory within / instead. After the install I "bind" the Documents folder in /mnt/Data to the Documents folder in home using a very simple command:
```
mount --bind /mnt/Data/Documents /home/morbius/Documents
```You can run that command as sudo, you can place it in /etc/rc.local, or if you really want to get fancy you can set it up as an upstart job ( which is the most full-proof way IMO ). When I save something to /home/morbius/Documents it's really going to /mnt/Data/Documents. OS's will come and go but /mnt/Data remains. You might have to change ownership if the new OS is not in the same family of Linux so that the uid's match the new system. You could have done the same thing by mounting your old Ubuntu home partition as ... I don't know .... /mnt/Uhome.

A separate home partition is a very overrated option. It does contain all of your data but it also contains all of your configuration files. Those files will either interfere with the new os or be completely incompatible with it depending on what OS your installing.

Just my opinion ;)

---

### Post by rigel4 on 2011-06-01
> **Morbius1 said:**
> In your defense you had the right idea to begin with:
Pointing the fedora subdirectories to the old Ubuntu subdirectories is completely different than the path you followed here. Here you attempted to make the Fedora home directory the old Ubuntu home partition. 

I set up a data partition at /mnt/Data. In that partition I create all the major subdirectories of a typical home directory ( i.e., Documents, Downloads, Music, Pictures, ... )

When I install a new OS I don't create a separate home partition. I allow it to create a home directory within / instead. After the install I "bind" the Documents folder in /mnt/Data to the Documents folder in home using a very simple command:
```
mount --bind /mnt/Data/Documents /home/morbius/Documents
```You can run that command as sudo, you can place it in /etc/rc.local, or if you really want to get fancy you can set it up as an upstart job ( which is the most full-proof way IMO ). When I save something to /home/morbius/Documents it's really going to /mnt/Data/Documents. OS's will come and go but /mnt/Data remains. You might have to change ownership if the new OS is not in the same family of Linux so that the uid's match the new system. You could have done the same thing by mounting your old Ubuntu home partition as ... I don't know .... /mnt/Uhome.

A separate home partition is a very overrated option. It does contain all of your data but it also contains all of your configuration files. Those files will either interfere with the new os or be completely incompatible with it depending on what OS your installing.

Just my opinion ;)

Morbius1

Thank you very much for the comments you have made. 
Your solution seems sound to me, and I'm sure I will Implement it very soon.
Onve i get all my data back on the current Install. i need to do some house keeping with it, and then,I think I will reinstall , using your solution.
I was attempting to keep my data,in a way that would let me install operating systems unhindered, but like i say i am such a noob. :D

But rejoice, we are members of the worlds greatest community :KS:KS:KS

---

### Post by Hedgehog1 on 2011-06-02
> **Morbius1 said:**
> A separate home partition is a very overrated option. It does contain all of your data** but it also contains all of your configuration files**. Those files will either interfere with the new os or be completely incompatible with it depending on what OS your installing.

A very valid point!  When distro hopping, you really need to remove the hidden configuration files if you are planning to use the same '/home' directory (separate partition or not).  We never got that far in this failed attempt!

***The Hedge***

:KS

---

### Post by Morbius1 on 2011-06-02
In the unlikely event that someone actually does a search and find this topic let's do a postmortem of the process followed on this thread:

[1] You suggested the wrong blkid command and got the following:
> 19726af5-abaa-49b3-9914-bafa4667e6ef
0e660a7a-de9f-4fff-aa57-789351e5dfa7
3efc8c6e-5b5b-44ab-b5c8-5a0711542b7aIt's a random list of UUID's. There's nothing connecting each UUID to a /dev/sdxy or a label and it doesn't tell you what filesystem is on that partition. You used a process of elimination to determine the missing home partition and then flat out guessed that it was formatted in ext4. Given the length and format of the UUID's one could ascertain that it was not fat32 or ntfs but that's about it. It was most likely a Linux format but it could have been ext3 or even btrfs for all we knew.

[2] You got the following steps reversed:
> Yes, please reboot. When you do, your real '/home' directory will be ignored (please don't delete it), and instead the '/home' partition will be used instead.

The only other step you may need to do is if the internal value for the first user is different from Ubuntu and Fedora (Ubuntu starts at 1000).If you suspected that the uid's were different you needed to change them before rebooting or else the user would confront a system that doesn't recognize the user in the new /home partition.

[3] You got this step reversed as well:
> A very valid point! When distro hopping, you really need to remove the hidden configuration files if you are planning to use the same '/home' directory (separate partition or not). We never got that far in this failed attempt!If you suspect that there's a conflict in the configuration files why wait until there is a conflict to fix it. If you remove all the configuration files from the /home partition it's now a Data partition and I would argue should be used as such.

---

### Post by rewyllys on 2011-06-03
> **Morbius1 said:**
> In your defense you had the right idea to begin with:
Pointing the fedora subdirectories to the old Ubuntu subdirectories is completely different than the path you followed here. Here you attempted to make the Fedora home directory the old Ubuntu home partition. 

I set up a data partition at /mnt/Data. In that partition I create all the major subdirectories of a typical home directory ( i.e., Documents, Downloads, Music, Pictures, ... )

When I install a new OS I don't create a separate home partition. I allow it to create a home directory within / instead. After the install I "bind" the Documents folder in /mnt/Data to the Documents folder in home using a very simple command:
```
mount --bind /mnt/Data/Documents /home/morbius/Documents
```You can run that command as sudo, you can place it in /etc/rc.local, or if you really want to get fancy you can set it up as an upstart job ( which is the most full-proof way IMO ). When I save something to /home/morbius/Documents it's really going to /mnt/Data/Documents. OS's will come and go but /mnt/Data remains. You might have to change ownership if the new OS is not in the same family of Linux so that the uid's match the new system. You could have done the same thing by mounting your old Ubuntu home partition as ... I don't know .... /mnt/Uhome.

A separate home partition is a very overrated option. It does contain all of your data but it also contains all of your configuration files. Those files will either interfere with the new os or be completely incompatible with it depending on what OS your installing.

Just my opinion ;)
Thanks for your comments on a separate /Data partition.  I can see that this idea would solve some problems I've encountered, and I plan to implement it.

Could you please expand on how one can handle the mounting of such a partition "as an upstart job (which is the most fool-proof way IMO)"?  For example, do you use a bash script for this task, with that script among the startup tasks? And if so, what should such a script say?  Or do you do something else?

Any and all details will be much appreciated.  

Thanks in advance.

---

### Post by Morbius1 on 2011-06-03
Let's say you have a Data partition mounted in fstab at /mnt/Data.

[1] Create an upstart script named "home-mounts.conf"
```
gksu gedit /etc/init/home-mounts.conf
```[2] The content of that file would look something like this:
```
# Remount partitions with bind
#
description "Bind Data Subdirectories to Morbius' Home Directory"

start on stopped mountall

script
mount --bind /mnt/Data/Documents /home/morbius/Documents
mount --bind /mnt/Data/Downloads /home/morbius/Downloads
mount --bind /mnt/Data/Music /home/morbius/Music
end script
```That's it. The "start on stopped mountall" is upstart-eese for "dont run the following scripts until all the mounts in fstab are finished"

The other way to do this is use symbolic links from the /mnt/Data partition to the home partition but  I like this way better. For one thing I have the attention span of a gnat so I forget sometimes what I've linked to or not. I can usually remember that I used a upstart bind job so all I have to do is open it up to see what I've done all in one place.

Back in ancient history you were able to do this in fstab with a slightly different syntax but that method is no longer reliable ( at least not in Ubuntu ). And of course it will only work if the OS you're dealing with uses upstart.

---

### Post by rewyllys on 2011-06-03
Morbius1, 

Many, many thanks!  That script is exactly what I needed to get started.:popcorn:

---

