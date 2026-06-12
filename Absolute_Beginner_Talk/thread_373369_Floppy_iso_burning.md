---
title: "Floppy iso burning"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by xunshirine on 2007-03-01
Hello. I reinstalled Windows and grub disappeared. I intend to try Super Grub Disk . I have downloaded the iso file for floppy disks . How can I burn this iso file onto floppy disk? I am on windows box now.
Thanks in advance.

---

### Post by Bachstelze on 2007-03-01
ISO files are supposed to be burned on CDs, not foppy disks. If you're certain your file is a floppy image, do

```
sudo dd if=/path/to/image of=/dev/fd0
```

replace /dev/fd0 with the path to your floppy drive of course.

---

### Post by xunshirine on 2007-03-01
> **HymnToLife said:**
> ISO files are supposed to be burned on CDs, not foppy disks. If you're certain your file is a floppy image, do

```
sudo dd if=/path/to/image of=/dev/fd0
```

replace /dev/fd0 with the path to your floppy drive of course.

Thanks for the reply. I have miswritten .The extension is **.img**. This is the [file download link]("http://forjamari.linex.org/frs/download.php/477/sgd_english_floppy_0.9550.img") that is on [http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61). And I am on windows box unfortunately and cant boot Ubuntu  box now. Could you give the solutioun according the windows if possible?

---

### Post by jkeyes0 on 2007-03-01
Since you're in windows, you'll have to use a program such as rawrite or winrawrite (gui based, easier) from [http://www.totalshareware.com/ASP/detail_view.asp?application=11059](http://www.totalshareware.com/ASP/detail_view.asp?application=11059) to do it.

---

