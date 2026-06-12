---
title: "Root// problem?"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by moonliter on 2006-08-07
When I try to copy some files to my root disk it says:

[B]Error while copying to "/media/hda1"

You do not have permissions to write to this folder
[/B]

Please can you tell me why because i am the only administrator user.What to do?

---

### Post by taurus on 2006-08-07
You can either use the "sudo" before the "cp" command or you can mount it using /etc/fstab with read/write permissions for everybody!!!  I assume you are talking about vfat filesystem, right!

```

sudo cp <filename> /media/hda1

```

---

### Post by moonliter on 2006-08-07
I have made it.Thanks a lot!
So every time i want to copy something i need to use terminal?
Can I just use my mouse to copy?
Thanks!!

---

