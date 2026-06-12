---
title: "HD Partitioning with Dapper installed and XP going into new partition"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by john wagner on 2007-06-01
**Yes, that's what I said....**  I'm a newbie, big time.  I replaced my OS with Dapper a week ago and are/am very happy.  My question is, **How do I partition the HD (since it's formatted for Ubuntu) to accept  XP?**   Ah, why?  WTF!?!  I can hear you all now...heh...  Well I have 1500 ebooks and various other items that require the Windows OS.  Until I eventually translate everything over.  Until then, i NEED some Windows to do my stuff.  Sigh.
I've been to [**_Installing a Dual-Boot with Windows and Ubuntu_** ]("http://http://www.psychocats.net/ubuntu/installing#booting").  Will it work fine going backwards?  Sticking XP onto a smaller partition(160 gig HD, figure 100gig for Dapper, 55 gig for XP and ballance for Swap).  And the drive is a new one (replacement for defective one), less than 1.5 weeks old, defragging is not required.  I formatted the whole thing with Dapper, it's never had Windoze on it.  Till now, sigh...or until it partition it!
Thanks, in advance...
john

---

### Post by Zzl1xndd on 2007-06-01
It will work but you will need to partition the hard drive first with Gparted or a like program as Windows can not do this on its own, Also you will need to reinstall Grub, as windows will write over your MBR.

---

### Post by bobplano on 2007-06-01
it will work, but you'll need to put grub back on the mbr or you won't be able to get to ubuntu. i need to learn how to do that too so you can look for it or someone else can tell us both

---

### Post by john wagner on 2007-06-01
> **tweakedenigma said:**
> It will work but you will need to partition the hard drive first with Gparted or a like program as Windows can not do this on its own, Also you will need to reinstall Grub, as windows will write over your MBR.

Cool, thanks.  So I just go ahead, set up all my parameters using Gparted via Dapper, then after the (yechh) XP install, go back and reinstall Grub.  Done deal.  Thanks.  Altho I have to say my soul is cringing at the thought of inflicting XP on the virginal HD.  Don't really want to do it....  Besides Wine/Codeweaver (which isn't perfect or total in translation coverage), is there any other equivalent translaters/emulators?  Decent ones?  Or is the Wine/Codeweaver it?

john

---

