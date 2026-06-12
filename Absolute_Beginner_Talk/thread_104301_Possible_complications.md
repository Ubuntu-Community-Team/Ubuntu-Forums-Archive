---
title: "Possible complications?"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by user12191 on 2005-12-15
Hello everyone, I'm new to Ubuntu and fairly new to linux. 

[I've only installed Fedora Core 4 in the past and used a few Live CDs.]

Anyway, I'm getting a new computer tomorrow, and I was told that I didn't need an ethernet card because there was a "LAN chip" in the motherboard. [This](http://www.newegg.com/Product/Product.asp?Item=N82E16813130493) is my motherboard. 

Would anyone mind tell me how a "LAN chip" differs from an ethernet card, and if there will be any more hassle than there normally is when I try to set up Ubuntu?

If it matters any, I've googled already and haven't found much. I've also done a search here and it didn't turn up anything I could recognize as similar to this.

Thanks.

---

### Post by Zelut on 2005-12-15
sounds like you just have an onboard LAN instead of a physical card.  That shouldn't cause any problems--it hasn't on any of my systems.  I only have a LAN card in 1/3 of my boxes and neither of the other two have any problems.

---

### Post by Arktis on 2005-12-15
It means that the ethernet is onboard (built into the motherboard) just like most motherboards now come with onboard sound, usb, etc.

I suspect that your onboard ethernet isn't going to be detected by ubuntu since your motherboard is fairly new.  I'm not sure though, because I don't have that board.  I just recently got a new mobo and the onboard lan doesn't show up.  For my last mobo, I think I had to install nforce drivers to get it to show up, but the board you have is nforce 4 and I don't think there are any linux drivers for nforce 4 yet.

You may be better off just using a pci ethernet card.

---

### Post by user12191 on 2005-12-15
Thanks for the explanations.

I have an ethernet card I can use if Ubuntu doesn't recognize what's on the motherboard.

Thanks again.

---

### Post by Arktis on 2005-12-15
Good, you should use that anyways.  Onboard stuff tends to steal cpu cycles, slowing down the machine.

---

### Post by MetalMusicAddict on 2005-12-15
[QUOTE=Arktis]Good, you should use that anyways. Onboard stuff tends to steal cpu cycles, slowing down the machine.[/QUOTE]
Oh come on man. It would be minimal. :) You could look at it this way; Using another PCI card would use more power.

I myself tend to like most onboard devices (minus GFX cards) because it takes up less room in my case and has tended to work out-of-the-box more for me with linux. IMHO :)

---

