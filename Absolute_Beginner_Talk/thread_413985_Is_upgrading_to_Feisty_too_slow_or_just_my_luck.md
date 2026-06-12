---
title: "Is upgrading to Feisty too slow or just my luck?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by emrextreme on 2007-04-19
Why is upgrading too slow? 
I have 1mbps connection but i can't upgrade even with 1kb/s.

---

### Post by Cypher on 2007-04-19
The sheer number of people that are probably hitting the server might be overwhelming things. Maybe you can wait a little bit?

Regards

---

### Post by gmc on 2007-04-19
> **emrextreme said:**
> Why is upgradng too slow? 
I have 1mbit connection but i can't upgrade even with 1kb/s.

You and about a million other people too... The Ubuntu servers are being hammered by everyone trying to upgrade at the same time. Just be patient or try again later.

Gord

---

### Post by juanhunglow on 2007-04-19
> **Cypher said:**
> The sheer number of people that are probably hitting the server might be overwhelming things. Maybe you can wait a little bit?

Regards

If you want to go with the .iso live/alt CD route, the torrent stream is a river... i.e. fast.

---

### Post by Campingman on 2007-04-19
Slow with me too, I installed by CD, updated OK.  When I tried to update repositories it was just sitting on connecting to archive.ubuntu.com.  Could not install any packages with terminal.
I had problems with video playback too.  Decided life was just too short and have reverted back to my edgy partimage backup.  Will try again in a few weeks when hopefully things will have quietened down a bit.

---

### Post by kittyhawk63 on 2007-04-19
Ain't nothing different about this then the day before Christmas. 

I always wait till one week after New Years.

Such peace and quiet!

I will wait for this to settle down as well.

I like peace and quiet.
kh

---

### Post by guillepb on 2007-04-19
Hmmm, ok, can I safely cancel the upgrade even if it's started already? I'm afraid I'm going to screw my edgy installation if I do... :-(

---

### Post by emrextreme on 2007-04-19
> **guillepb said:**
> Hmmm, ok, can I safely cancel the upgrade even if it's started already? I'm afraid I'm going to screw my edgy installation if I do... :-(

No harm will be done. You can safely call off the upgrade process.

---

### Post by FuriousLettuce on 2007-04-19
Hah! For once I'm glad I live in England. I upgraded within five minutes of it going live, and was getting ~150KB/s! Still took best part of two hours though, and it had to download 710MB of archives, which is larger than the install iso, so that was fun :|

---

### Post by guillepb on 2007-04-19
I know I could kill the process from a terminal window, but it's just that the "close" options are all grayed out on the upgrade window, so I'm feeling pretty weird about killing it...

(I'm still on the first phase of it, still "modifying the software channels" and all, no new packages have been downloaded yet)

---

### Post by PhoenixP3K on 2007-04-19
The servers are being stressed to their limit and on sevral occasions today they were out. Here is a working mirror. Use BitTorrent as much as possible! [http://mirrors.csumb.edu/ubuntu/feisty/](http://mirrors.csumb.edu/ubuntu/feisty/)

---

### Post by juanhunglow on 2007-04-19
> **guillepb said:**
> I know I could kill the process from a terminal window, but it's just that the "close" options are all grayed out on the upgrade window, so I'm feeling pretty weird about killing it...

(I'm still on the first phase of it, still "modifying the software channels" and all, no new packages have been downloaded yet)

'pretend' you had a power failure.

---

### Post by guillepb on 2007-04-19
I'll make it look like an accident ;-)

Thanks for your help.

---

### Post by rsambuca on 2007-04-19
You can always do an upgrade from the alternate CD.  It just took me 41min, 36 sec to download it via torrents.

The Kubuntu iso took a little longer - 1hr, 6min. 

I will continue to seed...

---

### Post by guillepb on 2007-04-19
Ok, I just restarted and I think my sources.list is filled with feisty repos and suggesting upgrades that won't work unless I upgrade to feisty, but I can live with that, I'm planning on upgrading as soon as possible. Other than that, everything seems to be working perfectly.

---

### Post by kittyhawk63 on 2007-04-19
> **juanhunglow said:**
> 'pretend' you had a power failure.

I did have a power failure the other day when I accidentally hit my keyboard up against the turn off switch on my surge power controller. I was in the early stages of doing a defrag on WinXP. Messed up everything including my hard drive. I couldn't reboot and couldn't reinstall. I have tried to fdisk the drive without success. I've used the disk that came with the drive without success. I lost the main partition and was left with only 7.9 GB of an 80 GB hard drive to use. Like I said, it really messed up my hard drive. This weekend I will be buying another hard drive unless someone here knows how to fix my problem. Open to any suggestions.
I am glad that I have another hard drive with Edgy installed. Edgy is my main OS. I use WinXP to do editing for authors using Word.
Any suggestions on how I might be able to restore this old 80GB hard drive again would be greatly appreciated. 
kh

---

### Post by juanhunglow on 2007-04-19
> **kittyhawk63 said:**
> I did have a power failure the other day when I accidentally hit my keyboard up against the turn off switch on my surge power controller. I was in the early stages of doing a defrag on WinXP. Messed up everything including my hard drive. I couldn't reboot and couldn't reinstall. I have tried to fdisk the drive without success. I've used the disk that came with the drive without success. I lost the main partition and was left with only 7.9 GB of an 80 GB hard drive to use. Like I said, it really messed up my hard drive. This weekend I will be buying another hard drive unless someone here knows how to fix my problem. Open to any suggestions.
I am glad that I have another hard drive with Edgy installed. Edgy is my main OS. I use WinXP to do editing for authors using Word.
Any suggestions on how I might be able to restore this old 80GB hard drive again would be greatly appreciated. 
kh

You can't get any of your data when you mount the windows drive from ubuntu??

---

### Post by kittyhawk63 on 2007-04-19
> **juanhunglow said:**
> You can't get any of your data when you mount the windows drive from ubuntu??

I have removed the Linux hard drive from the computer and set my WinXP drive as master and still can't get it to boot or any of the other things I have mentioned. I used Fdisk and formatted the drive. Nothing but 7.9 GB of hard drive is partitioned for use. It still sees it as an 80GB HDD.

---

### Post by juanhunglow on 2007-04-20
> **kittyhawk63 said:**
> I have removed the Linux hard drive from the computer and set my WinXP drive as master and still can't get it to boot or any of the other things I have mentioned. I used Fdisk and formatted the drive. Nothing but 7.9 GB of hard drive is partitioned for use. It still sees it as an 80GB HDD.

If you can boot with ubuntu live CD or mount from your Ubuntu install you could try the ntfs tools.  At the very least you could try to save any data, unless you were smart and it's already backed up.  NTFS-3g works for me in Feisty and it can be found in synaptic.

Finally, you could try a gparted cd, or from Ubuntu, and if you don't need anything off the drive, reformat NTFS.

It sounds like you may have lost a partition.  There are utilites to recover those.  Search synaptic for the ntfs tools, and testdisk, that might be what your looking for.

Best option....  Leave XP off your machine and just run Ubuntu..... !!!!

EDIT: If you want to have some more fun also check out 'foremost' in the repos

---

### Post by kittyhawk63 on 2007-04-20
> **juanhunglow said:**
> If you can boot with ubuntu live CD or mount from your Ubuntu install you could try the ntfs tools.  At the very least you could try to save any data, unless you were smart and it's already backed up.  NTFS-3g works for me in Feisty and it can be found in synaptic.

Finally, you could try a gparted cd, or from Ubuntu, and if you don't need anything off the drive, reformat NTFS.

[B] I can't burn the gparted iso. No CD-RW. It got burned with the power failure. Can I reformat the Windows hard drive from the Linux hard drive?
[/B] 
It sounds like you may have lost a partition.  There are utilites to recover those.  Search synaptic for the ntfs tools, and testdisk, that might be what your looking for.

**Can I use these from the Linux hard drive to fix the Windows hard drive? Doesn't seem feasible. **

Best option....  Leave XP off your machine and just run Ubuntu..... !!!!

[B]I have to have Windows to do editing for authors using Word. Special formatting that is not available in OO.
[/B] 
EDIT: If you want to have some more fun also check out 'foremost' in the repos[B]
Thanks
kh[/B]

---

### Post by kittyhawk63 on 2007-04-20
I'm moving this discussion to a new posts so others can get in on this. The Title doesn't help others to see my post. See you on the other side.

---

### Post by juanhunglow on 2007-04-20
> **kittyhawk63 said:**
> I'm moving this discussion to a new posts so others can get in on this. The Title doesn't help others to see my post. See you on the other side.

Let us know where the new thread is.

To answer your Q's from a prior post, yes, you can mount the windows drive while in your Ubuntu install and use the tools (actually, most of the tools get used on an unmounted drive) so it has to be that way.   That is why I use the live CD a lot of times when I'm doing diagnosis of problems on NTFS drives.

---

