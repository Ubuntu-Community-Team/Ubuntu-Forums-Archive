---
title: "ctx Tvstudio xtra MT002, how do I install"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by blackbottom48201 on 2007-03-18
where do I begin to install the ctx Tvstudio xtra tv capture card???

also Totem is installed but I cant play any dvd movies why not?

---

### Post by crispy_420 on 2007-03-21
DVD's, atleast commercial, require libdvdcss. Just look for a guide on howto install on these forums. You may need some other files installed to, like DVD read/navigate. And in my opinion, pick a different player for DVD watching. I recommend VLC or xine. They both support DVD menus where I don't believe totem does.

Do you know what chipset that tv card has? Run either dmesg or lspci from command line. If recognized, it should list the chipset and we will go from there.

---

### Post by blackbottom48201 on 2007-03-22
Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)

---

