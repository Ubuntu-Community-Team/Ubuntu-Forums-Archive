---
title: "Good Video Card?"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Funk Soul Brother on 2007-02-20
Hi Everyone,

I'm a total hardware dummy (and Linux dummy, to boot). Wondering what might be a good choice for a video card.

I need one that has about 256MB of RAM and can do OpenGL rendering. I have an old P4 IBM NetVista and the onboard Intel integrated video card will not allow me to run xserver.

Any ideas? I'd like to install Edgy Eft on this thing!

---

### Post by madmetal on 2007-02-20
i suggest nVidia and something like 6600 or 7600 if you dont want to give much money away..

---

### Post by Funk Soul Brother on 2007-02-20
madmetal,

Thanks! Will I have to edit the xorg.conf or whatever file to get that thing fired up? I'm kindof a hack when it comes to command line file editing. I wreck a lot of stuff.

---

### Post by kelbizzle on 2007-02-20
If your looking for a cheap card that will work. Check out [www.geeks.com](www.geeks.com) they have really cheap stuff. You could probably find a Geforce4 card there for under 60 bucks.

---

### Post by MystaMax on 2007-02-20
I'd also recommend nVidia cards. I've got a quadro in my laptop and works great. I'd check [newegg.com]("http://www.newegg.com/Product/ProductList.asp?Category=38&N=2010380048+4017&Submit=ENE&SubCategory=48&Description=NVIDIA&Ntk=all"), they have really good prices and wide selection.

---

### Post by kelbizzle on 2007-02-20
```
sudo dpkg reconfigure xorg
```


You might be able to fix your issue with reconfigure.

---

### Post by madmetal on 2007-02-20
> **MystaMax said:**
> I'd also recommend nVidia cards. I've got a quadro in my laptop and works great. I'd check [newegg.com]("http://www.newegg.com/Product/ProductList.asp?Category=38&N=2010380048+4017&Submit=ENE&SubCategory=48&Description=NVIDIA&Ntk=all"), they have really good prices and wide selection.

its damn that newegg does not ship to europe... :mad: 
well i use a FX5500 with no problems till now..
Quadro is great for rendering!

---

### Post by click4851 on 2007-02-20
heck I'm using a MSI FX5900 and it does great. Nvidia all the way.

---

### Post by kelbizzle on 2007-02-20
> **madmetal said:**
> its damn that newegg does not ship to europe... :mad: 
well i use a FX5500 with no problems till now..
Quadro is great for rendering!

[www.geeks.com](www.geeks.com) ships internationally.

---

### Post by ed-j on 2007-02-20
I've added a GeForce 7600GS (passive heatsink or "silent") which saves on the noise and the electric. The Binary Drivers for this are in 6.1 so you don't even have to go to the Nvidia website! I'm a Novice, but this card is allowing me to play with Ubuntu 5.1, 6.06 and 6.1: I've just installed KDE on top of 6.06 as my latest experiment. You can have effects frothing out of your keyboard and more eye-candy than you can Shake-a-Stick at!!

All the best. (By the way: Wicked Picture!)

---

### Post by Funk Soul Brother on 2007-02-20
ed-j,

Thanks - the pic is not really me - I just wish I could have hair like that. I'm really a Scotsman with no rhythm or jive.

Thanks for the tip on saving on power usage. I'm also a bit of a greenhead and I don't want my hardware to contribute to climate change! Ha ha!

---

### Post by Funk Soul Brother on 2007-02-20
And if Greenland melts and the Gulf Stream shuts down, you poor bastards in Wales are going to freeze your arses. So here's to us Canadians thinkin' of ya!

---

### Post by ed-j on 2007-02-20
> **Funk Soul Brother said:**
> And if Greenland melts and the Gulf Stream shuts down, you poor bastards in Wales are going to freeze your arses. So here's to us Canadians thinkin' of ya!

Not a chance! I'll apply for a gold-mining license North of you in Brodeur Pen. Pob hwyl brawd! (All fun brother!)
Are you sure that's not a photo of you? I saw a very similar looking Clansman playing his Pipes on the A1 border to the highlands (this was during the World Cup) standing by a sign that said "Cafe -->, half-price breakfast for Brazilians".

Hope your new graphics work out!

---

### Post by Funk Soul Brother on 2007-02-20
ed-j,

Ha ha! You wail (like Bill and Ted)! Thanks for the kind help. I will outfit my machino with the card you suggested.

Thanks everyone in this thread - this forum is hardcore.

---

### Post by RanDinCarolina on 2007-02-20
anything Nvidia has been easy for me........

---

### Post by Motoxrdude on 2007-02-20
Well, if you haven't ordered a card yet, i would highly suggest getting a nvidia card. It is all about your price range, but stay away from the 6000 series. I would look into getting either a 7600GT or a 7800GT. If you want to spend a little more then get a 7900GT.
But if you are just a casual gamer and are happy with games like WoW a 7600GT would be perfect.

---

### Post by rusty4r on 2007-02-21
I'm not a gamer but Beryl runs great on my old PNY/NVidia GeForce2 MX 400, in Dapper and Edgy, with only 64 meg.

---

### Post by Funk Soul Brother on 2007-03-03
Ok - here's the solution:

The NetVista workstation is an off-lease workstation - so the vid card is not really built for bleeding edge stuff. It's all about looking at what the machine was built to do... this one was made to run M$ Office. Period.

So I bought a $70 (CAD) EVGA e-GeForce 6200LE AGP card - slammed it in and the motherboard automatically disabled the on-board beater card (just like the Intel site said it should).

And the Edgy install went without a hitch - I'm typing this from my new desktop.

The Canonical team has identified this problem with video cards as a critical issue so they are hard at work to fix it.

But in the meantime - I now have a card that can do the kind of Open GL rendering that I would need to use Beryl - COOL!

---

