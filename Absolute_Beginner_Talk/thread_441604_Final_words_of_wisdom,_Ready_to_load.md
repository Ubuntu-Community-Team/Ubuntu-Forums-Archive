---
title: "Final words of wisdom, Ready to load"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by mustang2 on 2007-05-12
Ok I have installed the new sata drive ,it is active and I have not formatted it. I think I am ready to load feisty is there any final words of wisdom for me? I have 2 gigs of ram so I need 4 gig of swap file, 10 gigs for the system and the rest goes to the home partition.Is that about right? I also run a 22 inch wide screen with an Nvidia GPU, are drivers available for this? Also I read somewhere that I should have the printer, etc. on when running the setup program. I guess I need just abit of hand holding 
. Thanks

---

### Post by teaker1s on 2007-05-12
the forums are very active, mostly installs are uneventful, should you have teething problems then people will do their best to help.

Depanding on your nvidia model it may need tweaking or a beta nvidia driver-either way polite concise  questions you will receive assistance.

Welcome to the forums

---

### Post by kebes on 2007-05-12
Sounds like you're ready to go. 10 Gb system, 4Gb swap, and the rest for home is a good plan.

Your screen should work fine (you'll know when the LiveCD loads), but, yes to get full performance you'll want to install the nVidia binary driver, which is easy to do once the system is installed.

I've never had my printers hooked up during installation... but it probably doesn't hurt. Maybe they'll be auto-detected. If not, you can add them after installation.


Total install time should only be about 15-20 minutes. Good luck! And post any questions or concerns you run into along the way. (If you're using the standard install CD, it acts as a LiveCD, so you can browse the net while it is installing...)

Hope that helps... and welcome!

---

### Post by bobplano on 2007-05-12
the swap *can* be smaller because the swap holds whatever the RAM can't and you only really need double your ram for the swap if you are going to be using hibernate. the root and home are good but if you are going to be installing lots of things on ubuntu (and i mean huge programs) then it might need more, but i have 14gig and still have about 8gigs. as for the drivers, if the live cd runs fine, then it should look fine with maybe some tweaking. the reason to keep your printer on is so that it can load the right drivers for it, making it easier for you.

---

### Post by mustang2 on 2007-05-12
Thanks for the responses everyone. I am writing this in firefox from the live cd ( no problems connecting) so I guess just click setup on the desk top and away we go.

---

### Post by jkblacker on 2007-05-12
Yup sounds like you're ok to go, especially if you have no issues connecting to the net! Good luck!

---

### Post by starcraft.man on 2007-05-12
> **mustang2 said:**
> Thanks for the responses everyone. I am writing this in firefox from the live cd ( no problems connecting) so I guess just click setup on the desk top and away we go.

Hehe, don't worry... the odds of no one knowing the answer to any problem that may arise are so low, you may be hit by lightning first :p

Good luck, just make a new post if you get any issues after your installed.

---

### Post by mustang2 on 2007-05-12
Ok I am in setup and on the ready to install page and it is only showing that it is going to make 2 partitions.It never asked about the third one. It also never mentioned anything about the dual boot loader either? When I click on the advanced tab it tells me that hdo is the boot loader?? what does this mean.? Thanks

---

### Post by starcraft.man on 2007-05-12
> **mustang2 said:**
> Ok I am in setup and on the ready to install page and it is only showing that it is going to make 2 partitions.It never asked about the third one. It also never mentioned anything about the dual boot loader either? When I click on the advanced tab it tells me that hdo is the boot loader?? what does this mean.? Thanks

Well, considering you wanted to make a home partition you definitely didn't do it right, click back and go to the partitioner page. You should see 4 partitions when your done, you'll have to do it manually, I'm gonna guess ya tried to use the automatic installer. Read [this]("http://www.psychocats.net/ubuntu/installing") guide, its a good explanation how installer works (has partitioner section too :))

When your done and proceeding to install, you should see 4 partitions first should be XP i think mounted as sda/hda. Then in no particular order should be your 10 GB root, 4 gig swap and rest home. Make sure you have all 4 of those present and mounted before you write changes to your disk.

---

### Post by mustang2 on 2007-05-12
OK I see it I did go auto with the format. I'm in the right place now but don't quite understand it. It gives me a list of partition types but the only one I know for sure is the swap. Are the other two I need ext2 and ext3?I quess I need to be clear that I put the new HDD in for feisty only and  the original HDD is for XP and I want to have the dual boot option. I'm sorry to be so stupid about this but once I get a good install I won't need much help. I enjoy the challenge but I need to get this part right. Thanks

---

### Post by starcraft.man on 2007-05-12
> **mustang2 said:**
> OK I see it I did go auto with the format. I'm in the right place now but don't quite understand it. It gives me a list of partition types but the only one I know for sure is the swap. Are the other two I need ext2 and ext3?I quess I need to be clear that I put the new HDD in for feisty only and  the original HDD is for XP and I want to have the dual boot option. I'm sorry to be so stupid about this but once I get a good install I won't need much help. I enjoy the challenge but I need to get this part right. Thanks

Oh, didn't know ya had two drives. Did ya mention that, I musta missed it...

Ok then, well hold on whatever your doing right now. We gotta back up a bit, undo all the edits you made (there is an option somewhere in the first or second menu of gparted) top right corner of the partitioner lets you choose which drive you want to edit. Pick the one that is empty. Then, you want to partition out these three partitions.

Root
Mount to: /
Format: Ext3
Type: Primary
Size: 10 GB

Swap
Mount to: swap-file
Format: swap-file
Type: Logical
Size: 4 GB

Home
Mount to: /home
Format: Ext3
Type: Logical
Size: X (rest of that drive).

Those should be your 3 partitions on your new HDD, and if you change back to your other drive you should only have XP and or any other partition that you had before starting. Then when you go forward, the partitioner should mount your XP partition as data to hda or sda. That is good, you want to be able to read the data. Thats it, then I think you want to just continue and GRUB should load itself into your MBR (I think it should be your Original HDD which is loaded with grub, not certain, I keep all my OS on a single drive.) 

That should be all, hope thats all ya need.

---

### Post by mustang2 on 2007-05-12
My worst fears came true. I figured out the partitions and got ubuntu installed. Pulled the cd ,clicked restart and while rebooting when it got to loading grub it said error 22 and just hung. I reinstalled windows but it won't boot either grub error 22 again. It will at least run the live cd. What now?? I can live without linux but I have to be able to run windows.

---

### Post by kebes on 2007-05-12
Did you do a full reinstall of Windows? Normally a full reinstall would wipe the master boot record, so no trace of grub would be left.

You said you have a two-drive setup. If you disconnect the second drive, and try to boot, what happens?

If you have a Windows disk (install CD or floppy boot disk) available, boot into it and run "fixmbr":
fixmbr /mbr

This should make Windows bootable again.

---

### Post by mustang2 on 2007-05-12
No I did a windows repair. IT won't let me into the repair console because I don't know the administrator password which I never set one. But what is error 22anyway?Can I fix this? When I run the windows disc I never get to a command prompt to fixmbr.

---

### Post by starcraft.man on 2007-05-12
> **kebes said:**
> Did you do a full reinstall of Windows? Normally a full reinstall would wipe the master boot record, so no trace of grub would be left.

You said you have a two-drive setup. If you disconnect the second drive, and try to boot, what happens?

If you have a Windows disk (install CD or floppy boot disk) available, boot into it and run "fixmbr":
fixmbr /mbr

This should make Windows bootable again.

Hmmm, sorry to hear that... sounds to me though that your two installs are fine, you didn't actually have to reinstall. I'm pretty sure the only problem was setting up grub across the two HDD.

Since you need to access both OS's now, I will send you to [gag.]("http://gag.sourceforge.net/") It will automatically detect both windows and Ubuntu and set it up so you can boot both. I'm not sure exactly how to restore your GRUB so that both boot, need someone else to post. GAG is automatic though, just download and boot to it, then it will generate a boot list for you and install it to the right MBR. 

Sorry you had trouble again, hopefully someone comes by and tells ya how to restore the function to GRUB. I'm no expert on that >.>.

You can read up on GAG and GRUB [here,]("http://users.bigpond.net.au/hermanzone/") scroll down the page.

---

