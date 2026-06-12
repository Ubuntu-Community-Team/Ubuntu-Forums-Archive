---
title: "Corrupt xorg.conf file"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by reeksy on 2006-09-18
Hi.

I’ve just made the switch from Windows to Linux. I’ve successfully installed Kubuntu 6.06 and it’s great! I decided to get technical and fell at the first hurdle!

I want to run dual monitors and started editing the xorg.conf (in /etc/X11/xorg.conf) as per a ‘how to’ I found through google. However I’ve managed to corrupt the file and I can’t boot Linux now! I made backup of the file but I can’t get to it! I don’t even get as far as the login screen! The boot sequence goes fine and I get that scrolling-like sequence as things load up, however just before the login screen Linux gets stuck! I assume my PC hasn’t crashed as scroll lock still responds. 

So my question is how to I get back into Linux to recover the file?

Sorry – I’m a Linux beginner!

Thanks

Jon.

---

### Post by Brunellus on 2006-09-18
xorg.conf can take a lot of beating.  you will likely just come to a textmode login.

Log in there as usual, and then execute

sudo dpkg-reconfigure xserver-xorg

---

### Post by buffy^ on 2006-09-18
ok when the grub is loading press escape and load into safe mode to start with after that you should be able to reveter yuor changes.

---

### Post by taurus on 2006-09-18
Can you get to another console with <Ctrl><Atl>F2?  Otherwise, try to boot the desktop CD (LiveCD) and mount your partition where / is.  Then, copy the old /etc/X11/xorg.conf over again...

---

### Post by reeksy on 2006-09-18
I’ve just booted as normal and let it run. However I don’t come to a text mode login. Instead i have the Kubuntu logo and what looks like a blue horizontal loading bar (all on a black background). I don’t have any user control from here.

Is there another way i can access this text mode login?

---

### Post by buffy^ on 2006-09-18
> **buffy^ said:**
> ok when the grub is loading press escape and load into safe mode to start with after that you should be able to reveter yuor changes.

Try that

---

### Post by reeksy on 2006-09-18
OK thanks a lot.

Back up and running - i gotta say that was some quick replying! I could get used to this open source thing!

Does anyone know of a simple how-to when it comes to setting up  dual monitors? I'm struggling a bit here!

---

### Post by Brunellus on 2006-09-18
> **reeksy said:**
> I’ve just booted as normal and let it run. However I don’t come to a text mode login. Instead i have the Kubuntu logo and what looks like a blue horizontal loading bar (all on a black background). I don’t have any user control from here.

Is there another way i can access this text mode login?
hit CTRL + ALT + F1

---

