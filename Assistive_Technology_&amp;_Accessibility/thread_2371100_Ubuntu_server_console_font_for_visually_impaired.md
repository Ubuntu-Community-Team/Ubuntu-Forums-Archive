---
title: "Ubuntu server console font for visually impaired"
date: 2017-09-10
forum: Assistive Technology &amp; Accessibility
---

### Post by holiday2 on 2017-09-10
Hi
I have difficulty with small fonts. Even with strong glasses.
So I always bump up my font size in all displays.

I want to keep a small profile server running on my LAN for some services so have installed Ubuntu server. I know I can tinker with bash settings but it seems rather complicated. 

Does anyone have a bashrc that will give larger fonts, preferably with a bright color?

Or simple advice on how to tinker.

Thank you.

---

### Post by alexarnaud on 2017-11-11
Hello,

The best way to configure configure is the following command in root or sudo :
"dpkg-reconfigure console-setup"

You will be able to switch to the terminus or terminus bold font and to switch font size to 32.

For me the simple way is to access via SSH to the machine I have to manage.

Best regards.

---

