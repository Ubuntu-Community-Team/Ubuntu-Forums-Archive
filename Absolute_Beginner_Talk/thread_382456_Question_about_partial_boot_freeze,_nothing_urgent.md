---
title: "Question about partial boot freeze, nothing urgent"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Toxic-Waste on 2007-03-12
Hey there guys!

Ubuntu Linux noob once again! Please don&#8217;t kill me, I need some more help. 

When I Boot my PC (with Dual boot, the other OS is WinXP) screen freezes. It freezes at the exact same time and my hard disk just stops working at this point.

[IMG]http://www.papaspyropoulos.com/img/ubuntu/DSC00723.jpg[/IMG]

So I wait 5 - 10 mins, nothing happens and then I press **Ctrl+Alt+Del** and the Hard Drive starts working again and the loading bar starts moving on!

This is how I have been login on to Ubuntu, ever since I have been using it. I have performed 2 clean installs and I still need to press **Ctrl+Alt+Del** when my screen freezes. Is this normal?

Just for the record the system I am experimenting on is a **Toshiba Satellite A100-192 **(specs. [Here ]("http://gulf.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=AE&com.broadvision.session.new=Yes&PRODUCT_ID=113574")). I have an **ATI Mobility X1600**, a graphics card.

Thanks in advance guys!

---

### Post by Bachstelze on 2007-03-12
When youre at the GRUB menu, select your Ubuntu entry and press e to edit it. Then, select the kernel line and press e again. Remove the "quiet" and "splash" keywords, press Enter to confirm and b to boot. Then tell us what's the last thing you see before it freezes.

---

### Post by Toxic-Waste on 2007-03-12
Ok will do!
I am at work now, so as soon as I get back home to my test machine, I will do what you suggest and write down everything that happens... Or even better I will screenshot everything so I don't make any mistakes.

Thanks a million! :)

---

### Post by Toxic-Waste on 2007-03-17
Don't have this problem any more.
Thanks

---

### Post by Kateikyoushi on 2007-03-17
Could you share with us the way you solved it for other's benefit ?

---

### Post by Toxic-Waste on 2007-03-17
Sorry mate... I changed distros, moved on to OpenSuse 10.2 and in general found things much more stable and "as they should be".  This is why I don't have this and many other problems any more in Ubuntu.

---

