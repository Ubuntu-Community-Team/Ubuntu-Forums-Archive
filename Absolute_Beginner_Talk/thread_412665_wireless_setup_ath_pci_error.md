---
title: "wireless setup ath_pci error"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by metaphor- on 2007-04-18
Greetings,

I am trying to get my wireless to work, on edgy eft with a wda-2320 card. After running "make install" from the madwifi directory, then following up with the "modprobe ath_pci" command i get the following error,

" Fatal:error inserting ath_pci (/lib/modules/2.6.17-10-generic/net/ath_pci.ico): Unknown symbol in module, or unknown parameter (see dmesg)"

dmesg at the end shows a page in a half of ath errors...

what am i doing wrong? how can i get my net to work? any help would be appreciated ! 

Thanks.

its an ath0 chipset

---

### Post by ayenack on 2007-04-18
Is wda the make of the card? If not please give the actual make of the card. I'm guessing this is a D-Link card let me know.

---

### Post by metaphor- on 2007-04-19
yes it is  a d-link card

---

### Post by ayenack on 2007-04-19
Is it there? Try this in a terminal and see if it's listed **lspci**

This is just a punt in the dark but may be worth a try.

As you probably know this card will not work with ndiswrapper. There's a serious issue with this card. I've been looking on the net and this is the general advice I can find.  *"You've used mad-wifi which should work but I have a feeling that the native drivers for atheros cards is messing thing up here. This might sound crazy but you might want to un-install mad wifi and then re-install it and tell it to re-install your card. Do not change the config because it will try and config for native drivers and will make mr.card not work again"*. This might work.

If this does not work you may want to go and buy a new card check [WifiDocs]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") for Ubuntu supported cards.

Best of luck. ayenack.

P.S. Just because you're paranoid doesn't mean people aren't looking at you. Reference to the insane people quote.

---

