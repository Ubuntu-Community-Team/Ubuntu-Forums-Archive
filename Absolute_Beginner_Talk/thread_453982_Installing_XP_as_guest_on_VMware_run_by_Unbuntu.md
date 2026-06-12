---
title: "Installing XP as guest on VMware run by Unbuntu"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by URR on 2007-05-25
Hey all,

I have installed the latest Ubuntu - clean install - and installed vmware server - which runs fine, except when I try to install XP in the vmware guest OS - I get a ntldr error - basically, it goes to the XP install CDROM and says you got no ntloader.....

Any help here?

I only need XP so I can run Microsoft Money 2000. Wine doesn't like it.

Ciao - help!

---

### Post by Ek0nomik on 2007-05-25
What's the exact error message?

---

### Post by URR on 2007-05-25
I start the virtual machine, it begins to load the cd and then says:

"CDBOOT: Couldn't find NTLDR"

And thats it.

---

### Post by Ek0nomik on 2007-05-25
I have only used VirtualBox once, and I got rid of it.  (Although I will say it seemed like good software).

I don't know what the error is, but maybe someone else does.

In the mean time, maybe Google can help:  [http://www.google.com/search?hl=en&q=Couldn%27t+find+NTLDR&btnG=Google+Search](http://www.google.com/search?hl=en&q=Couldn%27t+find+NTLDR&btnG=Google+Search)

---

### Post by mariosx on 2007-06-08
well... i had the same error message with virtualBox a few minutes ago.

In my case, the error was shown, because i didn't mount the cd-rom drive, so virtualbox couldn't find somewhere to boot from...

When i mounted the cd-rom drive, and rebooted ubuntu, everything was OK

i don't konw vmware... try checking the settings for cd-rom options...

---

