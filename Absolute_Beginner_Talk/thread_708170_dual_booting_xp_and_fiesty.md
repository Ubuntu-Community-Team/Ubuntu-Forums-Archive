---
title: "dual booting xp and fiesty"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by umarali on 2008-02-26
hi, i installed xp on my pc a long long while ago and just a few months ago i bought a 10gb HD and installed ubuntu on it. i.e i had both xp and ubuntu installed on my same pc  but on different HDs...dual booted perfectly...no trouble at all. last month of so i upgraded to fiesty and still no probs.
HOWEVER... last week my pc just totally crashed and wouldnt boot at all...it gives a error " error 17, grub error" or summin..
i tried booting from the other HD  => "error loading operating system"
:confused: :confused:
so, i installed xp again and found out, while installing it,  that the root partitions of both the drives were shown as an "unrecognized" format ...???
anyways it installed and works ok...
i tried dual booting again; installed fiesty (from the live cd) and it was working fine for half an hour or so..then again...IT CRASHED!!!!
same thing!!
got back xp from the "recovery mode" or whatever
but my question being...WHY THE HELL DOES IT KEEP CRASHING WHEN I TRY DUAL BOOTING???? AND WHY DIDNT IT CRASH BEFORE??

---

### Post by bwallum on 2008-02-26
Hi

I am not sure what your problem is but it may be useful to have a look through the [GRUB manual]("http://www.gnu.org/software/grub/manual/html_node/")

Error 17 is Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

It looks as though the Master Boot Record has been clobbered. This could be a virus (Windows), If you have completely reinstalled (always install Windows first then Ubuntu) you may be able to rule this out. If you used a live Ubuntu CD you can boot up on that (check that the CDROM is bootable before the harddrive - edit the cmos when you switch on, usually by pressing del or F2 or F10). You will then be able to see your files and check the partitions using gparted System>Administration>Partition Editor.

---

### Post by mwanstall on 2008-02-26
It could be that the HDD that Ubuntu was loaded on died...that would explain the boot loader and why the windows partition still worked after its MBR was rebuilt.

A 10gig HDD, assuming its old from the size. It might have bitten the bullet and have bad sectors. Try installing a SINGLE OS just on that HD without the other connected and see if you can get that to work or try using some scanning tools on the drive to check if it's okay.

---

