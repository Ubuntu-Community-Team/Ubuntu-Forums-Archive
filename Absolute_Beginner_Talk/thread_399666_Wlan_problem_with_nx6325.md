---
title: "Wlan problem with nx6325"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by kaupoke on 2007-04-02
Hi, I'm totally new here. I've used ubuntu a couple of times and love it.
I just had my friend install Feisty Fawn on my notebook. Everything works just fine, it recognises the brodacom card. It even recognises the wireless networks,but can't connect to them.

any ideas?

HP Compaq nx6325
AMD Sempron 3500+
NetXtreme BCM5788 Gigabit Ethernet
512mb
60Gb 
Radeon Xpress 200M

...or something like that...
would appreciate any help you can give me...:confused:

---

### Post by Kobalt on 2007-04-03
Can you give us the exact model of your wifi card ? You can find it out in the list using this command line ```
lspci
```

---

### Post by Markio on 2007-04-06
Hi,

I have the same laptop, couldn't get the bcm43xx driver working so I'm using ndiswrappper.

I used the guide [here]("http://vale.homelinux.net/wordpress/?p=106").

Good luck.

---

### Post by kaupoke on 2007-04-09
Broadcom Corporation BCM4310 UART (rev 01)

I tried Valentino's install guide, but I got messed up and confused, so I decided to wait for Feisty with a new kernel, that should recognise BCM cards..or at least some of them..right?

(I can access the internet by a wire tho..)

---

### Post by wolfchri on 2007-05-31
@kaupoke:

Try my latest HowTo for Feisty on the NX6325 - it is now much smaller, less confusing, as Feisty already solves the worst issues:

[http://vale.homelinux.net/wordpress/?p=144](http://vale.homelinux.net/wordpress/?p=144)

Hope this helps.

---

