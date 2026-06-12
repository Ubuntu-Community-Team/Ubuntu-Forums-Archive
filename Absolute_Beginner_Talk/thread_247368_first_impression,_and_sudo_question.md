---
title: "first impression, and sudo question"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by bitbytebit on 2006-08-30
Well

I really wanted to like Ubuntu .. I tried the live CD, it didn't find my dlink USB wireless adapter.

The detailed help needs to have an online connection, so there goes that.

I plan on trying automatix, maybe that will work, otherwise I guess its back to debian ..although thats weird, if debian found my wireless why coudln't Ubuntu?

finally theres SUDO, for people who are used to having a root shell open is having no root access bothersome?

Thanks,

---

### Post by johnnymac on 2006-08-30
No - you can have that root access by issuing:

```

sudo bash

```

But it's just a good way at protecting people...even those who've used linux for years make the mistake of:

```

rm -rf *
vs
rm -f *

```

---

### Post by PPAAUULL on 2006-08-30
I used to think not being able to get in as root was a hassel, but when I switched back to SUSE from Ubuntu I ran into a problem the the SUDO could have prevented. I am now happily using Ubuntu and will be for a long time!!!

---

### Post by bitbytebit on 2006-08-30
Thanks for the replies.

The main thing that disappointed me I guess was that it doesn't really seem like Ubuntu is really any different from an installation standpoint as other distro's

With all the talk over the last several months I think I expected everything to 'just work'

I'll give it another go though

---

### Post by PPAAUULL on 2006-08-30
Install it and see if it will work. Besides you can come back here and it is probobly really easy to fix a lot of things that don't get detected.

---

### Post by matthew on 2006-08-30
If sudo bugs you that's okay. You can enable a root account and use Ubuntu just as you are used to with Debian and other distros. This wiki page describes how...it's easy and it's reversable.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

As far as your D-Link adapter, I don't have any experience using one, sorry. Without more info (specific model, etc.) I can't be much more helpful, but there is info on some of their usb wireless cards on this wiki page.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by aysiu on 2006-08-30
> **bitbytebit said:**
> 
finally theres SUDO, for people who are used to having a root shell open is having no root access bothersome? Type ```
sudo -s
``` and you'll have a root shell.

---

### Post by Bachstelze on 2006-08-30
The Wiki says *sudo -i* to gat a root shell.

---

### Post by aysiu on 2006-08-30
> **HymnToLife said:**
> The Wiki says *sudo -i* to gat a root shell.
That works as well.

---

### Post by Bachstelze on 2006-08-30
Yeah I know but I remember someone on #ubuntu saying sudo -s could break something up, just like sudo su.

---

### Post by aysiu on 2006-08-30
> **HymnToLife said:**
> Yeah I know but I remember someone on #ubuntu saying sudo -s could break something up, just like sudo su.
What was the explanation given for the potential breakage?

---

