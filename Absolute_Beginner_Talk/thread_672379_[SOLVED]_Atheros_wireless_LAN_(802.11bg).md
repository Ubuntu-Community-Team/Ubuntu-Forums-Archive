---
title: "[SOLVED] Atheros wireless LAN (802.11b/g)"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2008-01-19
I have read that there are sometimes problems with Built-in high-speed Atheros wireless LAN (802.11b/g). I've also heard that the drivers just come up in the restricted drivers manager. Does anyone know for sure? 

I am looking at this laptop for reference [http://www.bestbuy.com/site/olspage.jsp?skuId=8654075&productCategoryId=pcmcat138500050001&type=product&tab=2&id=1195600207253#productdetail]("http://www.bestbuy.com/site/olspage.jsp?skuId=8654075&productCategoryId=pcmcat138500050001&type=product&tab=2&id=1195600207253#productdetail")

---

### Post by Hightide on 2008-01-19
A good place to start is the 'networking and wireless' forum  

[http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136)

:):)

---

### Post by jimrz on 2008-01-19
It depends which Atheros chipset you have. I have 2 with the 5212 chipset that both work "out of the box", meaning they are automatically detected and the restricted driver applied at installation. With this chipset you may, for some cards, need to update your firmware in order to use WPA encryption. One of mine (Netgear WG511T) needed this while the other (IBM onboard a/b/g) did not.

 I have heard that the previous version (5002, I think maybe), which used to work "otb",  now needs ndiswrapper to function properly.

Your link does not specify which Atheros chipset, so a bit of research on the Sony site or, better yet, entering "lspci" (without the quotes) in the terminal will tell you

---

