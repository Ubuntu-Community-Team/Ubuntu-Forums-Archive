---
title: "Be root?"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Spaceomega on 2007-03-14
I've been using Ubuntu [Feisty fawn herd 5, seeing as how that's the only one that supports my Wireless adapter by default], and i've seemed to run into a problem.

I'm not "root".  I don't have all of "root"'s access.  Can I become this "root" ? Mainly what I'm trying to do is just be able to write to my ntfs partition, but it says I must be root.  

Any help?

---

### Post by geezerone on 2007-03-14
[COLOR="Purple"]man sudo-root[/COLOR] in terminal. Sudo gives you root access for 15mins in current terminal window.

---

### Post by siciliancasanova on 2007-03-14
There is a way to make yourself always have root access but it is not advised at times.  You would be coming closer to security vulnerabilities much like windows machines have.

---

### Post by tribaal on 2007-03-14
If for some reason you really need to have a root shell (couldn't think of one), there's always the option to type ```
sudo su
``` at the prompt.

Sudo should be really all you need however.

- trib'

---

### Post by Spaceomega on 2007-03-14
Thanks, guys.

By the way;  if there is maybe just a way to allow me to always write to my ntfs files, that'd be helpful if i had that information.  Anyone got a solution there? :)

---

### Post by zvacet on 2007-03-14
If you want to start something and you must be root 
```
sudo whatever
```
you will be asked for password and you type it even if you do not see what you are typing.

P.S. you will find that solution on this forums but it is not recomended to write on ntfs.

---

### Post by tribaal on 2007-03-14
The problem with ntfs is more a driver question than a system rights question.
I'm pretty sure I've seen several threads on how to make ntfs partition writable floating around here somewhere, but I've never installed the required stuff myself (don't have a windows partition to write to :) ).

For what I can remember, the problem is that writing is still not officially stable and may lead to an unconsistant ntfs system. But hey, you should really search the forums and wiki for a real answer, and not listen to me :)

- trib'

---

### Post by Kateikyoushi on 2007-03-14
> **Spaceomega said:**
> Thanks, guys.

By the way;  if there is maybe just a way to allow me to always write to my ntfs files, that'd be helpful if i had that information.  Anyone got a solution there? :)

Install ntfs-3g then edit your fstab. [LINK]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access")

List your partitions with the following commmand to know which one is the NTFS and replace hda1 if necessary.

```
sudo fdisk -l
```

---

### Post by Spaceomega on 2007-03-14
Works like a charm.  Thanks a ton : )

---

