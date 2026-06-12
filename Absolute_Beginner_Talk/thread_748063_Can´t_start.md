---
title: "Can´t start"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by Cebonet on 2008-04-07
I´ve tried to install beryl. 

I have found this web page [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon).

I followed the first pages instruktions. I edited this file: /etc/X11/xorg.conf

then after editing it sad that i should restart, and I did. 

Now after the splashscreen, I only get a blank screen. I think the problem is abot the graphiccard configuration( just a guess). Is there any way I can fix this. The grup starts, and I am able to go to recovery mode, but i dont know how to use it?

---

### Post by reyhan on 2008-04-07
maybe you have to know because beryl project is closed and change
to compizfusion project is closed if you want to install compiz fusion go to this link [https://help.ubuntu.com/community/CompositeManager/CompizFusionATI?action=show&redirect=CompositeManager%2FCompizFusiononATI]("https://help.ubuntu.com/community/CompositeManager/CompizFusionATI?action=show&redirect=CompositeManager%2FCompizFusiononATI")

---

### Post by prshah on 2008-04-07
> **Cebonet said:**
> 
I followed the first pages instruktions. I edited this file: /etc/X11/xorg.conf


Your original xorg.conf file will be saved as /etc/X11/xorg.conf[color=red]~[/color]

you can switch back to the original by using:```
sudo mv /etc/X11/xorg.conf ~
sudo mv /etc/X11/xorg.conf~ /etc/X11/xorg.conf

```

---

