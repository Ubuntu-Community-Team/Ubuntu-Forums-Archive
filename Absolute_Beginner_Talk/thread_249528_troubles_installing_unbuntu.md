---
title: "troubles installing unbuntu"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by baldheadedguy on 2006-09-02
Ok i tryed the OS on off the cd and desided to install it on an old computer. So i did and its not working, it seems to install well from start to finish. It is just when i go to boot off the hard drive it will not do anything. It just trys to load then it goes and says no operating system found. can any one help?

---

### Post by benfindlay on 2006-09-02
What spec is your "old computer"?

There is a good chance that if it is at, or around, ubuntu's minimum spec, then you will ahve problems using the live cd to install the OS. You're better off downloading the alternate cd and installing via a text based install. This is just as easy to do as the live cd install, it just doesn't look as good. Once it is instaled, however, it is exactly the same!

Another option would be to try xubuntu, as this uses a much lighter-weight GUI called XFCE, but it still looks impressive

Hope this helps!

---

### Post by jimmygoon on 2006-09-02
> **baldheadedguy said:**
> Ok i tryed the OS on off the cd and desided to install it on an old computer. So i did and its not working, it seems to install well from start to finish. It is just when i go to boot off the hard drive it will not do anything. It just trys to load then it goes and says no operating system found. can any one help?

is grub saying that?

I bet some how your HD isn't set active. You will need to fix that.

---

### Post by baldheadedguy on 2006-09-02
The computer is a pentium 3(600) with 256 of ram. Is that to low? 
jimmygoon! you could be right too i just bought a 150 gig hd for it. How do you set it active? As you can see i a little new to this so don't laugh to much. Or at least don't let know you are laughing at me.

---

### Post by taurus on 2006-09-02
The easiest way to go is to install GRUB on MBR (Master Boot Record)...

---

### Post by baldheadedguy on 2006-09-05
Ok, So i still need some help here. First where do i get GRUB and second how do i install it to the hard drive. Is there any one out there that can help this lack of knowlege guy?

---

### Post by Rizla on 2006-09-05
I *THINK* Grub usually gets installed to the master boot record of the disk you are installing ubuntu on.

---

### Post by taurus on 2006-09-05
> **baldheadedguy said:**
> Ok, So i still need some help here. First where do i get GRUB and second how do i install it to the hard drive. Is there any one out there that can help this lack of knowlege guy?
If you just follow the instructions on the screen, you will eventually come to a section about installing GRUB!  Make sure you have it install on MBR...

---

### Post by baldheadedguy on 2006-09-05
Ok so now that i have installed the os again. It nevered said anything about grub it just installed and that is it and when it reboots. I can see that it goes to the hard drive and then it say no operating system found. end of story. what gives. Am i stuck with windows for the rest of my life?

---

### Post by halitech on 2006-09-05
when you installed the 150 gig drive, did you make sure that the BIOS sees the drive? it could be that it's not seeing the drive so it's not installing anything which would give you a no OS found message.

---

### Post by baldheadedguy on 2006-09-06
OK,Ok, this is good I am starting to get somewhere. It was my fault i forgot to move a jumper on the hard disk. BUT now it says GRUB loading please wait. And under that is says Error 18. soooo now what is that, any one? I swear i am going to be computer geek by the end of the week:-D

---

### Post by xpod on 2006-09-06
> I swear i am going to be computer geek by the end of the week

LOL....Know exactly how you feel mate.I only sat down at the old used m.e we bought a few months back to play pacman with my kid`s.

NOW im sitting with multi pc`s with multi operating systems and a head full of the strangest stuff that seems to have brought quite a bit of pleasure.

Especially since the Ubu`s and Kubu`s appeared....The wifes starting to get worried me thinks.....(she`s sure this is some sleazy chatroom...lol)

EDIT: i just had to re-install xp to shut her up:( ...It`s not ALL fun

---

### Post by halitech on 2006-09-06
Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.


ok, guess I should hopefully try to make some sense of this. basically in a nutshell, when you put the 150gig drive in, your motherboard can't handle it so you may need to check and see if there is a firmware update for your board so you can use the drive (if there isn't one, I know a home that you can donate that drive to ;) )

---

### Post by baldheadedguy on 2006-09-07
boy just when i think that i am all set now i have more questions. Starting with partitioning i had to partition the drive so that the boot drive is 8 gigs(partition3) so it would boot. And the partition 1 is 9.20. The swap partition is 729.45 and there seemes to be two of them and then there is free space that is 213.82 gig. How do i use the rest of the hard drive? it will not allow me to use free space or i don't know how to use that free space. Please someone help me make sence of all this. Why do i need all of these partitions for any how.

---

### Post by halitech on 2006-09-07
you say the drive is 150gig but it is showing 213gig free? something isn't sounding right to me. If you go into the BIOS, does it show your drive installed as a 150 gig drive?

---

### Post by baldheadedguy on 2006-09-08
ahh, yes glad my head is attached. let me look at that hard drive. oh yes, it is a 250 gig drive. yep stupid me.

---

### Post by halitech on 2006-09-08
ok, think we are still at the same spot though, if you go into the BIOS, does it show that it is recognized by the computer?

---

### Post by CatKiller on 2006-09-10
> **baldheadedguy said:**
> Ok i tryed the OS on off the cd and desided to install it on an old computer. So i did and its not working, it seems to install well from start to finish. It is just when i go to boot off the hard drive it will not do anything. It just trys to load then it goes and says no operating system found. can any one help?

I know that this is probably too late for you, since you've already expressed your intent to migrate to a different operating system, but from the symptoms you've described it seems like the hard drive is too big for your motherboard.

Older motherboards will not work with very large hard drives without some updating. I believe that this limit is around 128 GB, although there are many different limits that have had to be overcome in the past. Google for "48-bit LBA" to find out some more on this issue.

There may be a BIOS update that will upgrade your motherboard to support drives larger than this. For very old boards, there probably won't be.

An alternative is simply to partition the drive differently. If you make sure that the first partition is smaller than 128 GB, the computer should boot OK. You might not be able to (reliably) use any space after the first 128 GB - it depends on the motherboard and hard drive.

It should be noted that any other operating system will have similar problems addressing this space since it is a hardware limitation rather than a software one.

Whichever operating system you decide to use, good luck. And if you persevere with Ubuntu, there are many people here that will try to help you out if you get stuck again.

---

