---
title: "No response to sudo chown in terminal?"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by FluorescentDuck on 2007-01-20
Hello everyone,

I installed a dual boot of Ubuntu Edgy and Windows XP a few days ago, and copied all my documents from the NTFS partition onto my Ext3 data partition. Now all the file permissions are set to root as the owner.

I've tried changing the file permissions using "gksudo nautilus", but the "Apply permissions to enclosed files" button has no effect. I can only change the file permissions one-by-one right now.

I've tried typing "sudo chown -R myname:myname folder/path/here", but when I press enter terminal simply skips to the next line and does nothing.

Could anyone please help with this? I'd really prefer not having to change all my files one by one!

---

### Post by taurus on 2007-01-20
Where did you save those files?

---

### Post by FluorescentDuck on 2007-01-20
Ooh..thanks for the quick reply. Right now I have them at /data/Mystuff. Data was set up as a partition of its own, if that makes any difference.:???:

---

### Post by taurus on 2007-01-20
What's the outputs of these two commands from a terminal?

```
id
ls -la /data
```

---

### Post by FluorescentDuck on 2007-01-20
I got this for id:

uid=1000(juanxi) gid=1000(juanxi) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),114(admin),1000(juanxi)

And this for ls -la /data:

total 68
drwxr-xr-x  6 root   root  4096 2007-01-19 16:50 .
drwxr-xr-x 23 root   root  4096 2007-01-18 20:09 ..
drwxrwxrwx 13 juanxi root  4096 2007-01-19 21:42 My Stuff
drwxr-xr-x  2 root   root 49152 2007-01-17 15:38 lost+found
drwxr-xr-x  2 root   root  4096 2007-01-19 16:51 Recycled
drwx------  8 root   root  4096 2007-01-18 19:09 .Trash-root

---

### Post by taurus on 2007-01-20
```
sudo chown -R juanxi:juanxi "/data/My Stuff"
ls -la /data
```

---

### Post by FluorescentDuck on 2007-01-20
Wow, thank you! That worked perfectly. :D Heh...I realize now that all I did was forget the quotation marks.

---

### Post by taurus on 2007-01-20
> **FluorescentDuck said:**
> Wow, thank you! That worked perfectly. :D

Good.  =D>

---

