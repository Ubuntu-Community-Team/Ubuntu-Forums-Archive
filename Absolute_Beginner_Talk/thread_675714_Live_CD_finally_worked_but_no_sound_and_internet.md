---
title: "Live CD finally worked but no sound and internet"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by _lik_ on 2008-01-23
Ubuntu Live Cd finally worked for me (in safe graphic mode) :-), but there was no sound and internet. So, is that how is supposed to be on Live CD (version 6.10 I think)?

I have HP laptop with vista installed, AMD64, 2 GB RAM,...

---

### Post by Mogurijin on 2008-01-23
First, I would recommend 7.10 since it does more stuff automatically. It might also have the right drivers for sound. If not, I'm not sure how to help you. However, in the wireless area I have more knowledge, or at least links :D. Check this out:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28wifi%29%7C%28support%29]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28wifi%29%7C%28support%29")

---

### Post by _lik_ on 2008-01-23
> **Mogurijin said:**
> First, I would recommend 7.10 since it does more stuff automatically. It might also have the right drivers for sound. If not, I'm not sure how to help you. However, in the wireless area I have more knowledge, or at least links :D. Check this out:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28wifi%29%7C%28support%29]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28wifi%29%7C%28support%29")

Hold on. When I download 7.10 I run it the same way I did with this one and then from the desktop I choose install. Am I right? Does 7.10 version have Live CD included or not?
I use cable internet

---

### Post by Mogurijin on 2008-01-23
7.10 does have a live Cd. In fact at least all of the current ones have Live CDs, and probably all of the new ones will too. It appears to be standard practice to have one... And yes, the installer should be similar. I haven't personally used any Ubuntu other than 7.04, but I've help someone setup a 7.10 install, and there was little difference. So yeah, just load the disk and click the install button.

---

### Post by _lik_ on 2008-01-23
Ok, but first I want to make sure that everything works before I permanentaly install it. If I mess up it would be tought because I am using the same laptop for trying the cd and to search the forum so I swithc back. 

can I see if Ubuntu works (just like I did with the Live CD) without installing it?

---

### Post by Mogurijin on 2008-01-23
Yes, the only difference is you'll be using an updated Live CD. Also, you can setup your laptop to dual-boot. That way you can play with Ubuntu (which is much faster off a hard drive) and restart into Windows if need be (to check forums and such until you can get an internet connection in Ubuntu).

---

### Post by _lik_ on 2008-01-23
> **Mogurijin said:**
> Yes, the only difference is you'll be using an updated Live CD. Also, you can setup your laptop to dual-boot. That way you can play with Ubuntu (which is much faster off a hard drive) and restart into Windows if need be (to check forums and such until you can get an internet connection in Ubuntu).

Ok, I will try that tomorrow, I don't have it downloaded yet and also I need to check the tutorials how to make both OSs to work at the same time. Thanks

---

### Post by Mogurijin on 2008-01-23
When searching around try using terms such as "dual-booting". Also, I can just give you a quick explanation.

Start with backing up any important data.
Run a defrag on hard drive (this can help the repartitioning later)
Restart your comp with your Live CD.
When Ubuntu is booted, go to Admin -> gparted (Or somewhere in that area)
Use gparted to resize your Windows partition
Give Ubuntu about 10gigs (good size for playing with....and pretty much using :D)
Set aside 512megs for a swap file (you might want more, but 512 was fine for me when I had only 1 gig of memory)
Save changes
Run through the install Wizard.
When you get to partitioning, use manual/advanced/whatever it is called
Find you 10gig Ubuntu partition, and go to properties (or, again, whatever it is called)
And set the mount point to "/" and the file system to ext3 (this is common and stable, you can try messing with Raiser, but I've only used ext3, so I don't know how good it works. There is a lot of discussion on the internet about filesystems if your interested, but ext3 will be fine for now)

Now go to the properties of your 512MB partition and set the file system to "Linux Swap" or something similar
Now, continue following the installation wizard to setup Ubuntu.
If you need help (and still don't have a working internet connection) simply reboot and select Windows when Grub shows up
You'll be using grub to switch OSes.

I hope that helped. Some areas are kind of gray since I haven't done an Ubuntu install in a while and I don't have Ubuntu installed on this comp....
Again, you might want to find a more thorough guide if you want more in depth info.

Good luck ;)

---

