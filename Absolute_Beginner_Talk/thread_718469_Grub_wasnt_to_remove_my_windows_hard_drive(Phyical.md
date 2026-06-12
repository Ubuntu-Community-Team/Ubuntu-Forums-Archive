---
title: "Grub wasnt to remove my windows hard drive(Phyically)"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by drubin on 2008-03-08
Hi,

I have the following set up.  
1 SATA 320gig hard drive   windows (xp)
1 SATA 250gig hard drive   Ubuntu (7.10)

I have grub set up for the default boot being linux, Now in need to use that windows drive as in my external hard drive case to transfer some work to another computer. 

So here is the question, I am scared that taking out Hard drive (xp) -will mess up my grub?   Will it? Is it a bad idea to remove the hard  drive and then put it back in the computer? The main problem is i intend on putting it straight back in a day or 2, and haveing the set up be the same 

Thanks.(Hoping this wont break every thing)

---

### Post by forestpixie on 2008-03-08
Depends which is the master I think - if the xp drive is the master I don't think you'll have it working

If it's not the master it shouldn't mess up grub - if the hdd isn't there it just won't boot it if you try to, but as you know it's not there you won't try

---

### Post by drubin on 2008-03-08
Nah the Ubuntu one is set as the master in the BIOS,

and I wont be booting up in windows for  a while :). Just want to check that i will be able to when i deiced to put the drive back..

also the default boot drive is the ubuntu so if i dont select any thing it will boot in to Ubuntu. :)

---

### Post by mikeyphi on 2008-03-08
> **rubinboy said:**
> Nah the Ubuntu one is set as the master in the BIOS,

and I wont be booting up in windows for  a while :). Just want to check that i will be able to when i deiced to put the drive back..

also the default boot drive is the ubuntu so if i dont select any thing it will boot in to Ubuntu. :)

Master in BIOS is not the point!!
If you installed Ubuntu on a system that already had windows then the grub is (probably) on the windows partition. If you remove that drive you will probably not be able to boot your system. However, when you put the windows drive back in (assuming no software changes) all should be OK.

---

### Post by drubin on 2008-03-08
I Have 2 separate hard drives! not just 2 portions.

Grub is  on the Ubuntu drive,  (Because i had to change the primary drive to be Ubuntu in order for grub to even show up).

Thanks for the help.

---

### Post by forestpixie on 2008-03-08
disconnect the drive boot the pc - if it works all is ok - if it doesn't reconnect it

---

### Post by uberlube on 2008-03-08
Why not just comment out the windows drive in grub for the timebeing? Then once its back in uncomment.

---

### Post by Duck2006 on 2008-03-08
If the ubuntu drive is the master then it don't matter if your xp drive is in or out. It only matters if you want to boot xp from your grub menu. If you then want to add a xp drive then you have to edit your grub menu.lst so you can boot xp.

---

### Post by drubin on 2008-03-08
Thanks guys,

Well i have unpluged the drive, Ubuntu didn't die :).

Now all i have to do is see if it will all be the same when i put it back in again.  :).

Will let you know if it was all good, or how i had to fix it, (Just for any one else wanting to do the same thing).

---

