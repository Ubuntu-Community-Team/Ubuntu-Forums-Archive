---
title: "Cant boot to windows, Disk read error"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Ragnarok0mega on 2008-02-17
Hey everyone, i read through a bunch of posts, and tried different solutions but none of them worked for me... I just installed ubuntu on a smaller disk, and wanted to resize my 160GB disk that my windows is on so i can move files from windows to linux so i can stop using that god forsaken OS. But as i tried with gparted it told me i needed to shutdown windows properly before i could resize it....but every time i try to boot to windows i get Error 25: Disk read error... ive tried rebuilding the boot sector, checked that grub was set up correctly....can anyone give me some other ideas?

---

### Post by njparton on 2008-02-18
You've somehow damaged your MBR or some windows start up files.

Boot from your windows CD into repair mode and then try and repair the installation from there.  Google for commands you can run when at the windows repair mode command line first.

---

### Post by jan quark on 2008-02-18
you can also use the
[URL="http://supergrub.forjamari.linex.org/?section=home#features"]
super grub disc[/URL]

to restore your windows mbr

---

### Post by Cochise on 2008-02-18
boot from the windows disc,
press r for recovery when prompted
choose your windows install
at the prompt then type: fixboot
at the prompt again type: fixmbr
reboot

[COLOR="Red"]**YOU WILL NEED TO RE-INSTALL GRUB AFTER THIS**[/COLOR]

---

### Post by geo909 on 2008-02-18
I had a similar problem recently. Seems that gparted may be harmful for editing such partitions..

Well, if you manage to restore windows' MBR and you have to restore GRUB afterwards, you may find this one useful:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by masque7 on 2008-02-18
if you have damanged your mbr you could try booting from your windows disc, selecting the recovery console option, and entering "fixmbr"

that's worked for me in the past before with a similiar problem

---

