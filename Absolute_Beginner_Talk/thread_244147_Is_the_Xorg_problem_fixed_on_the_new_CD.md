---
title: "Is the Xorg problem fixed on the new CD?"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by nu2this on 2006-08-26
I did that xorg update that borked a lot of systems on Monday. When I tried to do the fixes recommended in this forum they didn't work.
The cause is largely due to my inexperince with linux,so I did the radical thing & completely restored my Dual Booted PC. My thinking was the Ubuntu team'd get it fixed in 2-3 days, Id reinstall My Ubnutu partition,read the how to fix, no problem. Buuuut! I lost my install CD 8-[ 
So my question is if I burned a new disk, does the Ubuntu CD available for d'ld now have the latest fix on the xorg? Or will I need to do them?

---

### Post by aysiu on 2006-08-26
No fixes are on the CD. The CD is the same CD that came out on June 1, 2006.

The fixes are online downloads, and the downloads are now fixed in the repositories.

---

### Post by confused57 on 2006-08-26
> **nu2this said:**
> I did that xorg update that borked a lot of systems on Monday. When I tried to do the fixes recommended in this forum they didn't work.
The cause is largely due to my inexperince with linux,so I did the radical thing & completely restored my Dual Booted PC. My thinking was the Ubuntu team'd get it fixed in 2-3 days, Id reinstall My Ubnutu partition,read the how to fix, no problem. Buuuut! I lost my install CD 8-[ 
So my question is if I burned a new disk, does the Ubuntu CD available for d'ld now have the latest fix on the xorg? Or will I need to do them?

Can you boot into Ubuntu at all, meaning to the error message about xserver?
If you can, press Ctrl+Alt+F1, which will get you to a console...login.
Then enter:
```
sudo apt-get update
sudo apt-get upgrade
```

Then ```
sudo reboot
```

If you don't have internet in Ubuntu, you can downgrade the xserver:

```
sudo dpkg -i /var/cache/apt/archives/xserver-xorg-core=1:1.0.2-0ubuntu10.deb
```

Edit: Misread your post, coffeecat's correct...

---

### Post by msak007 on 2006-08-26
> **aysiu said:**
> No fixes are on the CD. The CD is the same CD that came out on June 1, 2006.

The fixes are online downloads, and the downloads are now fixed in the repositories.

I think nu2this is referring to the 6.06.1 release update CDs that were just released a couple of weeks ago. Your answer is still valid as that broken update was released after the CD, but I believe that's what he was asking.

---

### Post by coffeecat on 2006-08-26
> **aysiu said:**
> No fixes are on the CD. The CD is the same CD that came out on June 1, 2006.

No fixes are on the CD, true, but the iso available now (at least on the UK mirror I checked) is the 6.06.1 version dated 6th August.

**nu2this**, don't worry about the update that caused all the problems. This has now been replaced on the mirrors by a working version. I have now updated two machines with different graphics chipsets to the new xserver-xorg-core and they're both working fine. I'm posting from one of them.

If you have to do a fresh install, get the new ISO. It will have all updates to the beginning of August. The xserver-xorg-core will be a version prior to the bad one. Then, when you update you'll get the later working version and you should be fine.

---

### Post by nu2this on 2006-08-26
> **msak007 said:**
> I think nu2this is referring to the 6.06.1 release update CDs that were just released a couple of weeks ago. Your answer is still valid as that broken update was released after the CD, but I believe that's what he was asking.
 Yes, that is also what I wanted to know in addition to whether or not the CD was affected(thanks Aysiu!),because the lost disc is from 6/7/06. I thought there was some sort of upgrade in between then & now meaning up from just 6.06, I did want to have the version I had,in this case 6.06.1 therein was the source of my confusion. Until today I thought that some updates(xorg in particular)were integral to certain versions.

---

### Post by msak007 on 2006-08-26
If you have the 6.06.1 CD, then you should be OK. As was previously stated, the 6.06.1 CD is a service update of all the updates after the initial release of Dapper. The xorg update that broke systems was installed through an update, but was subsequently fixed. So after the install, don't worry when it prompts you to update xorg as the broken version has already been fixed and it's safe to update.

---

### Post by nu2this on 2006-08-26
Thanks to all of you guys!
I'll learn Linux,Ubuntu in particular yet! Next stop a new install CD d'ld,burnt,re-installed,& better track kept of my new disk.

---

