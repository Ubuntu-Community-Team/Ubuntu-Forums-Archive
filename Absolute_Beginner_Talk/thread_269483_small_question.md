---
title: "small question"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by Asaf_Shilat on 2006-10-01
hello,
i really want to install ubuntu on my leptop, but when i use the live cd, it doesnt read my usb wierless adaptor.
without it i cant connect to the internet.
is there anything i can do in order to make it work with the live cd and just then install it?

i gess thet u'll need more info. tell me what u need and i'll try to get it...

thanks

---

### Post by Mr Frosti on 2006-10-01
Specifically, what type of wireless adapter do you have in your laptop? This can be found out by running the following in a terminal:

```
lspci | grep Network
```

If it is a Broadcom, there are some instructions on the Ubuntu forums to use "ndiswrapper" and the Windows drivers. Also, I believe any changes made to the Live CD are gone once the installation completes and you restart your machine.

---

### Post by Asaf_Shilat on 2006-10-01
hey,
i write the command and it does nothing. it just starts a new line.
this is "level one" wireless adaptor model model: WNC-0300USB

any idea?

---

