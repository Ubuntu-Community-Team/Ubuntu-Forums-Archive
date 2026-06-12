---
title: "Video card replacement: advice / how to reinstall"
date: 2005-08-16
forum: Absolute Beginner Talk
---

### Post by teapot on 2005-08-16
I can't get any help on my video problems, so I'm thinking of getting a video card. Can anyone recommend one that will work with Ubuntu reliably? I don't need high-end 3d, just a supported card for watching dvds and surfing.

And once I get one, what do I need to do to Ubuntu to get the card to work?

---

### Post by KingBahamut on 2005-08-16
Nvidia AGP 5500 256. 

Ive got one, runs with the Free Nvidia drivers on the Repositories. 

I think you can pick one up off of newegg.com for about 85 bux.

---

### Post by Strongbad on 2005-08-16
I am running an agp pny technologies verto and it works very well. you could probably find one on e-bay for a good price. To set it up, just type "sudo dpkg-reconfigure xserver-xorg". From there it's pretty simple. Good luck!

-Strongbad-

---

### Post by kostkon on 2005-08-16
As you don't need such a powerful card, just go for a fairly good Nvidia card, like a Nvidia 4 mx. You can find one on eBay for just 25-35 euros.

Then, you can even have 3d acceleration (even if you don't need it) because is very easy to install the nvidia driver with Synaptic. Or you can just use the 2d only driver provided with Xorg by doing a *sudo dpkg-reconfigure xserver-xorg*, like Strongbad suggested.

Try to avoid buying a Ati, you'll get into problem otherwise. Do a search here in this forum and you'll understand why!

That's all, hpe I helped in some way.

---

### Post by kostkon on 2005-08-16
Oh and something else!

Specifically for watcing DVDs or divxs, I can say that I haven't found a media player in Linux that actually uses the hardware mpeg decoding acceleration capabilities of the nvidia or ati cards, even if you use the official drivers. Maybe it's a problem of the drivers in linux and not a media player problem... It's my opinion, I don't know if this is a 100% true fact...

Thus, it doesn't matter if you get a Nvidia FX or a Nvidia 4 mx.

---

### Post by teapot on 2005-08-17
Strongbad, Thanks for the info and installation advice!

Koston, Thanks for the Nvidia info and advice!

From other stuff I've seen, it seems the only recommendation usually given for Linux is Nvidia. I'd certainly caution anybody AGAINST relying on SiS video chipsets on Asus motherboards. I know some people have gotten them to work, but theres like zero performance compared to an add-in board from what I've seen.

Thanks again, guys.  :-P

---

