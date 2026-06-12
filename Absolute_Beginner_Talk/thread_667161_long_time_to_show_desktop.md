---
title: "long time to show desktop"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by kalya_kvs on 2008-01-14
Hi 

Can any body help in solving the problem. Why Ubuntu is taking long time to Boot up. When I select Ubuntu generic option. It takes 10-15 mins for desktop to appear. 

I am using Toshiba Tecra A4 loptop. 1.5 gb ram. 160 gb hdd. Dual boot.
Xp pro. 1.6 ghz intel.

Please can any body assists.

Thanks

Krish

---

### Post by kpkeerthi on 2008-01-14
You may switch to textual boot mode and see if anything apparent is causing delays.

From GRUB, highlight the boot option (the kernel line), press 'e' to edit. Using navigation keys scroll to the end and delete the word **splash**. Press <enter> and then 'b' to boot. This will put you in text mode for this session only and you can watch the boot messages.

---

