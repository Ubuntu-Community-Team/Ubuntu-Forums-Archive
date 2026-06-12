---
title: "No original XP disc available - can I make one?"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by subseashaun on 2007-02-14
Hi all.

I am currently preparing to start using Ubuntu for the first time (since last using a unix type OS some 18 years ago!). At some point I will need a copy of XP to either run virtually or to re-load (as my HD is not partitioned) as I will need to continue using some MS Office programmes. However the laptop was pre-loaded with XP when I bought it new and all I have is a Windoze Works utility disc and the 3 back up CDs I was ordered to make before doing anything else. Am I right to assume the 3 back up discs will contain the whole XP operating system and I can use these to reload? All my data is backed up on a different external HD which I have already partitioned up.

Shaun.

---

### Post by charles.g.moore on 2007-02-14
I'm not sure about installing from backup disks through vmware, but as far as your office programs OpenOffice can export all of your files in windows formats eg. .doc 

I've heard that sometimes things don't exactly line up but i've never encountered that.

---

### Post by oilchangeguy on 2007-02-14
yes the restore discs you were prompted to make will return your computer to the day when you unpacked it from the box. and depending on your machines maker there may be a partition on the harddrive with the same material that you burned to disc. check your owners manual on how to restore your computer.

---

### Post by rsambuca on 2007-02-14
Yeah, the restore disks will return your computer to the way it was when you first purchased it.  Restoration from these is very simple, but depending on how long ago you got your computer, you may have a ton of MS updates to install.

You can not use the restoration disks to install XP in a virtual environment as there isn't a real installer on the disks.

If MS Office is the only thing you need, you will probably be able to wipe XP anyways, as OpenOffice is virtually 100% compatible, and comes pre-installed with ubuntu.

---

### Post by MCSE_Crossover on 2007-02-14
> **oilchangeguy said:**
> yes the restore discs you were prompted to make will return your computer to the day when you unpacked it from the box. and depending on your machines maker there may be a partition on the harddrive with the same material that you burned to disc. check your owners manual on how to restore your computer.

Sometimes though, the restore discs will format and reparition your drive to the original specs, thus, removing your Linux installation. Another BS way that Microsoft and the vendors rip us off. You pay for the computer and the software, yet you don't get an official disc. You may be able to install a version of XP from the restore discs, and make an image of your XP installation through third part software (ie Symantec Ghost) and restore/load it through VMWare that way, but other then that, your out of luck unfortunately. Those restore discs are a bummer.

Any specific Office program you need that OpenOffice doesn't work with? The majority of them work (Excel, PowerPoint, Word). The only one that there really isn't an OpenOffice equivalant I think is Access, since that is somewhat database driven. Could be wrong though...

---

### Post by mcduck on 2007-02-14
If you have a valid license and registration key for Windows you can actually legally use any suitable install disk to do the install, just use the registration key you have.

Of course you could also call Microsoft or the computer's manufacutrer and ask for real installation disk, according to the license it should be provided with the registration code anyway.

I'm not sure what windows license says about virtual machines though, but I'd think that's fine as long s you don't have any other installation with the same registration key.

---

### Post by igknighted on 2007-02-14
> **mcduck said:**
> If you have a valid license and registration key for Windows you can actually legally use any suitable install disk to do the install, just use the registration key you have.

Of course you could also call Microsoft or the computer's manufacutrer and ask for real installation disk, according to the license it should be provided with the registration code anyway.

I'm not sure what windows license says about virtual machines though, but I'd think that's fine as long s you don't have any other installation with the same registration key.

Are you 100% sure of this?  I have been told by several IT guys that XP keys are tied to a specific disk.

---

### Post by MCSE_Crossover on 2007-02-14
> **igknighted said:**
> Are you 100% sure of this?  I have been told by several IT guys that XP keys are tied to a specific disk.

You are correct. There is a difference between OEM keys, commercial OTS keys, and volume license keys. They are not cross compatible.

---

### Post by gigaferz on 2007-02-14
Hi, well I have a theory It could help you, however I have not done it yet.

I use Bart PE to Repair windows installations (2000 & xp).

The way BartPE works is  , once you got it running , double click winnt.exe in windows  and it will reinstall the system.

[http://www.pcworld.com/article/id,122487-page,1/article.html](http://www.pcworld.com/article/id,122487-page,1/article.html)

Now my theory is this:
You copy the  i386 folder to a hard drive, then run bart pe and double click the winnt.exe

Because I also have those annoying 4 hours  restoration cds, i have 6!!! man talk about stealing. And on top of that winxp wont run if I upgrade my mobo.

---

### Post by oilchangeguy on 2007-02-14
> **mcduck said:**
> If you have a valid license and registration key for Windows you can actually legally use any suitable install disk to do the install, just use the registration key you have.

Of course you could also call Microsoft or the computer's manufacutrer and ask for real installation disk, according to the license it should be provided with the registration code anyway.

I'm not sure what windows license says about virtual machines though, but I'd think that's fine as long s you don't have any other installation with the same registration key.

microsoft is not going to provide an xp disc. the computer manuafactuer may if you complain enough. check with a friend to see if they have an xp disc (use your product key) or a computer shop may make you a copy (for a price) and you can use that. in virtual machines you install an os just as you normally would (xp one time only).

---

### Post by MCSE_Crossover on 2007-02-14
> **gigaferz said:**
> 
Now my theory is this:
You copy the  i386 folder to a hard drive, then run bart pe and double click the winnt.exe


I think that usually those restore discs are packaged in a way that you don't have direct access to the i386 folder - unless BartPE gives you that type of access...

---

### Post by gigaferz on 2007-02-14
No, he should make a back up copy of that i386 folder from his hard drive to a cd rom, then copy the folder to a partition or hard drive and go from there.
 
but keep in mind it is just a theory.

I have re installed windows 200 and xp that way, so I thought , it only needs the folder in the hard drive ready to execute winnt.exe, and it will go trough the process...

---

### Post by subseashaun on 2007-02-14
Crikey I had no idea I would get as much feed back - I thought my question was a bit of a doe-doe but there you go! As I bought the laptop at Dixons in the UK, the next time I am back there (in the UK, I live in Brazil) I will try and get a hold of a proper XP installation disk. I bought the thing about 18 months ago just as something to keep all my subsea junk on but I changed jobs recently and now it is my toolbox. This is why I wanted to get back to a unix type OS as although its been many years since I used it, just looking through the threads a lot of the syntax I see I still remember - some things don't change much, especially a good idea!

My intention is to run the Ubunto OS for a while on a separate partition and see how I get on running the MS stuff I need using wine, then when I am happy, bin the XP OS. But as my HD is only partitioned for the XP OS and it's obligatory 4GB recovery partition at some point I will need to wipe the whole of the HD and start from scratch.

Looking through some of the posts regarding installation I did see that the Ubuntu package has a utility to do this, i.e. shrink the XP partition and leave enough space to install the new OS. Otherwise I am stuck with running it from the CD, or from the external HD but then I will need another power source for that (320 GB Iomega HD). However I also saw that shrinking a partition is not without it's problems hence the need for a means to re-load XP.

Thanks again for the feedback.
Later Dudes.

Shaun
(Subsea Engineers do it deeper and under pressure!)

---

### Post by RanDinCarolina on 2007-02-14
I am soooo glad I have my own XP Corporate license................:lolflag:

---

### Post by MCSE_Crossover on 2007-02-15
> **subseashaun said:**
> Looking through some of the posts regarding installation I did see that the Ubuntu package has a utility to do this, i.e. shrink the XP partition and leave enough space to install the new OS. Otherwise I am stuck with running it from the CD, or from the external HD but then I will need another power source for that (320 GB Iomega HD). However I also saw that shrinking a partition is not without it's problems hence the need for a means to re-load XP.


The Ubuntu installer will automatically shrink your Windows partition for you when you go through the install! Another added bonus!

---

