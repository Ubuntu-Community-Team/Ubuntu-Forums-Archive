---
title: "Wha?  No Direct Rendering?"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by therunnyman on 2006-06-09
So I glxinfo | grep directed, and found the answer was no, no you don't have any direct rending.

My card, a GeForce4 MX 4000, should be capable of direct rendering.  Any idea on how to get this thing to say yes, we'll direct render for you?  Or is there a way I can, I dunno, like, turn it on?

I tried reinstalling the proprietary driver, legacy drivers, and so on, but this card just ain't cooperating.

Thanks in advance.

runny

---

### Post by Jucato on 2006-06-09
I have exactly the same Video card as you and it worked properly by following this guide: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

I just followed Method 1 and installed nvidia-glx, etc. Try that out.

---

### Post by therunnyman on 2006-06-09
Thanks Fenyx!

---

