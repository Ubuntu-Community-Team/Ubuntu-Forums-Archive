---
title: "Macbook Pro"
date: 2010-07-21
forum: Apple Hardware Users
---

### Post by NFblaze on 2010-07-21
So I had a Macbook pro for like an hour. I was trying to fix the users forgotten password.

Anyway, besides the point. I happened to load up an Ubuntu LiveCD just to see if the system would work. It did run off the LiveCD but for some reason the Macs hard drive wasnt viewable. It showed me a single folder with some long path all I remember is that it said EFI in the path name and firmware.

Im thinking it was some sort of encryption but I do not know. Perhaps it needs an HFSPlus driver?

Any guidance?

---

### Post by NFblaze on 2010-07-22
bump

---

### Post by elendryst on 2010-07-22
You can change the root password from the Mac OS X install disk that came with the computer. Or, if they upgraded to Snow Leopard, pop a copy of Snow Leopard in.

As for viewing the HFS+ partition from the LiveCD, never tried. But I know my external hard drive formatted HFS+ from the Ubuntu LiveCD doesn't show up when installing either. It does show up when Ubuntu is installed however.

---

### Post by NFblaze on 2010-07-25
Thanks for the answer. Actually, I was fixing the computer for someone else, and didnt own the CD.

---

### Post by Spitphire on 2010-07-26
Yah--stolen laptops are always a bummer--never comes with all the CDs. :p

---

### Post by NFblaze on 2010-07-26
I dont ask questions or judge. I just fix the computer issues.

Though, if he wants to torture himself using a Mac. Be my guest.

---

### Post by Macskeeball on 2010-07-26
EFI is not an encryption. It's like BIOS but newer, and Macs have a small and invisible EFI partition that is used by OS X for doing firmware updates.

> **elendryst said:**
> You can change the root password from the Mac OS X install disk that came with the computer.

Technically what you're talking about is the password for the *admin* accounts, not root. The root account is disabled by default.

---

### Post by NFblaze on 2010-07-26
Exactly, the admin account. Sorry, I only spent an hour or so with it. (and it was not my cup of tea.)

On a sidenote I ended up changing the admin password, after finally figuring how to long into single user mode and using the root account to use passwd to change it. 

Gotta like Linux/Unix knowledge.

---

