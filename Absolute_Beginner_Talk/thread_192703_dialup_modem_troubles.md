---
title: "dialup modem troubles"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by tollbooth on 2006-06-09
I've been having some problems with the pci modem that I have installed, I know ubuntu sees the modem, I did not have to use scanmodem, but I did use it anyway, I did look on here about the howto stuff, but I cant get it to work.
I did not do anything with installing drivers or anything like that.

The modem is a ESS Technology ES2838/2839 Superlink modem
When I was reading thru the stuff I may of missed something.
Thanks for the help

---

### Post by jason.b.c on 2006-06-09
> the pci modem that I have installed

It's a winmodem, It probably won't work..

External one's do though..;)

---

### Post by tollbooth on 2006-06-09
hmmm....ok, I kinda thought so, but I do have another pci modem thats a conexant, havent thrown it in yet to see what it is exactly, and Ive seen drivers and such for conexant modems. Would that work, I guess I'll know when I throw it in and play around with it.

---

### Post by jason.b.c on 2006-06-09
[QUOTE=tollbooth]hmmm....ok, I kinda thought so, but I do have another pci modem thats a conexant, havent thrown it in yet to see what it is exactly, and Ive seen drivers and such for conexant modems. Would that work, I guess I'll know when I throw it in and play around with it.[/QUOTE]

You could try, But i would seriously doubt it..

I think what everyone here will tell you is to go with an external one and be done with it..

=D>

---

### Post by tollbooth on 2006-06-09
Alrighty, well thanks for the help anyway

---

### Post by Omnios on 2006-07-07
Hi my dad has a similar modem superlink es 1838 2839 and it works with out  any additional drivers. The problem he had was that with 5.10 his modem port was detected as .....14 but using 
 $ sudo wvdialconf /etc/wvdial.conf

 He found his modem is not on ......4 

 After fixing this his modem worked perfectly with out any adition effort.

---

