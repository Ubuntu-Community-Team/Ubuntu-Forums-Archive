---
title: "CD Emulator for ubuntu"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by PoLiSonTe on 2006-11-21
Hey guys, 

I just have a noob question here, I'm wondering if there is a program like alcohol 120% (Cd emulator for iso/bin files) for ubuntu. I been doing some search but i haven't been able to find any that does the job. Any idea? ](*,)

---

### Post by kd7swh on 2006-11-21
gnome can mount iso files through the file browser (nautilus) by using freely available scripts. 

Sorry I don't have a link handy. google: nautilus scripts and you will find some neat stuff

or you could use the mount command from the terminal with a -loop switch

---

### Post by CatKiller on 2006-11-21
> **PoLiSonTe said:**
> I been doing some search but i haven't been able to find any that does the job. Any idea? ](*,)

You can mount an ISO file with the **mount** command. You can convert other image formats into an ISO with **bchunk**.

---

### Post by PoLiSonTe on 2006-11-22
So just to make sure I understand the command would be "sudo mount filename.iso -loop"? from there directory where the file is.. sorry if my questions are silly..and also im at work so i cant try the command till i get home :)

---

### Post by mcduck on 2006-11-22
the command is 'sudo mount -o loop /location_of/file.iso /media/cdrom'

(change the path and filename to point to your file)

---

