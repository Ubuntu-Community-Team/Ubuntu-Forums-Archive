---
title: "Can Wine be used to make pci modem connection?"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by directcharitycontribution on 2007-01-03
so that the system can go online until the just linux method is understood?

---

### Post by earobinson on 2007-01-03
wine cant install windows drivers so no, however if you had a program that directly talked to the pci bus to comunicate to the modem that would work but only for that program not for all of linux.

In your case I expect the answer is no

---

### Post by directcharitycontribution on 2007-01-03
No Windows programme that can make the connection?

---

### Post by earobinson on 2007-01-03
So if I understand all you have is a driver, in that case wine will not be able to do what you want.

Sorry

---

### Post by az on 2007-01-03
> **directcharitycontribution said:**
> No Windows programme that can make the connection?

Wine runs in userspace.  A driver run in the kernel space.  The windows driver you have is for the windows kernel.

Many wireless cards have driver built around the NDIS windows API.  As such, there is a linux kernel wrapper for NDIS which can use the windows drivers in linux (ndiswrapper).  Software modems do not use NDIS.  Since the functionality of the modem is in the software, the drivers are windows-only.

That being said, many software modems have linux drivers available, but they usually cannot be distributed along with the OS for licencing reasons.

See here:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by directcharitycontribution on 2007-01-05
wa!

---

### Post by Rodneyck on 2007-01-05
> **directcharitycontribution said:**
> No Windows programme that can make the connection?

Dreamlinux (debian based) has a program that configures windows pci drivers (at least for wireless) at least it appeared so from my initial inspection. I have not played around with it yet. You may see if it works and maybe it is available through synaptic (what they use.)  It is the first time I had ever seen such a program in a distro.

Best...

[http://www.dreamlinux.com.br/](http://www.dreamlinux.com.br/)

---

### Post by directcharitycontribution on 2007-01-06
> **Rodneyck said:**
> Dreamlinux (debian based) has a program that configures windows pci drivers (at least for wireless) .... It is the first time I had ever seen such a program in a distro.

Best...

[http://www.dreamlinux.com.br/](http://www.dreamlinux.com.br/)

thx. will certainly mark and look over this. suggests there is potential. another thread mentioned [http://distrowatch.com/kurumin]("http://distrowatch.com/kurumin") managing windows pci drivers but that was in porto and didnt recognise any connections between this and dreamlinux and didnt fancy translation on translation much. what is it driving brazil?

I'm guessing with laptops choice of modem must be more critical.

---

### Post by Rodneyck on 2007-01-06
> **directcharitycontribution said:**
> thx. will certainly mark and look over this. suggests there is potential. another thread mentioned [http://distrowatch.com/kurumin]("http://distrowatch.com/kurumin") managing windows pci drivers but that was in porto and didnt recognise any connections between this and dreamlinux and didnt fancy translation on translation much. what is it driving brazil?

I'm guessing with laptops choice of modem must be more critical.

Foresight Linux had a windows wireless application as well, another one to check out.  :D

---

