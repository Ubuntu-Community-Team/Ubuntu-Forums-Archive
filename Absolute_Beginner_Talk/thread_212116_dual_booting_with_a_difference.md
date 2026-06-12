---
title: "dual booting with a difference"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by rightsaidfred on 2006-07-09
Hi to you all. I would like to dual boot Dapper and Simply Mepis.I have a primary hard drive with dapper on it and a secondary with mepis on.When I set the BIOS to boot from the primary dapper loads ok no problem.When Iset the BIOS to load from the secondary Mepis starts to load as if normally ie I see the mepis files loading, but after a little while it goes into the dapper desktop which then freezes, no mouse activity etc.
I  am doing it this way because I have not mastered dual booting on the same hdrive!!! What is going wrong?Thanks.Just as an afterthought, when I installed the O/systems I used the hdrives as single master ones and then put them both on the system as master and slave.

---

### Post by steve.horsley on 2006-07-09
I think the problem is that Mepis was installed thinking it was on hda, and so during boot it tries to continue loading from hda which now contains Dapper. Boom!

You _might_ be able to fix this by mounting the mepis drive and editing its /etc/fstab to mount hdb rather than hda. If this works, you might be able to add mepis to the Dapper boot menu by looking in mepis's /boot/grub/menu.lst and copying its boot stanzas, adding them to /boot/grub/menu.lst in Dapper.

---

