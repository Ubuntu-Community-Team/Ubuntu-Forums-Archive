---
title: "out of space"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by sqela on 2007-11-03
to make a long story short i followed the instructions on pendrivelinux.com to install gutsy on my 1gb flash drive. unfortuntly i installed too many programs and the disk is filled to capsity. i recieved the error at the login screen not allowing me to login due to space. i tried autoclean and after a while i manged to login. however i was still reciving the error message that there was no room. i opened add/remove programs and when attemping to ninstall a few unneeded programs i recieved the
""dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "
i run the dpkg -config command only to get this error

"dpkg: failed to write status record about `xlsclients' to `/var/lib/dpkg/status': No space left on device"

am i in an endless loop here or can i fix this?

---

### Post by jfinkels on 2007-11-03
You can try deleting some of the files in your cache to clear some space.

Mount the flash drive from an operating system on your hard disk, and delete the contents of /var/cache/apt/archives/ . This is where the apt package management system downloads and caches packages when you tell it to install packages. You don't really need them, as you can always redownload them, (unless you don't have an internet connection...).

---

### Post by sqela on 2007-11-03
found the files and when i got to delete i dont have permission to :(

---

### Post by sqela on 2007-11-03
never mind figured out how to get root:guitar:

---

### Post by jordank on 2007-11-03
moral of this story?

---

