---
title: "Conky &amp; File Space"
date: 2009-10-25
forum: Art &amp; Design
---

### Post by EdGy28376 on 2009-10-25
Well after spending most of the day. I realize I might need some assistance.
I am trying to configure Conky (which is awesome) to show file space used by percentage for individual users. However if it seems Root always mirrors others.

Here is the code I have in conkyrc file:

Root: ${fs_used_perc /} ${fs_bar 6 /}$color
home: ${fs_used_perc /home} ${fs_bar 6 /home}$color
sda6: ${fs_used_perc /dev/sda6} ${fs_bar 6 /dev/sda6}$color
Root: ${fs_size /} ${fs_used /}

I am using version 1.7.2

Any comments will be apprecaited.

Thanks~

---

