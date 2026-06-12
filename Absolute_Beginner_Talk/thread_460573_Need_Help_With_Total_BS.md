---
title: "Need Help With Total BS"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by drowner on 2007-05-31
where BS = Big Switch

I basically haven't booted into windows for 10 weeks. I don't think i'll miss the 2 games i had (havent played them for ages, and my comp was too slow for them anyway) and now, I want to reclaim the space ;), my linux partition is only 9 gig, and its getting full(ish). So, I want to make it bigger!

The windows partition is 14 gig, you see, or there abouts

HOw do I go about this?

I was thinking:

1. I have a DamnSmallLinux LiveCd, which i wouldn't mind using. I undestand it comes with parted, is this a text based partitioner? I would prefer to use gParted, but the Ubuntu liveCD is a bit slow for me. Anybody know any mini-linux live distros with a graphical partition tool?

2. So when I sort out those issues I will hose the XP partition, make sure that the / partition is not mounted, and then make it bigger. Will this confuse my ubuntu on reboot?

3. Which files need to be modfied? fstab, i presume. And menu.lst, right? should i backup and edit men.lst before restart? You, know will having an XP entry pointing to a non-existant partition confuse it?

Thanks in advnace, guys!

Regards, Drowner

---

### Post by drowner on 2007-05-31
Another thing: if i remove the windows partition, which i suppose grub thinks is number hd0,0, will the linux partition then become hd 0,0, and as such, will it cause grub not to boot?

Does this make any sense at all?

I know theres a myriad of problems here, but any help will be appreciated

---

### Post by gjtoth on 2007-05-31
Why not download and burn the GPartEd .iso?  Works fine for me.  I just got done doing a partition resize and it was effortless.

---

### Post by drowner on 2007-05-31
> **gjtoth said:**
> Why not download and burn the GPartEd .iso?  Works fine for me.  I just got done doing a partition resize and it was effortless.

Yep, the gParted cd seems the most appropriate.

Does anyone know about my other issues? IE editing the menu.lst, and whether removing the primary windows partition will send grub through the roof?

---

### Post by drowner on 2007-05-31
So i suppose the easiest option is to just back up my data reinstall fresh.

But i'm not sure i REALLY want to do that. I'd much rather delete the NTFS partition and resize the ext3 one.

BUt i have serious concerns that moving the / partition will cause grub to panic, cause it can't find menu.lst, and probably my fstab will poop its pants too, because the / mount point has changed.

Are my fears justified?

---

### Post by Shazaam on 2007-05-31
Just a SWAG but couldn't you use the old Windows partition for /home? I think this might help-- 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by drowner on 2007-05-31
I don't know if a seperate /hom partition is exactly what i am looking for. I actually want to resize my entire / partition, but i am scared that i will mess up my fstab and menu.lst

---

