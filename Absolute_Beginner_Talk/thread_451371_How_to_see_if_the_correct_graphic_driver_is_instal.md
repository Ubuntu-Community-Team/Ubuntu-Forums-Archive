---
title: "How to see if the correct graphic driver is installed and working?"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by stefaan.dutry on 2007-05-22
Hi I'd like to know if it's possible to see if i installed the right graphic driver.

I'd also like to know if there's a way to make sure it is running properly.

Graphics card type : ATI RADEON x1650

I think i installed them, but have no idea if it was succesfull.

Any hints would be welcome.

---

### Post by BarfBag on 2007-05-22
Look in your xorg.conf.  It's next to Driver.

---

### Post by stefaan.dutry on 2007-05-22
There is something there, but it seems like there's too little info there.

I'm currently not at home, i will be in about an hour or so, I'll check then and post what's there.

Thank you for your response.

---

### Post by stefaan.dutry on 2007-05-22
```
Section "Device"
	Identifier	"Generieke videokaart"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
```

That's what it says

I have a ATI RADEON X1650 card and it states Generic videocard; so i don't know if that's right

Please help someone

Thanks in advance.

---

### Post by Terl on 2007-05-22
Per Ubuntu docs try entering:

```
fglrxinfo

```

Hopefully you will see something akin to this but with your info:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 2.0.5755 (8.24.8)
```

I found the info here:  [ATI How To]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28driver%29%7C%28ati%29")

---

### Post by stefaan.dutry on 2007-05-22
Thank you.

It showed me it was installed alright.

Now i know that that's not the problem if i should encounter one.

Sorry for not seeing it at that page myself, cause that's where i looked to install the drives actualy, must have missed that paragraph or something.

:D

---

