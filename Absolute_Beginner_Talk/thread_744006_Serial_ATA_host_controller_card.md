---
title: "Serial ATA host controller card"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2008-04-03
Can anyone help me find a eSata card that is supported by Ubuntu/Linux?

I am talking about a card like this one:
[http://www.edbpriser.dk/Products/listprices.asp?ID=437056](http://www.edbpriser.dk/Products/listprices.asp?ID=437056)

(Danish site, but here is the description)

> This Serial ATA host controller card is designed to offer a high performance, cost effective and reliability solution to user who needs to accommodate storage peripherals with the new Serial ATA interface. This card supports the Serial ATA (Generation II) transfer rate of 3.0Gb/s (300MB/s). This card provides only two SATA channels. 

I am helping a friend find a cheap card like this, that we can know for sure is supported..  

Any Help would be much appreciated. :)

---

### Post by AflingZ on 2008-04-03
yeah well I am the friend that needs the card :P (but thanks for making the thread mate)

But yes, its a card like that one, but the problem is, I need to be sure that it has drivers for ubuntu :)

edit: oh and I forgot to say, it doesnt need to be eSata, just sata or sata II :) if its external doesnt matter actually :) so I better example would be like this: [http://www.edbpriser.dk/Products/Listprices.asp?ID=205909](http://www.edbpriser.dk/Products/Listprices.asp?ID=205909)

---

### Post by njparton on 2008-04-03
Maybe you could use one of the cheaper highpoint PCI or PCIE raid cards and just not set up any raid arrays?  Your individual drives should still show up.
 
Highpoint have 2.6 kernel drivers available for most of their raid cards.
 
Check out their website.

---

### Post by AflingZ on 2008-04-03
I don't actually understand what you mean, sorry. Those highpoint are made for raid? And then buy them but don't set them up as raid.. ?

---

### Post by njparton on 2008-04-03
Yes, buy a cheap raid card but don't set up the hard drives in raid and linux should see the individual drives.

---

### Post by StOoZ on 2008-04-03
I use this one ,as reported by linux:
> Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)

automatically detected on ubuntu istallation, my DVD burner is connected to it, works like a charm.
both eSATA and SATA.

---

### Post by AflingZ on 2008-04-04
I was thinking about this one: [http://edbpriser.dk/Products/Listprices.asp?ID=100368](http://edbpriser.dk/Products/Listprices.asp?ID=100368)
[edit]but now I see the delivery status is bad.. so I have to find another one.[/edit]
It has Silicon Image 3114 as chipset, and is very cheap, but is it supported? I guees [this one](http://www.newegg.com/product/product.aspx?Item=N82E16815124020) is about the same, but I am not sure.. I see the drivers works for that one :)

edit2: [http://edbpriser.dk/Products/Listprices.asp?ID=390015](http://edbpriser.dk/Products/Listprices.asp?ID=390015) this one has 2-3 days delivery and the same chipset, so I hope it will work?

---

