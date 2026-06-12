---
title: "WINE Install Failure On Feisty AMD64"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by givupnliv on 2007-07-14
I posted this on another thread earlier, but then I realized that thread had been inactive for a couple days or so.

I'm not sure if this qualifies as a new thread. I tried to install WINE on Feisty AMD64, it apparently didn't take. I am getting the following error msg when I run update manager:

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

Any advice would be appreciated. 

It is my understanding that if I can get wine running properly, i will be able to run cd-rom games on Feisty Fawn 64bit even though the cd's came only with windows drivers.. Is this correct?

---

### Post by rahul.gupta on 2007-07-17
i guess you did not import the gpg key for the repository. try issuing the following command

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Here is the link which helped me install wine on feisty AMD64
[https://help.ubuntu.com/community/WineForAMD64](https://help.ubuntu.com/community/WineForAMD64)

---

