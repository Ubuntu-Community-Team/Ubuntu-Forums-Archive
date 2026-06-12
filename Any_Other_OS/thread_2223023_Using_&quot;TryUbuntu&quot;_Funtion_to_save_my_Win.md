---
title: "Using &quot;TryUbuntu&quot; Funtion to save my Windows (Help Please!)"
date: 2014-05-09
forum: Any Other OS
---

### Post by binamenator on 2014-05-09
Hi all,
I need your genius brains. Please help me.

Basically I screwed up my Windows 8, and every time I log in, the screen goes black and back into the log-in screen.
(I changed to high contrast in assesebility, and now it won't let me log in)

So I'm was thinking that I could save all my files from my hardrive using a flashdrive and running "tryubuntu"
My files are saved on a different hardrive than the C: drive, so I thought I would be able to access it. But when I try, I get this error message:

Error mounting /dev/sda5 at /media/ubuntu/Binam: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sda5" "/media/ubuntu/Binam"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda5': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

Please help me solve this problem.... thanks....
BinamK

---

### Post by binamenator on 2014-05-09
I've posted on this forum, because it deals with other operating systems as well, so I thought you guys might be more knowlegable in the problem.
I have no idea what "officially recognised Ubuntu flavours" is supposed too mean in the rules form, so I hope I'm not breaking any rules :p....

BinamK

---

### Post by LastDino on 2014-05-09
Hybrid shutdown is enabled on W8, that is why you're getting this problem.

[http://askubuntu.com/questions/296030/error-mounting-ntfs-partition-after-hybrid-shutdown-with-windows-8](http://askubuntu.com/questions/296030/error-mounting-ntfs-partition-after-hybrid-shutdown-with-windows-8)

---

### Post by binamenator on 2014-05-10
Thanks LastDino, 

I can access both the C: and D: drives now! Woohoo!
If I find a solution on the windows contrast problem I'll post it here.

Thanks again,
BinamK

---

### Post by LastDino on 2014-05-10
You're welcome.

---

