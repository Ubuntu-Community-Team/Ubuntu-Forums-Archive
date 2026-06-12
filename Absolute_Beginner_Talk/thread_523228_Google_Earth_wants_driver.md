---
title: "Google Earth wants driver"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by ADH on 2007-08-11
I installed Google Earth, but it tells me I need a driver for my video card.  The card is a Matrox G450, and there don't appear to be any Linux drivers on the Matrox site.  Where can I get the driver I need?

Thank.

---

### Post by csimons on 2007-08-11
It seems that the driver can be found here:

[http://www.matrox.com/graphics/en/corpo/support/drivers/home.php](http://www.matrox.com/graphics/en/corpo/support/drivers/home.php)

You'll need to know whether you're running 32-bit or 64-bit Linux, and whether your card is a G450x2 or G450x4.


If you drill into the "G450 MMS Series" item in the "Graphics Cards (Add-in boards)" category, check your card model, click Next, check "Latest display drivers", and Next, "Linux" and "Linux 64-bit" appear.  If you check one of those and continue, the drivers appear on the following page.

---

### Post by ADH on 2007-08-11
I'm running Ubuntu 7.04 - is that 32 or 64 bit?

As for the card, it's a regular Matrox G450.  Is there something in Ubuntu that will give me details on the card?

---

### Post by eapache on 2007-08-11
32bit

System>Prefs>Hardware Information

---

### Post by ADH on 2007-08-11
Hardware information just shows the card as an MGA G400/G450 with 32 Meg.  No x2 or x4.

---

### Post by eapache on 2007-08-11
What is the output of```
sudo lspci
```

---

### Post by ADH on 2007-08-11
How do I do that?

---

### Post by eapache on 2007-08-11
Applications>Accessories>Terminal

---

### Post by ADH on 2007-08-11
I didn't see anything different than Matrox G450.

---

### Post by eapache on 2007-08-11
That's really odd. I can't think of any other way, so just try them both. Sorry I couldn't be of more help.

---

### Post by ADH on 2007-08-11
I really appreciate your trying.  Thanks.

Alan

---

