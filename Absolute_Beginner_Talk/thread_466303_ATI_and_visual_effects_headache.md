---
title: "ATI and visual effects headache"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by phollos on 2007-06-06
Brand new linux user and I'm not quite sure what to do.
I'm interested in "spicing things up" a bit (I absolutely love expose from the mac OS, and it would be nice to have window transparency) but it seems like I'm out of luck on an ATI card.

If I install the fglrx drivers under restricted drivers everything looks nice and crisp but it doesn't have "composite" so beryl and compiz won't work, and neither will other addons such as skipper (basically expose).

If I install the generic ATI driver I can get effects working, but everything seems sluggish and renders choppy (like when I scroll in a firefox window I see choppy lines).

So what am I to do? Will there ever be a time when this is fixed and I can enjoy the best of both worlds? Is there a workaround? Or am I stuck eyeing the greener grass on the other side?

---

### Post by mcduck on 2007-06-06
Fglrx drivers work fine with XGL, so it's possible to run Beryl/Compiz with them. It requires a bit extra work to install, but works great.

---

### Post by Rocket2DMn on 2007-06-06
If you are using a Radeon card, check out this link for getting Beryl setup.  I used it and it works great, just double check their list to make sure your card is supported.
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")

---

### Post by phollos on 2007-06-06
Running an X800 card so it's supported.

Rocket2DMn's link includes
"AIGLX with open-source ATI driver instead of XGL with the proprietary ATI driver (fglrx)"

but (at least for me) the open-source ATI driver makes things look choppy and sluggish. It looks like I want to use fglrx and XGL which I didn't think was possible.

Could you link a guide mcduck? It's nice to know that it's possible. I've been trying to find a tutorial that allows fglrx and compiz but I've had absolutely no luck.

---

### Post by mcduck on 2007-06-06
Here's the guide I've used. Worked fine for my both Ati cards (9600XT and Mobility X1600) [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL")

---

### Post by phollos on 2007-06-06
I'm up and running!

Thank you Rocket2DMn and mcduck for the quick replies!

---

