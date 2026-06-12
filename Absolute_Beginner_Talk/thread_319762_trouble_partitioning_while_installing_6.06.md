---
title: "trouble partitioning while installing 6.06"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by andrewpb on 2006-12-16
okay i'm newer than new to this.  i'm trying to install ubuntu 6.06 and i get to the partitioning screen and am faced with three options.

erase entire disk
use largest continious free space
manually edit partition table

now i want to be able to duel boot the computer in both windows and ubuntu, and don't want to erase anything i have on windows yet.  i tried doing the "use largest..." but it said there was a problem "failed to partitioning selected disk"

now i don't know anything about partitioning, and i don't want to erase anything.  what do i do?

thanks

---

### Post by moshuptrail on 2006-12-16
Partitioning divides your hard drive into manageable "slices" for different purposes.  One slice you absolutley want is your Windows.  This will be a partition of type NTFS.

That screen with three choices is a bit mis-leading.  It looks like #3 (manually edit the partition table) would be a daunting task.  Have no fear.  There is a nice GUI-driven program (called Gparted) behind it.  Better yet, it's fairly idiot-proof.

It will give you a nice visual picture of your disk usage.  Take a look and see if you've got some space to add Ubuntu partitions.  (Yes, more than one. It's NOT Widows)

---

### Post by andrewpb on 2006-12-16
okay i think i get it...and this is make it so that i can duel boot?

danka

---

### Post by az on 2006-12-16
> **andrewpb said:**
>  i tried doing the "use largest..." but it said there was a problem "failed to partitioning selected disk"

now i don't know anything about partitioning, and i don't want to erase anything.  what do i do?



I would suggest trying to defragment your windows drive and then try again.  It should offer you the option of resizing (shrinking) your windows partition.  That it, provided it has enough free space on it.  You need something like a minimum of two gigs (more is better).

---

### Post by davd_bob on 2006-12-16
> **moshuptrail said:**
> Partitioning divides your hard drive into manageable "slices" for different purposes.  One slice you absolutley want is your Windows.  This will be a partition of type NTFS.

That screen with three choices is a bit mis-leading.  It looks like #3 (manually edit the partition table) would be a daunting task.  Have no fear.  There is a nice GUI-driven program (called Gparted) behind it.  Better yet, it's fairly idiot-proof.

It will give you a nice visual picture of your disk usage.  Take a look and see if you've got some space to add Ubuntu partitions.  (Yes, more than one. It's NOT Widows)Dog-it.  Im going through this too.  80gig drive.  15used so I will make the new size of NTFS 25gig. 55gig left.  How big for the parts and file type?  I know one will be for the OS, and one for the SWAP and these should be specific sizes.  Then the remainder will be the "User section."

Anyone want to recomend how I should chop that 55gig of unallocated?
Thanks.

---

### Post by indytim on 2006-12-16
It's really a matter of personal choice and how much you're going to load into the operating system.  To be safe you could allocate say 8-10G as ext3 for Ubuntu (or Kubuntu), 1G for /swap and maybe 5-10G ext3 for /home (where you will put your personal files etc).  Leave the rest unallocated (you may want to add a developmental version of Ubuntu or Kubuntu for testing purposes later on).

IndyTim

---

### Post by davd_bob on 2006-12-16
> **andrewpb said:**
> okay i'm newer than new to this.  i'm trying to install ubuntu 6.06 and i get to the partitioning screen and am faced with three options.

erase entire disk
use largest continious free space
manually edit partition table

now i want to be able to duel boot the computer in both windows and ubuntu, and don't want to erase anything i have on windows yet.  i tried doing the "use largest..." but it said there was a problem "failed to partitioning selected disk"

now i don't know anything about partitioning, and i don't want to erase anything.  what do i do?

thanksThanks for the info and suggestions IndyTim.
andrewpb,
I am usually pretty good at surfing until I find the answer but I guess Im getting cranky in my old age.  Instead of waiting for an answer or finding out the correct answer on how much for my partitions and what type of part, I just hit the reset button on my computer and started over.

I have Windows 2000 Pro(legal and registered) on the drive.  I defraged, then defraged again before starting the install process.
When I got there, I chose "use largest continious free space" option and then slid the bar right so it showed a 70% 30% split.(I got it backwards cause I wanted Windows to be about 24gig but it ended up over 50 gig and my Dapper stuff is now on the remaining 24gig.

I let the software do its thing then logged in when Dapper asked for username then password.

I got bogged down because I couldn't figure out how to shutdown again.  By accident I hit the little icon in the top right corner of the screen and got out.

When the system rebooted I chose Windows.   Windows began normally to a point then ran chkdsk.  When chkdsk finished instead booting the rest of the way it rebooted.

I had to choose Windows again from the dual boot menu.  This time it went all the way in, asked for my username/pasword then popped up a screen stating my "new" hardware was installed and I had to reboot.  I clicked YES to restart then had to choose Windows again from the dual boot menu.

Finally W2K came up and I went start, settings, control panel, administrative tools, computer managment, DISK MANAGER.  Im looking at D/M now showing my drive with the Windows NTFS partition, and only 2 other parts.  One is 1gig exactly and I asume that is SWAP and the remaining shows as one partition which I assume is ext3 for combined OS and USER.

Long story short(wait, i told the whole long version didn't I);)   my Windows partition is fine and W2K is running fine and Dapper boots fine and I guess its fine cause I don't have a clue what to do next, and the DUAL BOOT menu does pop up.

Can someone tell me how to edit the dual boot menu so I can give myself longer to choose.  I missed it twice and had to restart the silly computer because I wanted Windows not Dapper.

---

### Post by indytim on 2006-12-17
davd_bob,

Glad you worked your way through the installation and the build process.  You asked a question about how to edit the menu you see on dual booting.  First off there are tons of postings on  editing the menu on the forums. Here's the long-and short of it

At the terminal:
```


$cd /boot/grub
$sudo cp menu.lst bu-menu.lst
$sudo gedit menu.lst


```

Ok brief explanation:
"$cd /boot/grub" : you are changing to the directory that contains the menu.lst (the file that runs for your boot options.
"$sudo cp menu.lst bu-menu.lst" : you are making a copy of the file as bu-menu.lst (good practice when editing system files).
"$sudo gedit menu.lst" : invoking the default text editor for editing the file.
-- you will want to find the line that has the timeout and change it's value from 3 seconds to whatever you need for default decay timing.  
-- Be very careful of editing anything else in the file until you gain some additional familiarity with the system.

Good Luck,

IndyTim

---

