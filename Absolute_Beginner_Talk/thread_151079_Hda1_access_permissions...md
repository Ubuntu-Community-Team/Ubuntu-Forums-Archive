---
title: "Hda1 access permissions.."
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by abyrne10 on 2006-03-27
Hi all..

I just installed Ubuntu on my pc. I have 2 20 GB HDs. I formatted one of them and installed successfully Ubuntu on it. Xp sp2 is on the other (NTFS). On my desktop there is an icon called Hda1 but when I try to open it, it says I don't have the permissions. I can browse this HD with the disk manager, but is there some way that I can browse it from the icon on my desktop?

Thanks in advance..

---

### Post by taurus on 2006-03-27
You need to edit your /etc/fstab and add this line in "umask=0222" so you can read stuff on the first harddrive...
```

/dev/hda1  /media/xp  ntfs  defaults,umask=0222   0  0

```

---

### Post by abyrne10 on 2006-03-27
[QUOTE=taurus]You need to edit your /etc/fstab and add this line in "umask=0222" so you can read stuff on the first harddrive...
```

/dev/hda1  /media/xp  ntfs  defaults,umask=0222   0  0

```[/QUOTE]

thx for the reply, but it didn't work; I still get the same error message (btw it's mounted to /media/windows..I put that in instead of /media/xp). In the disk manager it says that Hda1 is accessible..why can't I access it from the file browser or anything?

---

### Post by abyrne10 on 2006-03-27
[QUOTE=taurus]You need to edit your /etc/fstab and add this line in "umask=0222" so you can read stuff on the first harddrive...
```

/dev/hda1  /media/xp  ntfs  defaults,umask=0222   0  0

```[/QUOTE]

SORRY my mistake it worked....i didnt reboot the computer first time round

thanks again!

---

