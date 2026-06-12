---
title: "MacBook Air cannot boot"
date: 2012-12-28
forum: Apple Hardware Users
---

### Post by JiuJitsu500 on 2012-12-28
Okay, so here I am. I've dealt with a million problems with Windows, Linux, and Mac so much worse than this it's almost embarrassing to be stuck on something so... ummm... well, never mind it's apple. Bastards.

Anywho, my rant is for another time and place, here's my problem. I hate Apple for a hundred reasons, and I got another one today. Basically, I can't boot into the damn installer.

I have the latest and greatest version of the Quantal Installer (with mac jazz - ubuntu-12.10-desktop-amd64+mac.iso from whatever site hosts it). I also bought my girlfriend a Macbook Air a year ago for X-mas, model is mid-2011, 4.1, core i5. I'm pretty sure this model was the first to have a 64-bit processor, so I'm not looking stupid here just yet.

So, the nitty gritty now. Snow leopard, Lion, three different puppy linux's, FreeBSD 9.1, XP Vienna, and Windows 8 all virtualized with full R/W access to almost anything, including shared files and USB - the OS X's can even do NTFS with ease. One SSD has Precise, the other has Windows 7. This all matters because no matter which one of these I use to create a bootable USB, it does NOT BOOT on the mid-2011 Air. In various tutorials that all say exactly the same thing, and my own know-how, there is not a damn thing stopping me from doing this. But, apparently I am very wrong.

I have rEFIt installed and working flawlessly, with all MBR's synced. I used Mac's own Disk Utility to make the DOS (FAT of course) partition for Ubuntu as every tutorial says, nothing in this part is the problem from anything I can tell. The mac is fine, rEFIT (v .14) is fine (also tried three older versions, and two other EFI tweakers).... and the partition is fine. I also hate to admit that, given how slow and horrible OS X is at handling jobs linux and even windows does in literally seconds.

So, I figured it was the USB stick, and once I tried it all on four thumb drives, I can safely say it's not that either, since all four boot up in a virtual machine and on two different real machines. Yes, I've created these things more than 30 times, with dd on mac, BSD, and linux and unetbootin on three windows' machines. With two different downloads of the same image from two hosts. I've used the .iso for dd against the rules, used an .img from conversion on linux and mac, and used the .dmg mac makes on it's own from conversion.

But, now... here's where I am. The disk was created successfully, and I can get rEFIT to see the blank "windows" partition I'll put ubuntu on, and I can hold alt/option to choose the USB drive... then I had a problem with it saying that there was no bootable media. I fixed that after trial and error like a boss by syncing the boot records with rEFIt's partition deal. BUT, now I'm at the point to where I get the same blank screen, saying "non-system disk" "press any key to reboot" and a total system freeze. I've googled, looked, and searched but haven't found anyone with that problem.

I have followed essentially this exact guide in every possible way on four different operating systems on three different computers in two different environments with four different thumb drives:

[http://ubuntuxtreme.com/howto/how-to-install-ubuntu-12-10-in-macbook-air-2011-mid/](http://ubuntuxtreme.com/howto/how-to-install-ubuntu-12-10-in-macbook-air-2011-mid/)

I've ran the script he has in Puppy, BSD, and Ubuntu to create it, ran the commands all manually in terminal and through GUI, followed the /rdisk1 vs /disk1 for mac (as well as use the iso, dmg, and img), tried two other EFI loaders, have a 20GB partition specially made, and have tried booting this thing at least 30 times total now. I haven't exactly exhausted every single possible way to do this, but COME ON!!!! Mac can't do it, Linux hasn't been up to it, and even the odd Berkley Distro can't do it. So, unix and unix-like/unix-similar are not working... and even Winodws XP, 7, and 8 have failed...

Is there something I'm missing here? Or did I overlook some very serious information? Again, after holding ALT and choosing the USB, I get:

non-system disk
press any key to reboot

But then a blinking cursor, and no key works to reboot. I have to hold the power button to turn it off. But, at least now I'm past the original "non-bootable" crap... From what I can gather, this problem is the rEFIT attempting, ironically, to boot the USB in BIOS mode, or as a BIOS... but I don't understnd that too much. EFI and BIOS are different, but no matter what way I create the USB, the same error occurs (from file copy and syslinux as root in nautilus to dd in BSD and Mac... or UNetBootIn in windows... anything).

I'll buy you a unicorn if you can tell me what I'm doing wrong.

---

### Post by tgalati4 on 2012-12-28
Take it to the genius bar? (as I duck.)

I would run the Apple Disk Utility and check all of the partitions for integrity.  Perhaps there is a BIOS enumeration issue because of partition table errors.  It sounds like your situation is an edge case.

---

### Post by JiuJitsu500 on 2012-12-28
The genuis bar!!! EL OH EL I nearly forgot about them!!!! :) That's why I prefer the Ubuntu Geniuses here! I rarely consult you guys anymore actually... hmmm... seems almost like I fell off of my own bandwagon.

Great response actually, I kind of wonder if the coders after wozniak did want EFI over BIOS for some reason to do with making it harder to run other-than-apple-endorsed stuff... Like what Microsoft is attempting recently with BIOS locks and crazy firmware codes. Resistance is futile Geniuses!

I ran GPT on both partitions, and made the USB a couple more times again... still no luck...

Oh, maybe I should note as well that like many others I get the same message error when the dd is finished in Mac, and it doesn't seem like any OS can read it once it's done. GParted says all but the used 792MB or so is unallocated, which is fine. The flags on it are still boot and lba, which is also fine. BUT, the used space is in a format nothing can see. The Disk Utility can't verify the disk or any partition since it can't mount the damn thing.

People were saying this is normal, and it booted for them when they chose the USB in the EFI menu. So, I can't really check it in any OS, unlike a boss... but I'll keep looking for an answer.

Maybe something in the MAc is telling it to do something it can't? I need a rEFIT log or something...

Thanks for the response!

---

### Post by tgalati4 on 2012-12-31
I would try different size and different manufacture USB drives.  It could be that the dd writes are failing because of a slow USB controller (on the flash drive itself).  Because of the minimalist design of flash drives, there is probably no feedback, like there would be with a real hard drive.  So a failed dd (because of a worn-out flash drive or a buffer overflow of the drive controller) would not give any indication of failure, other than the fact that you can't mount it because it is not recognized by the operating system.

So rather than a corporate master plan by Apple to make your life miserable, you might just have crappy USB drives.  There are a lot of fakes floating around.

A trip to the Genius Bar was simply for our entertainment.  I always like reading the transcripts from tech support.

---

### Post by JiuJitsu500 on 2012-12-31
So, there I was, nearly forgetting I posted here when I found the problem.

I picked up this thumb drive about 4 years ago in Kuwait and used it pretty heavily since. Being that it was 4GB at that time too, it was top of the line, like boss mode. I also in the following year or two, picked up a few more small drives on the way. I have like 12 of these damn things.

Oddly enough, by some strange karma or coincidence or some craziness... All of the drives I tried were in either bought Malaysia or Kuwait, one Might have been from Iraq. All of which are also my oldest ones, and all of which have had problems for quite some time, and all of which might have just been chinese knock-offs. Why on EARTH I hadn't seen this sooner is why I like to drink so much.

I almost went into some serious insanity as NOTHING online anywhere was what I was going through. I went to Best Buy the other day and found a bada$$ sale for thumb drives, and got a 2GB for like $3 (and 2 16GB crap ones for backup for $18 total... hell yeah).

Anyway, dork mode engaged, and FIRST TRY!!!!!!!!!! The new, cheap, 2GB drive worked flawlessly. Though I did still get the error that it couldn't be mounted anywhere (Linux recognized it, but said it was essentially corrupt, which was better than nothing and what was supposed to happen).

So, your theory was right. And that would have been hilarious to go to customer service. One thing I have my hats off to Apple though is their customer service (given all your papers are in order - so to speak). I wonder what they would have said if I told them I was attempting to put another OS on a Mac??? :popcorn:

Thanks again! That solved the problem, I'll mark the post shortly. Lesson here is: The Genius Bar is a crazy place for mostly die-hards who know very little, if anything, about computing... and that half-decade old and possibly fake thumb drives are only good for storing files as a last resort.

The damn thing couldn't even format right I found out too, the dd would appear to work, but a whole lot of bad sectors were just skipped or written directly over. Only a few bytes were missing in various places, but that's all it takes.

---

### Post by tgalati4 on 2013-01-01
Glad you got it worked out.  I would hate for you to have to throw out the MacBook because you couldn't put Ubuntu on it.

Lesson learned:  Not all flash drives are created equal, sometimes a burned CD or DVD works better.  DD is simply a dumb image writer.  No feedback, whatsoever.  Any disk errors are yours to keep.  The MacBook Air is a sealed gadget of Apple Goodness.  Any frustration must be taken to the Genius Bar, where your frustration will be multiplied.

---

