---
title: "Edgy Upsplash..."
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by blendmaster on 2006-10-28
Hello!

I recently upgraded to Edgy, and everything went well except for the upsplash.

At first when it was restarted, It showed the Ubuntu logo with a progress bar that was split into several pieces, and it did not show startup processes.

Well, I had a startup splash problem before (it showed the Kubuntu startup instead of the Ubuntu one) and I used this code:

```
sudo ln -sf /usr/lib/usplash/usplash-default.so /usr/lib/usplash/usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)

```

to fix it, so I tried it again.

Now when I restart, the splash screen shows a bunch of colors, symbols, and numbers, almost as if it were a screen test. So I'm wondering if there's a code to fix this.

Thank you!

---

### Post by blendmaster on 2006-10-28
Anyone got advice?

---

### Post by Permafrost91 on 2006-11-13
have you tried reinstalling the usplash packages? (usplash and usplash-theme-ubuntu)

---

