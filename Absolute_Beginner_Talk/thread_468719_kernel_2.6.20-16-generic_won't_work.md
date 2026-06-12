---
title: "kernel 2.6.20-16-generic won't work"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by shanike on 2007-06-09
after installing all updates to date (9th of july 2007), i can't run kernel 2.6.20-16 at all. xorg.conf messed up dramatically, so instead i'm using kernel 2.6.20-15.
any knowledge base for this?
:(

---

### Post by Outrunner on 2007-06-09
It's best not to use -16. It's pretty broken, and unless it works from the start, I don't think you should try to fix it.It's pointless work. Use what works for you.

---

### Post by southernman on 2007-06-09
> **shanike said:**
> after installing all updates to date **_*(9th of july 2007),*_** i can't run kernel 2.6.20-16 at all. xorg.conf messed up dramatically, so instead i'm using kernel 2.6.20-15.
any knowledge base for this?
:(
Have I been sleeping for a whole month? dagnabbit, not again! :p

Guess I better backup my xorg.conf cause I just installed the update too... 2nd round for the -16 kernel. My first -16 kernel works just fine... hoh humm!

Just waiting on gusty to finish downloading before shutting down.

---

### Post by khardbored on 2007-06-09
This new kernel devoured my X. The only other kernel I have listed in grub is .15. I was using the .16 that was released before this latest one without problem. Not too sure how I can get access back to that previous kernel either. Erg.

---

### Post by southernman on 2007-06-09
> **khardbored said:**
> This new kernel devoured my X. The only other kernel I have listed in grub is .15. I was using the .16 that was released before this latest one without problem. Not too sure how I can get access back to that previous kernel either. Erg.

When booting it should tell you that x can't start and ask if you want to see the log file. Use the tab key to highlight "ok" when it drops you to a console do:

```
sudo dpkg-reconfigure xserver-xorg
```

Go through the steps, accept the defaults if you are none the wiser and you'll be back up pdq.

Thanks to Outrunner for the correction in code. ;)

---

### Post by Outrunner on 2007-06-09
That would be ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by khardbored on 2007-06-09
I would love to do that. However, after I get out of the little ugly blue X windows and get dropped back to a console it asks me to login. I tried logging in with my normal l/p and nothing. I tried logging in as root with my current pw, nothing. They all fail. I know that I am entering the correct information as well. Erg.

---

### Post by Outrunner on 2007-06-09
Hmm, that's strange. Did you try booting into recovery mode? Then type ```
sudo dpkg-reconfigure xserver-xorg
``` as suggested above.

---

### Post by southernman on 2007-06-09
Not sure what you mean when you say I/p, never heard that.

Just use your normal username and passwd.

---

### Post by Outrunner on 2007-06-09
> **southernman said:**
> Not sure what you mean when you say I/p, never heard that.

Just use your normal username and passwd.

He means login/pssword.

---

### Post by southernman on 2007-06-09
> **Outrunner said:**
> He means login/pssword.
Sometimes I wonder how I've managed to live 42 years without getting run over by a big mack truck!

Gawd, I can be thick at times!

Thanks for the heads up, Outrunner.

---

### Post by jmedina on 2007-06-09
I agree. The new version of the kernel has a lot of bugs. I tried install Feisty Fawn and it gives me many errors when trying to boot from the Live CD. But, I installed Edgy and did a Distro Upgrade to Feisty and it boots fine. Other Distros do it too. I hope the next version of the kernel improves.

---

