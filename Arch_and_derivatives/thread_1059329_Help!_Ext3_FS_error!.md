---
title: "Help! Ext3 FS error!"
date: 2009-02-03
forum: Arch and derivatives
---

### Post by mips on 2009-02-03
First a basic rundown. My PC has a 500GB USB WD MyBook (/dev/sdd1) ext3 external drive I use to backup my /home which lives on a internal 500GB sata drive.

 Problem is my /home is currently empty as I did a fresh install a while ago so now I only have one copy of my data which is on the fubarred external 500GB USB drive!!!

 **How save is it to run [COLOR=Red]fsck -yt ext3 /dev/sdd1[/COLOR] on this drive?**

 Or should I rather remove the drive from it's housing (invalidates warranty but I can live with that) and connect it directly to my MB HD controllers, make an image with dd to my blank internal drive and then try and fix it?

Output of fsck -vnt ext3 /dev/sdd1,
```

[mips@obelix ~]$ fsck -vnt ext3 /dev/sdd1
fsck 1.41.3 (12-Oct-2008)                
e2fsck 1.41.3 (12-Oct-2008)              
/dev/sdd1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes                 
Inode 73733, i_blocks is 197680, should be 767608.  Fix? no

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts      
Unattached inode 581702                
Connect to /lost+found? no             

Unattached zero-length inode 581703.  Clear? no

Unattached inode 581703
Connect to /lost+found? no

Unattached zero-length inode 581704.  Clear? no

Unattached inode 581704
Connect to /lost+found? no

Unattached zero-length inode 581705.  Clear? no

Unattached inode 581705
Connect to /lost+found? no

Unattached zero-length inode 581706.  Clear? no

Unattached inode 581706
Connect to /lost+found? no

Unattached zero-length inode 581707.  Clear? no

Unattached inode 581707
Connect to /lost+found? no

Pass 5: Checking group summary information
Block bitmap differences:  -(65799--65806) -(119602--119608) -(119836--119841) -(120071--120074) -(128750--128756) -(135147--135153) -(136527--136531) -(147651--147658) -(148317--148323) -(148356--148362) -(170248--170254) -(170957--170963) -(170991--170997) -(171461--171467) -(171608--171614) -(171889--171895) -(172524--172528) -(172723--172729) -(172839--172845) -(173203--173206) -(173216--173222) -(173715--173721) -(174325--174331) -(176126--176132) -(177927--177933) -(178605--178611) -(179074--179080) -(179534--179537) -(179910--179914) -(181793--181797) -(183062--183068) -(183171--183173) -(183606--183612) -(184034--184037) -(188123--188129) -(188222--188228) -(188959--188966) -(192146--192152) -(192479--192481) -(192621--192627) -(193232--193238) -(193247--193253) -(193369--193374) -(193388--193392) -(194628--194634) -(196459--196465) -(197402--197404) -(198043--198049) -(198758--198762) -(199353--199359) -(199970--199976) -(200198--200204) -(201009--201013) -(202137--202143) -(202145--202152) -(207630--207636) -(208834--208840) -(209224--209230) -(210839--210840) -(210908--210913) -(214455--214461) -(215612--215618) -(215986--215992) -(219945--219951) -(222462--222468) -222765 -(223010--223014) -(223922--223928) -(223930--223937) -(227552--227559) -(230660--230667) -(232537--232543) -233320 -(234260--234266) -(234372--234375) -(235836--235842) -(235992--235994) -(235996--236003) -(262403--262410) -(296196--296203) -(333540--333546) -(337821--337827) -(338856--338859) -(449137--458751)                                    
Fix? no                                                                                          

Free blocks count wrong for group #11 (15789, counted=0).
Fix? no                                                  

Free blocks count wrong for group #12 (32502, counted=1).
Fix? no

Free blocks count wrong for group #13 (32510, counted=0).
Fix? no

Free blocks count wrong (14884490, counted=14803690).
Fix? no

Free inodes count wrong for group #71 (8189, counted=8185).
Fix? no

Free inodes count wrong (30450959, counted=30450955).
Fix? no


/dev/sdd1: ********** WARNING: Filesystem still has errors **********


   80625 inodes used (0.26%)
    3791 non-contiguous inodes (4.7%)
         # of inodes with ind/dind/tind blocks: 47099/22570/5
107211510 blocks used (87.81%)
       0 bad blocks
      13 large files

   72222 regular files
    8379 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
      19 symbolic links (1 fast symbolic link)
       0 sockets
--------
   80614 files

```The thing that annoys the hell out of me is that ext3 is supposed to be the 'stable' FS. This is the second time on a different drive ext3 has failed me,  xfs to date has not let me down once, grrr.

---

### Post by handy on 2009-02-03
If it is the only copy of your data, then I would remove the drive & make an image of it.

Was the other one that failed also a USB drive?

I personally don't like USB for connecting drives.  I hope I can happily change my mind when USB 3.0 hits the streets.

---

### Post by mips on 2009-02-04
> **handy said:**
> If it is the only copy of your data, then I would remove the drive & make an image of it.

Was the other one that failed also a USB drive?

I personally don't like USB for connecting drives.  I hope I can happily change my mind when USB 3.0 hits the streets.

I think I will remove the drive then.

The previous time this happened was a long time ago. I had two identical WD 160GB sata drives with the one acting as a backup/mirror for /home. The ext3 FS one croaked.

I'm not a big fan of USB either, firewire or eSata would be a much better option. When I open the enclosure up I will investigate the possibility of getting another enclosure with USB, Firewire & eSATA but they are usually not that cheap.

---

### Post by handy on 2009-02-04
I could have said this, & I could have said that.

But the reality of the situation was that, nothing I could have or would have said would have been more valuable than your own knowledge.

So, the above was my way of saying nothing.

:lolflag:

{[(mips, god knows who I was talking to in this post, I would just like you to know that it was not you.)]}

---

### Post by mips on 2009-02-04
> **handy said:**
> I could have said this, & I could have said that.

But the reality of the situation was that, nothing I could have or would have said would have been more valuable than your own knowledge.

So, the above was my way of saying nothing.

:lolflag:

{[(mips, god knows who I was talking to in this post, I would just like you to know that it was not you.)]}

Lol, I was wondering what your were on about :p

Anyway I manage to remove the drive from it's housing which basically destroyed 3 small clips in the process.
I used this guide, [http://rebootdaily.blogspot.com/2007/03/how-to-open-western-digital-my-book.html](http://rebootdaily.blogspot.com/2007/03/how-to-open-western-digital-my-book.html) My model is a later one so I did not have to bother with the case screw.

I however have to update the firmware on my internal Seagate first as it is one of those affected by the firmware bug. I will do this first before even attenting to image the WD drive. Wish me luck as firmware uprgades genrally make me nervous.
[http://ubuntuforums.org/showthread.php?t=1043795](http://ubuntuforums.org/showthread.php?t=1043795)

I'm really not having a good day today. Woke up in the early hours of the morning with an inflamed & pinched muscle under the right shoulder blade. Doing anything is painfull as well. I suppose I should be thankfull as there are others worse off than me though.

I'm going to use ddrecue instead of normal dd.

Will give feedback a bit later on.

---

### Post by handy on 2009-02-04
> **mips said:**
> 
Lol, I was wondering what your were on about 

I got pissed yesterday, which is a very rare occurrence these days.  I expect to find that I made a few strange posts last night.  Oh well. :-)

> **mips said:**
> 
I'm not a big fan of USB either, firewire or eSata would be a much better option. When I open the enclosure up I will investigate the possibility of getting another enclosure with USB, Firewire & eSATA but they are usually not that cheap.

I had a USB & firewire external once, I only used the firewire interface.  It died well inside of warranty (cheap Chinese crap).  It did not cost me much as I had dealer pricing at the time.

I didn't bother with warranty return as I have found that sometimes it is more trouble than it is worth when you live outside of towns & cities.

I hope your data survives.  

Have you thought of setting up a FreeNAS box, you could use the same drive, & if PII & PIII's are available very cheap where you are it will cost you next to nothing.

Just boot it up when you want to do a backup.  I'm sure you would really enjoy the process of creating the thing, it really is good fun, as they have done it so well.  

Just a thought. :-)

---

