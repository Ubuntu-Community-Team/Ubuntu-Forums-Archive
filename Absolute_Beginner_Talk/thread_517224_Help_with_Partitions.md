---
title: "Help with Partitions"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Nike T on 2007-08-04
Hi, I'm new here and I wanted to install ubuntu.  I want to dual-boot with Windows and I was wondering if when you use gparted and you edit the partitions do you have to install everything in Windows again, because that's what my dad says.

---

### Post by forestpixie on 2007-08-04
only if you make mistakes and install over the top of it :)

have alook at this 

[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)

---

### Post by stevebakerj on 2007-08-04
Welcome Nike T,

First, [COLOR="Red"]**backup**[/COLOR] everything.

then look here:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

and here:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

and no you don't have to reinstall everything in Windows, but don't forget,[COLOR="Red"]** backup everything thats important**[/COLOR].

Enjoy

---

### Post by sad_iq on 2007-08-04
Just do a nice defrag from windows and check the drive for errors before proceeding to install. Also take a look here...give you a clue about dual-boot:  [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Nike T on 2007-08-04
Thanks for all the help, but my dad still isn't convinced about this installing everything again, so he told me to ask if I have to reformat the hard drive and then redo all the partitions and then reinstall everything

---

### Post by forestpixie on 2007-08-04
at the moment I assume you've got windows on one partition - is this correct? If not how many partitions does the disc have?

How much room is there on either the one drive or on the partitions.

Give us as much information as you can and we'll be able to help more.

You don't have to reformat the whole drive - but you will be reformatting the part on which Ubuntu is going to be installed.

---

### Post by stevebakerj on 2007-08-04
Hi Nike T

As we have all said read here:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

and you will see that you can install Ubuntu/Kubuntu/Xubuntu or any *nix distro without affecting your Windows install, just ensure you follow the Dual Boot instructions as detailed in the article above.

But as always [COLOR="Red"]**backup everything**[/COLOR], I can understand your fathers caution so[COLOR="Red"]** backup everything first**[/COLOR].

---

### Post by forestpixie on 2007-08-04
> **stevebakerj said:**
>  I can understand your fathers caution so[COLOR="Red"]** backup everything first**[/COLOR].

as can I - I would have a minor fit if one of my young ones told me they were going to be installing stuff on my pc :D

---

### Post by Nike T on 2007-08-04
> **forestpixie said:**
> at the moment I assume you've got windows on one partition - is this correct? If not how many partitions does the disc have?

How much room is there on either the one drive or on the partitions.

Give us as much information as you can and we'll be able to help more.

You don't have to reformat the whole drive - but you will be reformatting the part on which Ubuntu is going to be installed.

Right now I have 4 partitions, I have one that is FAT16, it's the first 55 mb, I have one that is NTFS, it's 24.4 gigs, I have 1 that is FAT32 that is 3.4 gigs, and some unallocated space.  I used Gparted to find that out from the live Ubuntu CD, is there another way to find that out?

EDIT: o yea and I've backed up my music, videos and other stuff in the my documents folder, is there anything else that I should be backing up?

---

### Post by belikralj on 2007-08-04
Have you decided where you will install ubuntu? How big is the unallocated space? Since I'm not sure what you want us to tell you, I'll just walk you through how I installed Ubuntu the first time. I used PartitionMagic to resize the Windows partition because I only had it on my hard disk and made some space for Ubuntu (about 6 GB + 1 GB for Swap). As I understand you have a few partitions more than I did plus some unallocated space. Depending on where you want to put Ubuntu (on which partition, new or existing) you will need to reformat it and make it ext3 filesystem for Ubuntu and will have to make one more additional partition for Swap space (it is the linux equivelant of the Page file and must be on a separate partition with it's own spetial filesystem), the reformating is a part of the instalation and the partitions you can make in gParted and if you can't reformat your partitions in it (I don't see any reason you couldn't) you can always use PartitionMagic just google for it. After you have prepared the partitions you put Ubuntu on the ext3 and Swap on Swap and that's all about partitioning I can think of at the moment.

---

### Post by Nike T on 2007-08-04
O srry the unallocated space is 7.8 mb's, I don't know where that came from, and the FAT32 partitions I also don't know where it came from, since I did not create it.

---

### Post by Nike T on 2007-08-05
I found out that the FAT32 partitions is some dell restore thingy.  I have a bigger problem now though, I tried shrinking the NTFS partition in gparted, but I get an error, I defraged twice.  I looked in the details and it said "ntfsresize -p --force --force /dev/sda2 -s 19914719232 --no-action.  Does anyone know what I'm doing wrong?

---

### Post by stevebakerj on 2007-08-06
With gparted you can resize a partition only if there is no data in the freed up part of the partition.  That's why you need to defrag before and I would defrag twice at least after clearing out any unused software

However the free space in a partition is never in only one segment. If something remains written in the last sectors of the partition, then you can't shrink it.

In your case, I see that you have about 24 GB in total on the NTFS partition, how much of this is free? . 

If this free space isn't located at the end of the current partition, then there is problem and error. It's probable that the free space is distributed all over the partition. 

If you could give us a screen shot of the gparted screen, it would be very helpful to better understand your system state.

---

### Post by Nike T on 2007-08-06
I have about 18.something gigs used on my hard drive.  I tried to free up 6 gigs.  Then I tried 5 gigs.  Then I tried to free up 1 gig, none of them worked.  I'll get the screenshot of gparted.

---

### Post by psusi on 2007-08-06
Force windows to run a chkdsk on the partition.  Run chkdsk /f c: and answer yes to the prompt, then reboot windows and let it check the disk.

---

### Post by Nike T on 2007-08-06
Wow, you're the best.  Thanks for the chkdsk thing, I'm pretty sure it will work now.

---

### Post by Nike T on 2007-08-06
Actually it didn't do the trick.  I think I know the problem, when I defrag my hard drive there is this big patch of stuff that's floating around near the end of the bar.  Is that the problem, if it is how do I fix it, I tried to defrag it again and I don't know why but it seems to be doing the trick

---

### Post by Nike T on 2007-08-06
ok, nothing is working at all.  I defrag a few times, reboot and use the gparted live cd.  I try to resize my ntfs partitions I get an error, and then something happens, my drive shows that I have nothing on it.  I get out of gparted and reboot, chkdsk pops up and starts checking, when I get back into windows everything is the same, nothing's changed and it's still not working, I really need help. :(

---

### Post by psusi on 2007-08-07
If defrag won't move files away from the end of the partition, then you will just have to backup, reformat, and restore.

---

### Post by yorkie on 2007-08-07
[http://video.google.co.uk/videoplay?docid=-2369893842637434537](http://video.google.co.uk/videoplay?docid=-2369893842637434537)

above link video on howto dual boot with windows this might help you if you can see how its done then its easier to do it your self
good luck

---

### Post by Nike T on 2007-08-07
I saw the partitioning part of the movie thing and the options that it shows are not the same, for mine it says guided use entire disk, use largest continuous space, and then manual partition (which doesn't work)

---

### Post by Nike T on 2007-08-07
Here's a pic of my defrag screen, should it work? [IMG]http://img2.putfile.com/main/8/21817482680.jpg[/IMG]

I think maybe I'm gonna have to use Wubi until I get an external hard drive where I can install  Ubuntu without problems.

---

### Post by thefoolisme on 2007-08-08
Honestly, I don't think there's really enough room to siphon some space off the c drive.  it looks pretty full, and if you take some away, it's not going to have room on the disk to write to.  I think your dad would be mad if he went to save something in windows and got a full disk message.  

It looks like 2/3 of the hard drive is full, leaving you only 7-8 GB to take for Ubuntu.  You have to leave space in the windows for storage, and temp writing to HD, etc.  I would think you would want at least 8GB for Ubuntu,  because I'm betting you want to play with Beryl/compiz and all the eye candy.  

I think if you try to partition off part of your drive, neither one of you will have enough room to do what you want to do.  I would reccomend an additional hard drive personally.  It's a cheap fix, and you'd have plenty of breathing room.

---

### Post by Nike T on 2007-08-08
It's almost my laptop, my dad got a new one and he won't be using this one, he made this one like a family laptop, but I'm mostly the only one that uses, but he doesn't want anything to happen to it, like wiping it or something, he'd get really mad at that.  Once I save up enough money I'll get an external hard drive and then there won't be any problems.  Thanks for telling me about the space problem.

---

