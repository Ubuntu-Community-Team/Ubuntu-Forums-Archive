---
title: "[SOLVED] Sudo  problem"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by DaveyG on 2007-03-20
Hi, i tried to install updates via the synaptic manager but it doesnt seem to open, so i tried opening it with the terminal and this is the result

```
davey@davey-online:~$ gksu /usr/sbin/synaptic
sudo: must be setuid root
davey@davey-online:~$ 

```

I think iv lost sudo but have no idea how to get it back,
any help would be much appreciated.

Thanks, Davey

---

### Post by Bachstelze on 2007-03-20
Same thing with *gksudo synaptic* ? If so, what happens when you do *sudo -i* ?

---

### Post by DaveyG on 2007-03-20
Same thing happens, must be setuid root

what il do is give the forum a search and see what i can find

---

### Post by 3rdalbum on 2007-03-20
Go into recovery mode (by starting its entry in GRUB). When you get to the recovery terminal, type "startx".

Now, open up a file browser to /usr/bin and find "sudo". Right-click it, select Properties, then click on the Permissions tab. Make sure that the owner is "root" and the group is "root" - if it isn't, then change those to root. Now, click the "Set User ID" checkbox to turn it on.

Reboot into normal mode, and now sudo should work.

---

### Post by Circus-Killer on 2007-03-20
you might want to check what groups your user is a part of. 

i think you might need to add *wheel* to the list of groups for your current user.

---

### Post by DaveyG on 2007-03-20
Thanks all for your help, i read posts 8 & 9 on [this thread]("http://ubuntuforums.org/showthread.php?t=228443&highlight=setuid+root"). i seem to have sudo back & synaptic manager opens ok now.

---

