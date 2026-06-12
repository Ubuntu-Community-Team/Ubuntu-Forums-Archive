---
title: "Before I go to install Arch..."
date: 2008-02-29
forum: Arch and derivatives
---

### Post by Pogeymanz on 2008-02-29
Can I use the same config files from my Ubuntu install?

I scanned through the beginner's guide and it seems like I might be able to copy a lot of the info from Ubuntu.

I'm thinking I might just print out copies of some config files. Which ones should I print?

I'm super-paranoid that I wont be able to get my broadcom card working. Is that going to cause problems, or will Arch help me out with that?

---

### Post by justsomedude on 2008-02-29
Some config files in Arch are the same, some are different.

In general: do not copy and paste entire config files or parts of them from Ubuntu to Arch.

Instead, print out your config files from Ubuntu so you can refer to them while configuring Arch. However, your most important source of information should be their beginners guide. 

Your xorg.conf is definitely worth printing out, as are your config files regarding network and such.

```
Is that going to cause problems, or will Arch help me out with that?
```

Well, Arch will do nothing automatically for you. However, their documentation is excellent and the setup is nothing to be afraid of if you are patient enough to read the documentation.


If an idiot like myself can do it, it'll be a walk in the park for you.

---

### Post by Rumor on 2008-02-29
> **EmosSuck777 said:**
> Can I use the same config files from my Ubuntu install?

I scanned through the beginner's guide and it seems like I might be able to copy a lot of the info from Ubuntu.

I'm thinking I might just print out copies of some config files. Which ones should I print?

I have no experience with Broadcom cards. Before installing, you might want to search the Arch forums for your broadcom card to see if other users have had to jump through lots of hoops to get it working.

The config file you might want to print is your network one in /etc/init.d/ 

Arch does not use init.d, so when you go to compare them, you'll want to look in /etc/rc.d/ for the file in Arch.

The Arch forums are a great resource for help with installation issues. Good luck if you decide to undertake the install!

---

### Post by Crooksey on 2008-03-01
You could keep your home dir, this would keep user created program settings for programs, and arent nearly all broadcom cards supported natively now?

---

