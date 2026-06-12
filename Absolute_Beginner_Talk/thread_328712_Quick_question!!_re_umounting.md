---
title: "Quick question!! re umounting"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by linuxbun on 2006-12-31
I just need this one thing to finish off a small script i'm working on. I've googled for a while now, still can't find what I want.

to unmount i use

sudo umount ~/folder

but I want to grant my username permissions to umount. How can I do this? I can mount without sudo (as I added myself to the fuse group) but I couldn't see any groups to add myself to with regards to mounting.

Would greatly apprecaite a quick response :) 

ty!!!!!!!!:mrgreen:

---

### Post by Hossie on 2006-12-31
> *man mount*

Only the user that mounted a filesystem can unmount it again. If any user should be able to unmount, then use users instead of user in the fstab line. The owner option is similar to the user option, with the restriction that the user must be the owner of the special file. This may be useful e.g. for /dev/fd if a login script makes the console user owner of this device. The group option is similar, with the restriction that the user must be member of the group of the special file.

Does that help you?

---

