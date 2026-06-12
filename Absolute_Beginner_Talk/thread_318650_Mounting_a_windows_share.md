---
title: "Mounting a windows share"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by lance_klusener on 2006-12-14
Hello folks , 
                 I wanted to mount windows share on my ubuntu machine . So i went thru the forum i found that samba was the way to go .

But when i explored the OS further i found that there was a option under places --> connect to server , in the service type i choose "windows share" and i specified the remainning parameters which allowed me to mount the share.

My question is are both of these mouting techniques same or is there a difference between them ( meaning does the connect to server wizard use samba internally ? )

Thanks in advance , 
Lance

---

### Post by zgornel on 2006-12-14
The connect to server method is less reliable and is nautilus related. You can't for example play files from there because the smb:// protocol is not recognized by applications. Mount the samba shares through fstab or using the mount command.

---

### Post by lance_klusener on 2006-12-14
Thanks man

---

### Post by mogwai on 2006-12-14
Try [here]("http://ubuntuforums.org/showthread.php?t=280473&highlight=mounting+a+windows+share")

---

