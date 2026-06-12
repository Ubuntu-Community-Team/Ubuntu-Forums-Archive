---
title: "booting without keyboard and monitor on mac mini intel"
date: 2006-10-07
forum: Apple PPC Users
---

### Post by matcram on 2006-10-07
Hi all,

i installed ubuntu on my brand new mac mini intel and my last problem is that when i want to boot it without any keyboard or monitor attached to it, it simply doesn't start.

It's kinda weird and i can't seem to find any clue on the forum or on google.

Could someone point me into a direction ?

forget to say i'm of course using dapper.

Thanks in advance,
Matthieu.

---

### Post by matcram on 2006-10-07
i answer to myself and to others that might be interested...

The only way to boot the mac mini headless (without monitor) seems to be throught the use of a "dummy connector" that simulates the presence of a monitor. [http://tvtool.info/go.htm?http://tvtool.info/english/dummy_e.htm](http://tvtool.info/go.htm?http://tvtool.info/english/dummy_e.htm)

I also called the apple support and they told me the same...

BUT, i also found that when you run MacOSX the mini can boot headless if you turn the remote access ON.

If MACOSX can do it, then Ubuntu can do it too. I think...

Any clue ?

---

### Post by matcram on 2006-10-11
up ? and help please :mrgreen:

---

### Post by brent.stephens on 2006-10-21
Consider yourself lucky :)  I didn't run into this problem until I had already colocated my Mac mini.  Rebooted at 2am one night and had to wait for tech services to come in the following morning to get it back up.  I'm glad I didn't do it on a weekend :o

From what I read [here](http://www.mythic-beasts.com/support/macminicolo_howto.html), the intel Mac mini can only boot 'headless' if its _not using Boot Camp_ to boot.  Since I simply couldn't get Ubuntu up and running using EFI in the timeframe I had, I have to boot with Boot Camp.

***Does anyone here know if you can purchase these monitor "dummy" or "cheater" devices anywhere?***  Not only do I not feel comfortable in making one, but I don't have a device to test it on.

---

### Post by matcram on 2006-10-22
thank you for your reply.

Why don't they just give us a standard bios... That's why i hate a little bit my new macmini. At least on standard PCs you can do whatever you want.

I haven't seen any dummy plug to sell on the net but i can promise you that your local electronic shop will do it for you. Mine did it at least ;-)


Has anyone seen an alternativ firmware ?

---

### Post by pafjeje on 2006-11-02
Hi!

I've added a bit about our experience with this issue here: [http://forums.macnn.com/104/alternative-operating-systems/296206/headless-mac-mini-server-using-bootcamp/](http://forums.macnn.com/104/alternative-operating-systems/296206/headless-mac-mini-server-using-bootcamp/)

Regards,
Jeremy

---

### Post by jursoleo on 2006-11-05
boot PC without keyboard  [http://www.versalent.biz/keylim.htm](http://www.versalent.biz/keylim.htm)

---

### Post by pspcz on 2007-07-26
i am bumping this old thread too see if there is any new info on a workaround for this issue?

just discovered it today after dropping $600 to "upgrade" my mini server to an intel

Pz

---

### Post by Expeditor on 2007-09-03
> **pspcz said:**
> i am bumping this old thread too see if there is any new info on a workaround for this issue?

just discovered it today after dropping $600 to "upgrade" my mini server to an intel

Pz

Just joined to advise you of this product which I found that may solve some peoples problems. It solves my problem when I had to replace my Logitech wireless keyboard and mouse. This had the option of using a USB only connection fronm the reciever or via a supplied converter plug, use the 2 PS2 ports. I used the latter simply to:
1. Avoid using a USB post when there were PS2 ports available that would otherwise be unused
2. I have a barcode reader with a keyboard wedge that requires a keyboard to be present to lift a signal line ( my barcode reader doesn't assume this function like some newer devices when a keyboard is absent).

The device I found does just this, is only the size of a 5pin DIN plug and works with my barcode reader. 

The item is the [Multibug]("http://www.multibug.co.uk/keyboard_dummy.html") at £12.50 ex. VAT. For those outside the European Union I don't know if you need to pay this tax or any other import duties, but at about $24.25 that may be acceptable.  If your bios allows you to solve the problem then you don't need this unless you need it for a similar reason as did I, If your bios allows the configuration to boot without a keyboard and your only need is to allow for remote operation you don't need this item. But if your bios doesn't allow booting without a keyboard, then this is a cheap alternative.

Hope this helps some of you.

---

### Post by pspcz on 2007-09-03
we solved this issue with a dongle 

[http://drbott.com/prod/db.lasso?code=0153-GHDD](http://drbott.com/prod/db.lasso?code=0153-GHDD)

a custom boot loader can be developed using EFI as well but that is way over my head

Pz

---

