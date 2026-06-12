---
title: "The default user - what groups is he part of?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by wildkarde on 2007-06-07
By mistake I removed my main user from all groups.  I went to single usermode and tried to take educated guesses by looking at /etc/groups as to which groups he was a part of.

I succedded for the most part - but now whenever I tried to do something admin related it will not ask for my password no longer.  (this is when i use sudo, gksu).

Can anyone please type 'id' on their system and paste it so i can see which groups i should be part of?

This is what mine shows.

```
contarc@contarc-desktop:~$ id
uid=1000(contarc) gid=1000(contarc) groups=4(adm),24(cdrom),27(sudo),29(audio),46(plugdev),104(scanner),117(admin),1000(contarc),1001(vboxusers)

```

Thank you.

---

### Post by Kingsley on 2007-06-07
Here is mine.
```
uid=1000(king) gid=1000(king) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(king),1001(vboxusers)

```

---

### Post by wildkarde on 2007-06-07
Thank you.

---

### Post by fazillatheef on 2007-06-07
I am new to forums.I can mount ubuntu dvd but cant add it to the repository.
can you pls help

---

### Post by wildkarde on 2007-06-07
You might want to start a new topic about this.

What exactly do you want to do?  Are you trying to set the dvd as a repository to install applications from it?

---

### Post by evaldas on 2007-06-13
is someone still using Edgy Eft 6.10?
I have the same problem as wildkarde, I accidentally removed myself from all groups. Please paste the output of 'id' on Ubuntu 6.10, cause on the output of 7.04 I see some groups, which aren't in 6.10.

thanks

---

### Post by evaldas on 2007-06-14
*bump*

---

