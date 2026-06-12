---
title: "Hosed partition map; can't boot"
date: 2005-03-29
forum: Apple PPC Users
---

### Post by PCM2 on 2005-03-29
I made a boo-boo while trying to install Ubuntu to a partition on my Power Mac G4 and now the system won't boot to Mac OS X or to Ubuntu without some help.

Basically, I accidentally set the Boot flag on the first partition of the drive in the drive partitioning process. What this did was change the partition type of that partition from "Apple_partition_map" to "Apple_Bootstrap". Once you do this, the system won't boot.

Unfortunately, I can't find any way to change the type of the partition back to what it once was. Fdisk says it "can't create a partition with the Map type." Parted won't run at all. Near as I can tell, there's simply no way to do it, short of reformatting the drive -- but I don't want to do that, because clearly all my partitions (and my data) is still there. If I boot the Hoary disc in Rescue mode, I can boot to Linux by specifying a partition manually.

Once upon a time, there was apparently a bug in the Yellow Dog Linux installer that would  make this exact mistake on systems with more than one hard drive. Somebody in that camp came up with a hacked version of pdisk that would let you change a partition to the Apple_partition_map type. Unfortunately, the only links I can find to those hacked versions don't work (and it might be difficult to get them onto this crippled machine to begin with).

Does anyone know a way to brute-force the partition type label from "Apple_Bootstrap" back to "Apple_partition_map"? Is there a bootable CD somewhere that comes with the hacked version described above? Can Knoppix PPC do it somehow, maybe? Any help would be much appreciated ... losing this Mac would be a real drag for me right now.

---

### Post by erkki70 on 2005-03-29
Hi,
You're refering to this [http://www.yellowdoglinux.com/support/solutions/ydl_3.0/dual-drive-fix.shtml]("http://www.yellowdoglinux.com/support/solutions/ydl_3.0/dual-drive-fix.shtml")
and the modified Pdisk aren't accessible (You don't have permission to access /~dburcaw/pdisk_OSX.gz on this server.) :( too bad.

However, what about trying maybe mac-fsdisk to see if you can change the type correctly from there.
If you cannot change it, why not consider trying to create a new partition with the right settings?
Have a look to this thread:
[http://groups.google.fi/groups?hl=fi&lr=&client=firefox-a&rls=org.mozilla:frofficial&threadm=bbiesb%2441g%241%40geraldo.cc.utexas.edu&rnum=1&prev=/groups%3Fq%3Dapple_bootstrap%2Bapple_partition_map%26hl%3Dfi%26lr%3D%26client%3Dfirefox-a%26rls%3Dorg.mozilla:frofficial%26selm%3Dbbiesb%252441g%25241%2540geraldo.cc.utexas.edu%26rnum%3D1]("http://groups.google.fi/groups?hl=fi&lr=&client=firefox-a&rls=org.mozilla:fr:official&threadm=bbiesb%2441g%241%40geraldo.cc.utexas.edu&rnum=1&prev=/groups%3Fq%3Dapple_bootstrap%2Bapple_partition_map%26hl%3Dfi%26lr%3D%26client%3Dfirefox-a%26rls%3Dorg.mozilla:fr:official%26selm%3Dbbiesb%252441g%25241%2540geraldo.cc.utexas.edu%26rnum%3D1")

In case you cannot do anything, looks like you'll have to ask Dan Burcaw from Terrasoft to send you the modified pdisk files...

Good luck.

---

### Post by tater on 2005-03-29
Just wondering, did you read this?

[http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-powerpc/current/doc/manual/en/ch07s01.html](http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-powerpc/current/doc/manual/en/ch07s01.html)

It talks about holding down the option key while booting and other ideas for getting your G4 to boot.  Of course, this was written for warty, but it may give you some clues.

I did some hunting for that pdisk utility for you, and so far, can't find it either.

Good luck,
tater

---

### Post by PCM2 on 2005-03-29
OK, I went to bed, woke up this morning and realized what I had to do. So I'm replying here for it to be archived for anyone else who might have the same problem.

I had to erase my partition table and rebuild it from scratch.

NO WARRANTY EXPRESSED OR IMPLIED! Here's what I did:

1. Boot up something in single-user mode and get a copy of fdisk, mac-fdisk or pdisk running on the affected drive. Whatever it's called, it should be an fdisk-like program that understands Apple partition tables. Even though parted doesn't work, fdisk type utiltities should still see all the partitions, just as they were before. Print out the partition map of the drive. You should see that the first partition is of type "Apple_Bootstrap" when it should be "Apple_partition_map."

2. WRITE DOWN EVERYTHING YOU SEE. Make four columns: Starting block, length in blocks, partition name, partition type. Include everything, even the partitions marked "Apple_Driver_ATA" and the like. DON'T MAKE MISTAKES. If you mess up, your drive could be done for.

3. Type "i" to initialize the partition map. That's right, erase it. Remember, even at this point, you're still safe -- until you write the partition map to disk, nothing has changed. So erase it.

4. By now you should be very afraid. If you don't feel like you know what you're doing, back out and try to find another option (be sure to quit fdisk without writing the partition table!) But to see where this is heading, print the partition map again. You should now see a first partition with the correct "Apple_partition_map" type, and nothing else.

5. Now, recreate your partition map by hand. Press "C" (capital C) to create new partitions, one by one, filling in the information you wrote down earlier. If partition names or types have spaces in them (like the "Apple patches" partition), put them in quotes. Again, DO NOT MAKE MISTAKES. 

6. Print the partition map again and double check. Go through and verify all the numbers with what you have on paper. Try to remember if the partition map you saw before you started the process looked exactly like this one.  Remember, you haven't actually change anything on disk yet, so THIS IS YOUR LAST CHANCE. 

7. Hit "w" to save the partition map. It should tell you it was successful. If it doesn't, you're probably seriously out of luck.

8. Hit the reset button on the front of your Mac. Best not to beat around the bush; you don't want to risk anything writing to the disk while the partition map is in this state. So just cold boot. 

9. Now cross your fingers. You've changed your partition map, but you haven't actually modified the data on the disk. If you specified the same start block and length for every partition, then the contents of each partition should fit just perfectly, just like they were before. So after a while, the machine should boot right into your old Mac OS partition, as if nothing ever happened. It's probably advisable to run Disk Utility on the partitions to make sure they're sane, but otherwise you should be ready to screw it all up again the next time you try it! :-)

Hope this is helpful to someone. It was sure a relief when it worked for me this morning.

Best,
Neil

---

### Post by erkki70 on 2005-03-30
Hi Neil,

Great to know that you could get it back up and running :wink: 
Would you mind telling wich tool did you use to create the Apple_partition_map partition? Is it Pdisk, Fdisk, mac-fdisk?
Did you really have to recreate the whole partition table? Wasn't it possible to just operate on the faulty Apple_bootstrap partition, erase it and recreate a good Apple_partition_map?
It would definitely reduce risks messing up the table...

Anyway, great that you could recover!
Take care,

Erkki

---

### Post by tater on 2005-03-30
Absolutely FANTASTIC news!!  =D>   When I started reading it, I thought you were going to say that you had to completely start from scratch, reformat, rebuild.  Way to go!

tater

---

### Post by PCM2 on 2005-04-01
[QUOTE=erkki70]Hi Neil,

Great to know that you could get it back up and running :wink: 
Would you mind telling wich tool did you use to create the Apple_partition_map partition? Is it Pdisk, Fdisk, mac-fdisk?
Did you really have to recreate the whole partition table? Wasn't it possible to just operate on the faulty Apple_bootstrap partition, erase it and recreate a good Apple_partition_map?
It would definitely reduce risks messing up the table...

Anyway, great that you could recover!
Take care,

Erkki[/QUOTE]
 erkki70, I don't think it should matter which utiltiy you use of the ones you list. All of them use pretty much the same key commands. If it's built with Macs in mind, it should recognize the Apple partition table format. If it isn't, you won't see the partitions you were expecting to see. I think the actual one I used was fdisk from the Ubuntu install (though I think that might really be a symlink to mac-fdisk).

As far as just erasing the Apple_Bootstrap partition and recreating it as Apple_partition_map, nope! That will not work. None of the partition programs will let you create a partition with type Apple_partition_map. The only way to make one is to initialize the partition map, in which case the software will create a fresh one for your automatically.

For a while, the folks who put out Yellow Dog Linux posted links to a hacked copy of pdisk that would let you create the Apple_partition_map partition type, but those links seem to be dead now.

---

### Post by erkki70 on 2005-04-02
[QUOTE=PCM2]erkki70, I don't think it should matter which utiltiy you use of the ones you list. All of them use pretty much the same key commands. If it's built with Macs in mind, it should recognize the Apple partition table format. If it isn't, you won't see the partitions you were expecting to see. I think the actual one I used was fdisk from the Ubuntu install (though I think that might really be a symlink to mac-fdisk).

As far as just erasing the Apple_Bootstrap partition and recreating it as Apple_partition_map, nope! That will not work. None of the partition programs will let you create a partition with type Apple_partition_map. The only way to make one is to initialize the partition map, in which case the software will create a fresh one for your automatically.

For a while, the folks who put out Yellow Dog Linux posted links to a hacked copy of pdisk that would let you create the Apple_partition_map partition type, but those links seem to be dead now.[/QUOTE]

Thank you very much Neil for those precious details! :D
Again a time saver and precise how-to in order to recover from that kind of "big" problem...
Cheers,

Erkki

---

