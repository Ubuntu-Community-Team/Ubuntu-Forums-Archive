---
title: "Help, I messed up GRUB :-("
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by pbb on 2006-01-01
A few weeks ago, I installed Ubuntu on my harddisk, dual-booting with Windows XP.

Today, I was re-organizing Windows a bit, and decided to create a FAT32 partition so that I can use my files both in Windows and Ubuntu.

So I fired up Partition Magic, shrank one of my NTFS partitions, and created a new FAT32 partition.

Then I rebooted my computer again, and GRUB (the program that allows me to choose between Windows and Ubunutu), just responded with "Error 17". No other messages, no help, no prompt, nothing.

I tried re-installing Windows, which seemed to work as expected on first hand. But rebooting after reinstalling gave me the exact same GRUB error again.

I am now running from the Ubuntu Live CD. It seems I can mount and access my partitions from there, so I have good hope eveything can be restored to working conditions, but I have no idea how!

Can anyone tell me how to get my system booting again?

---

### Post by Swab on 2006-01-01
[QUOTE=pbb]A few weeks ago, I installed Ubuntu on my harddisk, dual-booting with Windows XP.

Today, I was re-organizing Windows a bit, and decided to create a FAT32 partition so that I can use my files both in Windows and Ubuntu.

So I fired up Partition Magic, shrank one of my NTFS partitions, and created a new FAT32 partition.

Then I rebooted my computer again, and GRUB (the program that allows me to choose between Windows and Ubunutu), just responded with "Error 17". No other messages, no help, no prompt, nothing.

I am now running from the Ubuntu Live CD. It seems I can mount and access my partitions from there, so I have good hope eveything can be restored to working conditions, but I have no idea how!

Can anyone tell me how to get my system booting again?[/QUOTE]

If you can manage to boot into your normal Ubuntu then you should be able to fix this.  

Plan of action?  Find out on which partition Ubuntu is installed.. you can find this in /boot/grub/menu.lst ... so open up your menu.lst and find the Ubuntu entry.... copy down all the details... mine looks like this:

title           Ubuntu, kernel 2.6.12-10-686
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-686
savedefault
boot


Now reboot using the live CD and get to the grub console/command line.  You should be able to boot up your HD installed Ubuntu by entering:

root (hd0,1)       <enter>
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda2 ro quiet splash   <enter>
initrd          /boot/initrd.img-2.6.12-10-686 <enter>
savedefault <enter>
boot <enter>

Obviously replacing with the information your got from your menu.lst

Once you are booted.. open up a terminal and type:

sudo grub-install hd0  (or whichever disk your ubuntu is installed on)

Hopefully this will fix everything.

---

### Post by Swab on 2006-01-01
If it wasn't clear I was referring to /boot/grub/menu.lst on your hard drive... let me know how it goes.

---

### Post by pbb on 2006-01-01
Thanks for lending a hand, Swab!

I am *not* able to boot into "normal" Linux (that is, the Linux installed on my harddrive). Grub just dies with an error number. I am only able to run the Live CD.

I guess the boot.lst file is located on my Linux partition? That should be sda6 if I'm not mistaking. However, I only ever learned how to mount NTFS partitions, I don't know how to mount that Linux partition.

---

### Post by Swab on 2006-01-01
[QUOTE=pbb]Thanks for lending a hand, Swab!

I am *not* able to boot into "normal" Linux (that is, the Linux installed on my harddrive). Grub just dies with an error number. I am only able to run the Live CD.

I guess the boot.lst file is located on my Linux partition? That should be sda6 if I'm not mistaking. However, I only ever learned how to mount NTFS partitions, I don't know how to mount that Linux partition.[/QUOTE]

Is your harddrive scsi?  Normally a harddrive partitions would be hdxx... my linux partitions is hda2....

Anyway you can type man mount from terminal on the live CD to get info on mounting.

---

### Post by Swab on 2006-01-01
You can find out about all your partitions from System > Administration > Disks

---

### Post by pbb on 2006-01-01
Wow, thanks again Swab. Being so new to Ubuntu, I hadn't even found the Disks application yet. (Everybody always just directed me to the command prompt.)
Okay, I've mounted my Linux partition now, found my menu.lst, I am going to edit that now and try it out.

By the way, it's not a SCSI drive, but SATA. Apparently, that is also labeled as sda...

---

### Post by Swab on 2006-01-01
[QUOTE=pbb]Wow, thanks again Swab. Being so new to Ubuntu, I hadn't even found the Disks application yet. (Everybody always just directed me to the command prompt.)
Okay, I've mounted my Linux partition now, found my menu.lst, I am going to edit that now and try it out.

By the way, it's not a SCSI drive, but SATA. Apparently, that is also labeled as sda...[/QUOTE]

Are you sure you need to edit the list?  Anyway back it up first.

If I were you I would try and boot into your hd installed ubuntu first.

---

### Post by pbb on 2006-01-01
Okay, apparently I misunderstood you...

How do I "boot into my hd installed ubuntu"? Grub just dies on me with "Error 17".

---

### Post by Swab on 2006-01-01
[QUOTE=pbb]Okay, apparently I misunderstood you...

How do I "boot into my hd installed ubuntu"? Grub just dies on me with "Error 17".[/QUOTE]

Do you get to the GRUB menu before the error? If so you can type c to get to the GRUB command line... from there you can boot your HD Ubuntu as I described in my first post... if you can't get to the GRUB menu then we need to think of another way.. I'm gonna check if you can use the live CD to boot your HD install.

---

### Post by pbb on 2006-01-01
[QUOTE=Swab]Do you get to the GRUB menu before the error?[/QUOTE]

Nopes, it just says "Loading boot menu.1.5." (or something in that direction) and then comes the error message. No menu whatsoever.

I haven't tried if I can actually type in anything. I will try to see if anything happens when I type "c".

---

### Post by cbudden on 2006-01-01
Hello.  I have had this error before, and I fixed it by putting in the Ubuntu install CD and when it gets past the detecting hardware stage, pressing ESC and skipping onto the set up the partitions.  Mount your partitions where they shoud be, root, home, swap etc but do not format anything.  Once the partitioner has set up press esc again and go to the install grub section.  Once grub has installed, reboot and you should get your normal grub menu back.  Just remember, read the instructions from the installer carefully as you wouldn't want to re install Ubuntu or delete any data.

---

### Post by pbb on 2006-01-01
[QUOTE=pbb]I haven't tried if I can actually type in anything. I will try to see if anything happens when I type "c".[/QUOTE]

Tried it again. I can't type in anything after that error message.

---

### Post by Swab on 2006-01-01
Alternatively you could boot up with the live CD.   Now mount your linux partition as you have done previously... now chroot into the parition by

sudo chroot /<linuxparition>

where linuxpartition is the location where your linux partition is mounted..

now you can type:

sudo grub-install <hd0>  

where hd0 is the partition to which GRUB is installed.

Now reboot and GRUB should be back...

---

### Post by Mustard on 2006-01-01
Here is a link on recovering grub from the wiki, which can guide you on how to do it from a liveCD.

[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

When I lost my grub, I used the option explained above in another post, using the Install CD.

I went through the initial prompts for installation, until it gets to the part about manual partitioning (or I may have hit ESC as cbudden said, I don't recall now). Once at the manual partitioning stage,  I went through all the partitions, setting them all up again as they were before , but choosing **not to format them**, then installed grub again.  From there you can back out of the install and try booting up.  I found that a bit easier than using the liveCD method.

I think cbudden described the process better than me though....

[quote=cbudden]Hello. I have had this error before, and I fixed it by putting in the Ubuntu install CD and when it gets past the detecting hardware stage, pressing ESC and skipping onto the set up the partitions. Mount your partitions where they shoud be, root, home, swap etc but do not format anything. Once the partitioner has set up press esc again and go to the install grub section. Once grub has installed, reboot and you should get your normal grub menu back. Just remember, read the instructions from the installer carefully as you wouldn't want to re install Ubuntu or delete any data.[/quote]

---

### Post by pbb on 2006-01-01
[QUOTE=cbudden]Once the partitioner has set up press esc again and go to the install grub section.  Once grub has installed, ...[/QUOTE]

I looked at the partition configuration in the installer, and everything seemed to be okay. But when I choose to install GRUB, I get the error message "No root file system is defined", and the installer refuses to continue.
I have no idea what a root file system is, and how to define one.

---

### Post by Mustard on 2006-01-01
[QUOTE=pbb]I looked at the partition configuration in the installer, and everything seemed to be okay. But when I choose to install GRUB, I get the error message "No root file system is defined", and the installer refuses to continue.
I have no idea what a root file system is, and how to define one.[/QUOTE]

One of your partitions should be set up to mount on the mount point '/'.  This is the mount point for root.  It would appear that you haven't defined that part in the process of manually partitioning again.

I notice it is talking about a 'file system', so I would check whether you have it defined as using ext3 or ext2 or whatever filesystem you initially set up with.  The default is ext3 I think.

---

### Post by Mustard on 2006-01-01
As an example of where things might be mounted here is how my system is mounted...

```

# <file system> <mount point>   <type>
/dev/hda1       /               ext3    
/dev/hda6       /home           ext3

```

My root partition is /dev/hda1 mounted on the mount point '/'
My home partition is /dev/hda6 mounted on mount point '/home'.

Both use ext3 file system.

How was yours initially set up?  One single partition?  Or do you have seperate partitions for /home or anything like that?

---

### Post by pbb on 2006-01-01
Mustard, here is what setup shows me:

```
SCSI1 (0,0,0) (sda) - 80.0 GB ATA ST380013AS
  #1 primary   4 GB % * ntfs          /media/sda1
  #3 primary  59 GB   * ntfs          /media/sda3
  #2 primary 550 MB   * fat32         /media/sda2
  #5 logical  12 GB   * fat32         /media/sda5
  #6 logical   3 GB % * ext3          /media/sda6
  #7 logical 170 MB   @ swap          swap

```

Where % is a thunder symbol, * is a black face and @ is a white face (skull?).
Note the sort order (#3 before #2), and the absence of #4.

Should I look for a way to change "/media/sda6" into just "/" ?

By the way, sda5 was the new partition I created under Windows which started all the problems.

---

### Post by pbb on 2006-01-01
[QUOTE=Swab]Alternatively you could boot up with the live CD.   Now mount your linux partition as you have done previously... now chroot into the parition by

sudo chroot /<linuxparition>

where linuxpartition is the location where your linux partition is mounted..

now you can type:

sudo grub-install <hd0>  

where hd0 is the partition to which GRUB is installed.

Now reboot and GRUB should be back...[/QUOTE]

I mounted my linux partition under /media/linux, then entered the following:

    sudo chroot /media/linux
    sudo grub-install /dev/sda6

Then I got this error:

    The file /boot/grub/stage1 not read correctly.

No other information. Any ideas?

---

### Post by Swab on 2006-01-01
[QUOTE=pbb]I mounted my linux partition under /media/linux, then entered the following:

    sudo chroot /media/linux
    sudo grub-install /dev/sda6

Then I got this error:

    The file /boot/grub/stage1 not read correctly.

No other information. Any ideas?[/QUOTE]

Try sudo grub-install sda

---

### Post by Mustard on 2006-01-01
[QUOTE=pbb]Mustard, here is what setup shows me:

```
SCSI1 (0,0,0) (sda) - 80.0 GB ATA ST380013AS
  #1 primary   4 GB % * ntfs          /media/sda1
  #3 primary  59 GB   * ntfs          /media/sda3
  #2 primary 550 MB   * fat32         /media/sda2
  #5 logical  12 GB   * fat32         /media/sda5
  #6 logical   3 GB % * ext3          /media/sda6
  #7 logical 170 MB   @ swap          swap

```

Where % is a thunder symbol, * is a black face and @ is a white face (skull?).
Note the sort order (#3 before #2), and the absence of #4.

Should I look for a way to change "/media/sda6" into just "/" ?

By the way, sda5 was the new partition I created under Windows which started all the problems.[/QUOTE]

content deleted...I think I was more confusing the issue with that post.

---

### Post by Taino on 2006-01-01
[QUOTE=pbb]Mustard, here is what setup shows me:

```
SCSI1 (0,0,0) (sda) - 80.0 GB ATA ST380013AS
  #1 primary   4 GB % * ntfs          /media/sda1
  #3 primary  59 GB   * ntfs          /media/sda3
  #2 primary 550 MB   * fat32         /media/sda2
  #5 logical  12 GB   * fat32         /media/sda5
  #6 logical   3 GB % * ext3          /media/sda6
  #7 logical 170 MB   @ swap          swap

```

Where % is a thunder symbol, * is a black face and @ is a white face (skull?).
Note the sort order (#3 before #2), and the absence of #4.

Should I look for a way to change "/media/sda6" into just "/" ?

By the way, sda5 was the new partition I created under Windows which started all the problems.[/QUOTE]

scroll down to and select...

 #6 logical   3 GB % * ext3          /media/sda6

hit enter, then scroll down to the mount option and hit enter

you want to change..

#6 logical   3 GB % * ext3          /media/sda6

and make it root..

#6 logical   3 GB % * ext3          /

then submit and write that to the disk (but dont format anything)

when you reboot you should be all set.

---

### Post by Mustard on 2006-01-01
[QUOTE=pbb]I mounted my linux partition under /media/linux, then entered the following:

    sudo chroot /media/linux
    sudo grub-install /dev/sda6

Then I got this error:

    The file /boot/grub/stage1 not read correctly.

No other information. Any ideas?[/QUOTE]

I was pretty confused when I used the liveCD method, so I am not sure how you go about dealing with that error.  I'll defer to the other post above that gives some advice on what you might do from there. :)

---

### Post by Mustard on 2006-01-01
[QUOTE=Taino]scroll down to and select...

 #6 logical   3 GB % * ext3          /media/sda6

hit enter, then scroll down to the mount option and hit enter

you want to change..

#6 logical   3 GB % * ext3          /media/sda6

and make it root..

#6 logical   3 GB % * ext3          /

then submit and write that to the disk (but dont format anything)

when you reboot you should be all set.[/QUOTE]


ah ok..you sound like you remember the menu options better than me. :)

I'm only going on vague memories of how the menus worked.

---

### Post by pbb on 2006-01-01
[QUOTE=Swab]Try sudo grub-install sda[/QUOTE]

No, that does not seem to be the correct usage of grub-install:

root@ubuntu:/# sudo grub-install sda
Format of install_device not recognized.
Usage: grub-install [OPTION] install_device

By the way, sudo grub-install /dev/sda gives the known error:

root@ubuntu:/# sudo grub-install /dev/sda
The file /boot/grub/stage1 not read correctly.

Going to try Mustard's installer method now...

---

### Post by Mustard on 2006-01-01
[QUOTE=pbb]

Going to try Mustard's installer method now...[/QUOTE]

Try Taino's instructions..I think he is closer to the mark.

---

### Post by pbb on 2006-01-01
And again another wall I run into... ;-(

I start the Ubuntu Installation, press Esc to go to the installer menu, choose to install GRUB, am presented with the partition table.

I change the mount point of #6 from /media/sda6 to /, and choose "Finish partitioning", I get the following error:

> The installation to the target file system has been cancelled, as the target file system contains files from a past installation, which could break the installation process or cause a broken system to be installed. You should go back and erase or format the target file system before proceeding with the install.

Boohoo... I **do not** want to format my filesystem!!! I want to get back into Windows! It feels like it is just a crazed, non-cooperative GRUB is blocking my way!

---

### Post by Mustard on 2006-01-01
[QUOTE=pbb]And again another wall I run into... ;-(

I start the Ubuntu Installation, press Esc to go to the installer menu, choose to install GRUB, am presented with the partition table.

I change the mount point of #6 from /media/sda6 to /, and choose "Finish partitioning", I get the following error:



Boohoo... I **do not** want to format my filesystem!!! I want to get back into Windows! It feels like it is just a crazed, non-cooperative GRUB is blocking my way![/QUOTE]

Ok..I have a couple of ideas.  Firstly I need to confirm that you chose not to format /media/sda6.  If you forgot to choose 'do not format' then I would try it again.

Second idea.  I assume you are using the 'default install' process by just hitting enter when the install disk boots up.  Try using the 'expert install' process by typing 'expert' at the prompt when the install CD boots up.

I've done this successfully before, not just once, but several times, so I am sure its possible.

-edit-

Some more ideas in this thread too....

[http://ubuntuforums.org/archive/index.php/t-76652.html](http://ubuntuforums.org/archive/index.php/t-76652.html)

**IMPORTANT**  Was there the option to ignore the error you got above and continue anyway?  From reading the thread above it seems that you can.

---

### Post by pbb on 2006-01-01
Thanks for helping Mustard.

I did keep the standard option of NOT formatting the partition when changing the mount point.

I did run a default install, I will try with the expert option as you mentioned.

There was a option "Continue" on the warning screen, I will try that also. However, the warning screen for the root file system also had a Continue button, which just led back to the partition screen.

I will also look into the link you supplied.  Back to rebooting (again....) !

---

### Post by Mustard on 2006-01-01
[QUOTE=pbb]Thanks for helping Mustard.

I did keep the standard option of NOT formatting the partition when changing the mount point.

I did run a default install, I will try with the expert option as you mentioned.

There was a option "Continue" on the warning screen, I will try that also. However, the warning screen for the root file system also had a Continue button, which just led back to the partition screen.

I will also look into the link you supplied.  Back to rebooting (again....) ![/QUOTE]

I feel your pain.  Its a frustrating problem to be dealing with without any idea how to fix it.  You'll be an expert when you've finished though. :)

The main thing to focus on is that it **is fixable**.  You just have to work through the process.  I'm just frustrated that my recollection of the process is not sufficient to guide you through it smoothly without any hitches.

---

### Post by Mustard on 2006-01-01
From reading the thread it seems that default install should work fine for doing this.  So I wouldn't concentrate too much on doing it via the expert install.

---

### Post by pbb on 2006-01-01
Okay, the quick answer: GRUB is working again!

The long one:

After pressing "Continue" on the error "Not installing to unclear file system", I got another error message, this one seemed more serious.

> Installation step failed -- An installation step failed. You can try to run the failing item again from the menu, or skip it and choose something else. The failing step is: Install the GRUB boot loader on a hard disk.

When trying again, as proposed, I got the same error but this time the failing step was "Finish the installation". 

So, I thought just to go back to the forum to report my new failings. But to my big surprise, after rebooting the machine now, GRUB actually worked again! How frustrating can things get, it actually seems like all the stuff makes you believe you are doing things wrong, when in fact you are on the right way.

For all of you who ever saw "The Labyrinth":
> Hoggle: Don't listen to them, they are just False Alarms. You get a lot of them in the labyrinth, especially when you're on the right track!

False Alarm: Oh please, I haven't said it for such a long time...

Hoggle: Okay, but don't expect a big reaction.

False Alarm: Nonono, of course not. "Go Back! This Is Not The Way! Take Heed, And Go No Further!"

Sorry, I couldn't resist, my adventures in the Ubuntu Setup really gave me flashbacks...

Anyway, the story is not finished yet...

With GRUB fixed, I tried running Windows XP again. However, as part of my restoration attempts, I had run the Windows setup. So, this setup immediately continued when I tried to run Windows. And what do you know, I have insufficient diskspace to complete the setup! And of course, the setup doesn't provide a "quit" option. Rebooting just restarts the Windows setup again...

> But that's another story, and that should be told another time.

Yeaps, The Neverending Story... Time to go looking for a Windows Forum :razz:

Swab, Mustard and all the others that helped; :KS thanks a million.:KS  I wouldn't have found the solution without your help!

---

### Post by Swab on 2006-01-01
[QUOTE=pbb]Okay, the quick answer: GRUB is working again!

The long one:

After pressing "Continue" on the error "Not installing to unclear file system", I got another error message, this one seemed more serious.



When trying again, as proposed, I got the same error but this time the failing step was "Finish the installation". 

So, I thought just to go back to the forum to report my new failings. But to my big surprise, after rebooting the machine now, GRUB actually worked again! How frustrating can things get, it actually seems like all the stuff makes you believe you are doing things wrong, when in fact you are on the right way.

For all of you who ever saw "The Labyrinth":


Sorry, I couldn't resist, my adventures in the Ubuntu Setup really gave me flashbacks...

Anyway, the story is not finished yet...

With GRUB fixed, I tried running Windows XP again. However, as part of my restoration attempts, I had run the Windows setup. So, this setup immediately continued when I tried to run Windows. And what do you know, I have insufficient diskspace to complete the setup! And of course, the setup doesn't provide a "quit" option. Rebooting just restarts the Windows setup again...



Yeaps, The Neverending Story... Time to go looking for a Windows Forum :razz:

Swab, Mustard and all the others that helped; :KS thanks a million.:KS  I wouldn't have found the solution without your help![/QUOTE]

It's all good fun... it's boring when everything is working :)

---

### Post by cbudden on 2006-01-01
Glad you got it working.  A handy live / install cd boot option would be to just re install grub as it is quite tricky for most people.

---

### Post by Mustard on 2006-01-01
Persistence wins the day. :)  Well done.

---

### Post by vasudevank on 2006-01-01
good job

---

