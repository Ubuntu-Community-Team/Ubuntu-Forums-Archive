---
title: "sudo access disabled"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by abhi_am on 2006-02-28
Hello,

I'm in a big fix. I'm the only user on my machine (Ubuntu 5.10) and my login is "ashu". I removed myself from the admin group by typing the command "usermod -Gdisk ashu". I was doing this to add myself to the disk group so that I could change files on disk without requiring to sudo always.

Anyhow, this led to my removal from the "adm" group and as a result I can't use sudo anymore. Also, I've locked the root account by using the command "sudo passwd -l root". As a result, I can't use sudo or su to access admin privileges.

Is there anyway I can recover from this blunder?

Thanks!
Ashu

---

### Post by o_fortuna on 2006-02-28
[QUOTE=abhi_am]Hello,

I'm in a big fix. I'm the only user on my machine (Ubuntu 5.10) and my login is "ashu". I removed myself from the admin group by typing the command "usermod -Gdisk ashu". I was doing this to add myself to the disk group so that I could change files on disk without requiring to sudo always.

Anyhow, this led to my removal from the "adm" group and as a result I can't use sudo anymore. Also, I've locked the root account by using the command "sudo passwd -l root". As a result, I can't use sudo or su to access admin privileges.

Is there anyway I can recover from this blunder?

Thanks!
Ashu[/QUOTE]
Start up your computer and hit ESC before Ubuntu starts loading. Then, choose recovery mode, which gives you automatic root access. From there, you can change your user's group back to admin witht the correct command.

---

### Post by abhi_am on 2006-03-02
Thanks for the note o_fortuna. I tried doing this unsuccessfully since the file system was mounted as read-only. Please let me know if know a way to get around this problem.

What I did instead was to boot through an install CD, manually mount that file system, and then edit the /etc/groups file. This worked.

Thanks!

---

### Post by mlind on 2006-03-02
You can specify run level as a kernel parameter. If you put it as 1, you will get root
access if I recall right.

If you press 'e' during Grub's menu (ESC if it doesn't show on bootup) and apply
'1' without dashes on kernel line.

```

kernel          /vmlinuz-2.6.15-16-k7 root=/dev/hda3 1

```

I recall I once solved my problem like this.

---

