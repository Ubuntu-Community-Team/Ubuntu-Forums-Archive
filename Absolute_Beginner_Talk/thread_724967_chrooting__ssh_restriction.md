---
title: "chrooting / ssh restriction"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by sebkinne on 2008-03-15
Hello fellow ubuntuers,

i am actually under a little time preassure, but it would be great if someone could help me.

I need to restrict a user to ONLY their home directory, meaning he cannot view or cd into the / dir. in otherwords, have no access whatsoever to any dir above his home dir.

I tried using a chroot or a programm that jails the user, which should work fine, but his user shell is so restricted that he cannot even change his password, (passwd) and he cant use vim, nano, and other things like that, which i need him to use tho. he should be able to do anything he wants, as long as he is in his home dir.

i hope someone can help me, and i did search here in the forum,

regards,
sebkinne

---

### Post by mrsteveman1 on 2008-03-15
There is a patch for openssh that implements chrooting, but ubuntu hasn't picked it up for some reason. I just set it up on my server (which runs arch, they had a package for it), and it works well it seems.

For scp/sftp only there is the rssh-chroot shell which restricts users to a specific directory, but that doesn't work for a real shell, it'll refuse to let them login.

---

### Post by sebkinne on 2008-03-15
hm... well i solved it, i chrooted the user, and manually added the commands + files it needs.

regards,
sebkinne

---

