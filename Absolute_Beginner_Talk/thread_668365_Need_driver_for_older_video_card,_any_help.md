---
title: "Need driver for older video card, any help?"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by hoovie26 on 2008-01-15
I've installed Gutsy on my computer, which due to a Nvidia graphics card going bad, has had an older Hercules 3d Prophet 4500 installed in it for some time.  Unfortunatly, it appears that there are no drivers available for the current linux kernel.

Does anyone know where I might be able to find a compatible open source driver for this graphics card, or if anyone would be interested in writing one?

Thanks

---

### Post by gn2 on 2008-01-15
Why not just ebay the Hercules and get another nvidia card?

---

### Post by jeffus_il on 2008-01-15
The following two threads reference your card, seems that you are stuck with the vesa driver, 
edit your /etc/X11/xorg.conf, 

under "Section Device" 

change the 
Driver  "xxxxx"
to 
Driver  "vesa" 

[http://ubuntuforums.org/showthread.php?t=216675](http://ubuntuforums.org/showthread.php?t=216675)
[http://ubuntuforums.org/showthread.php?p=2172605](http://ubuntuforums.org/showthread.php?p=2172605)

---

### Post by hoovie26 on 2008-01-15
in regards to putting the hercules on ebay, it wouldn't even put a dent in the bill towards replacement, not to mention that my mobo is AGP.  my next card purchase will be a PCI-E, since I don't have the wallet for a new PC yet....I make do :)


As for the VESA drivers, I was afraid of that.  Oh well, I'll deal for now until I can build myself a new box.  thanks for the prompt replies.

---

### Post by gn2 on 2008-01-15
There are still some AGP cards available and they're cheap. [http://tinyurl.com/32823h](http://tinyurl.com/32823h)

If you're in the UK and interested in a used MSI FX5600VTDR128 for £10 plus p&p PM me an e-mail address and I'll send you a PayPal invoice.

---

### Post by hoovie26 on 2008-01-15
You're right, those are pretty cheap.  Unfortunatly, I'm in the US, so I'd imagine shipping would be more than the card cost, though I do appreciate the offer.

---

### Post by jeffus_il on 2008-01-15
So in the Us, you can do even better, the not so late model Nvidia cards are inexpensive and good for moderate gaming.

---

### Post by gn2 on 2008-01-15
There's cheap ones in the US too: [http://tinyurl.com/35nnuf](http://tinyurl.com/35nnuf)
Given the $-£ exchange rate, they're even cheaper than the ones I linked to before!

---

### Post by hoovie26 on 2008-01-15
I've just been putting off any hardware purchases for as long as possible - the more my wife gets fed up with the current box, the better the computer I can put together later on ;)

---

### Post by jeffus_il on 2008-01-15
> **hoovie26 said:**
> I've just been putting off any hardware purchases for as long as possible - the more my wife gets fed up with the current box, the better the computer I can put together later on ;)

Advice on how to deal with your wife is a little beyond the scope of the forum, makes these little technical problems sound easy, Good Luck! :)

---

