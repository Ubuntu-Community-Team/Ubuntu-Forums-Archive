---
title: "I got scared installing versuib 6.06 LTS to my Mac"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by midiw on 2007-01-10
I received the mac CD installer as requested.

The install instruction as printed on the inside cover of the CD jacket was brief.

OK, I thought, that sounds rather simple to install.

So I fired up my MDD G4 1.25 GHz 2 GB RAM with 4 internal hard drives.

I errased one of the hard drives in preparation for installing LINUX. In fact I named that drive LINUX so that I could easily identify that drive.

However much to my chagrin after restarting I am facing a screen with white on black print. What the? do I do now.

After my heart quit pounding I typed in some letters ( can't remember what they were now ).

Whoa, off I go to the land of Linux. The landscape is orage/brown. Well, OK.

Then I see an "install" icon in the left hand side of my screen.

Oh sure, what the hey, let's try that.

Whoa, now I see a listing of my 4 internal hard drives.

But LINUX/UBUNTU does not name them the names I named my 4 droves. Where's that dirve I named LINUX ?

LINUX/UBUNTU names with what the manufacturer named them I guess. 

Which hard drive should I select to erase?

Tell, please, tell me LINUX/UBUNTU....

Bail out men, this could be the end of all four hard drives.


Why oh why can't LINUX/UBUNTU provide a heads up printed sheet ( maybe two pages ) to give fair warning and step by step instructions with screen shots. Especially when you guys went to all that expense of mailing out the CD.

I'm not a LINUX geek but sure would love to become a citizen of the LINUX/UBUNTU  nation.

Could some one from the nation of LINUX/UBUNTU please provide me with the steps to take to make the installation and use of LINUX a pleasure.

I'm still so scarred I am sleeping with one eye open for fear of being swept away into LINUX/UBUNTU land.


](*,) ](*,) ](*,) ](*,)

---

### Post by rai4shu2 on 2007-01-10
If it's that big a deal, make a backup. Then, even if you do lose all your Mac data, you have a backup to fall back to.

---

### Post by midiw on 2007-01-10
> **rai4shu2 said:**
> If it's that big a deal, make a backup. Then, even if you do lose all your Mac data, you have a backup to fall back to.

back up 4 hard drives ?

no offence my friend really there should be a  detailed instruction sheet or why waste monies in mailing out the system

i thinks i got this installation solved 

thank you for you encouragement

---

### Post by jimrz on 2007-01-10
> **midiw said:**
> I received the mac CD installer as requested.

The install instruction as printed on the inside cover of the CD jacket was brief.

OK, I thought, that sounds rather simple to install.

So I fired up my MDD G4 1.25 GHz 2 GB RAM with 4 internal hard drives.

I errased one of the hard drives in preparation for installing LINUX. In fact I named that drive LINUX so that I could easily identify that drive.

However much to my chagrin after restarting I am facing a screen with white on black print. What the? do I do now.

After my heart quit pounding I typed in some letters ( can't remember what they were now ).

Whoa, off I go to the land of Linux. The landscape is orage/brown. Well, OK.

Then I see an "install" icon in the left hand side of my screen.

Oh sure, what the hey, let's try that.

Whoa, now I see a listing of my 4 internal hard drives.

But LINUX/UBUNTU does not name them the names I named my 4 droves. Where's that dirve I named LINUX ?

LINUX/UBUNTU names with what the manufacturer named them I guess. 

Which hard drive should I select to erase?

Tell, please, tell me LINUX/UBUNTU....

Bail out men, this could be the end of all four hard drives.


Why oh why can't LINUX/UBUNTU provide a heads up printed sheet ( maybe two pages ) to give fair warning and step by step instructions with screen shots. Especially when you guys went to all that expense of mailing out the CD.

I'm not a LINUX geek but sure would love to become a citizen of the LINUX/UBUNTU  nation.

Could some one from the nation of LINUX/UBUNTU please provide me with the steps to take to make the installation and use of LINUX a pleasure.

I'm still so scarred I am sleeping with one eye open for fear of being swept away into LINUX/UBUNTU land.


](*,) ](*,) ](*,) ](*,)

I'm not familiar with the mac system and so not sure how you can check your drives from it. You could kill the install and go into mac to llok in your partioner to identify the correct drive. You could also continue in the install to the section where you partition the drive and select the "manually partion" option, this will open the partition (Gparted) which will show you a great deal of information (drive id, size, mount point, file system, used/unused space, etc) that likely would allow you to determine the correct drive you want to install to. If this is the case simly create your partio(s) and proceed with the install. However, if after reviewing the info in Gparted you are still uncertain, I would suggest stopping the installion until you have determined for certain exactly where you wish to install to.

---

### Post by KaeseEs on 2007-01-11
Check out...

[http://paulstamatiou.com/2005/10/24/how-to-ubuntu-linux-for-novices/](http://paulstamatiou.com/2005/10/24/how-to-ubuntu-linux-for-novices/)

This guy installed Ubuntu in a dual-boot on his G4, and has a link up (under 'installation') inviting folks to e-mail him if they want help doing the same.



Otherwise...


Ubuntu is most likely labeling your disks using the internal disklabels.  These may not be descriptive, however, so your best bet is to distinguish them by size - just write down the size of the disk you blanked.  Note that you're likely going to have to reformat it again, anyways, as Linux tends to use different filesystems than a Mac.  This will be done during the install process.

Google may be your best frind when it comes to a screenshot walkthrough of the install process, however.

PS - I would suggest filing a bug that the LiveCD doesn't recognice Mac drive names.
Also, best of luck!

---

### Post by rccharles on 2007-01-11
> **midiw said:**
> 

So I fired up my MDD G4 1.25 GHz 2 GB RAM with 4 internal hard drives.

I errased one of the hard drives in preparation for installing LINUX. In fact I named that drive LINUX so that I could easily identify that drive.



My first suggestion is to physical detach the three harddrives you do not want touched.  I am not sure how you identify which three and you could get it wrong.  I guess you would put in the Mac OS install cd and see what disk utility said.

This is along the lines of jimrz's post.

I recently installed Ubuntu 6.10 from the alt cd on my iMac.  I was a little worried too.  I did backup my entire harddrive. 

How I installed was to pick the option to install on the largest free space. 

What you did when you said erase the entire disk was to put the MacOS extended file system on your disk.  This isn't the same as free space.  It will be hard to identity the partition from this information.


What I suggest you do is to go into the Mac OS Disk Utility. Select your drive. Go into Partition and change the 'erased' partition to free space. Remember the size.  Maybe make it a funny size.

In the Ubuntu partitioner you will be able to identify free space.  Use this area to make your ubuntu partitions.

On the Alt cd, Ubuntu gave the option of installing in the largest free space.  This is what I used.

On my iMac g3, I can press the option key ( or alt on a PC keyboard. ) to get up a menu of bootable partitions.  You press the option key just after powering on the Mac.  This will show you the Linux bootable partitions and you can pick the one to boot.  

Robert

---

### Post by midiw on 2007-01-12
TVM

Now that's the kind of help I was expecting to get.

You folks have really assured me that I should not be scared and also the urls for installing on a Mac by a non geeky guy albeit more then old and goofy.

As I noted in my original posting I can only hope that when the next batch of Mac Ubuntus get mailed out that they provide a beginners guide on  how to install on a Mac. In the Mac world we just point and click and allow the programme to do the rest.

I know I'm going to love this new  world of LINUX that I've only just discovered. Ah sure, better late then never. 

:)

---

