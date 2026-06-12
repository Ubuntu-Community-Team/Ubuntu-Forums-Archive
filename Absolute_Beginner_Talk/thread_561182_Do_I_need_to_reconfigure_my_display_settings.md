---
title: "Do I need to reconfigure my display settings?"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-09-27
I want to exchange monitors with my PC moving from an AOC to a Compaq.

Do I need to reconfigure anything (both are CRT) or just a simple swap?

---

### Post by w4ett on 2007-09-27
Unless you are using some outlandish refresh rates on your old CRT (outside the 60-85 range) you will be ok...

---

### Post by chrome307 on 2007-09-27
I did check the configuration and the AOC is listed ....... backed it up just in case LOL

Thanks for getting back to me so quickly :)

---

### Post by w4ett on 2007-09-27
No problem...next time I'm in London, you can get me a pint and a pork pie.

---

### Post by chrome307 on 2007-09-27
LOL ......... spoke too soon ........... I had to reconfigure the display again and ended up with the CLI

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Not too worry, I think I'll give it miss and wait until the next release later next month before starting over again.

LOL ......If your over in East London, you can have pie/mash & liquor with your pint e :)

---

### Post by w4ett on 2007-09-27
> **chrome307 said:**
> LOL ......... spoke too soon ........... I had to reconfigure the display again and ended up with the CLI

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Not too worry, I think I'll give it miss and wait until the next release later next month before starting over again.

LOL ......If your over in East London, you can have pie/mash & liquor with your pint e :)

Well the edid data will be different on the new monitor a

```
sudo dpkg-reconfigure  xserver-xorg
```

and letting the new monitor autodetect should clear up your problem.

P.S I used to live on New Compton Street, just off Oxford Circus. :)

---

### Post by chrome307 on 2007-09-27
I did do that and the monitor was fine but it failed to pick up the ATi graphics card so I chose VESA and then editted the config file with my ATi details that I had backed up previously ...... just ended up with the CLI upon reboot.

Not to worry, I was planning on upgrading in the future anyway.  So it gives me more experience in setting it up again .... I'll wait for Gutsy Final to do this.

Oxford Circus ........... how could you put up with the noise/crowds etc .......... I'm over in Redbrige (Roding Valley) near Essex much quieter and sedate ... LOL

We've just got this new fangled invention called television here some are predicting it will **"threaten to change us into creatures with eyeballs as big as cantaloupes and no brain at all"** :lolflag:

---

