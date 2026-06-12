---
title: "WIFI with Nintendo DS through ubuntu box"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by feap on 2006-09-19
I'm trying to connect my Nintendo DS to the internet via my ubuntu box. The box is connected to the internet via LAN. My DS recognizes the other wifi connections in the area, but I can't get the ubuntu wifi to show up at all. I'm new to ubuntu and wifi, also.

The main problem appears to be that I'm not sure whether the "wireless connection" settings in "network settings" refers to outgoing or incoming connections. It seems that it's outgoing as I can see another wifi connection in "network name ESSID".

So, how do I set up the 3COM wifi router to accept incoming connections? I've tried putting in random info in "network name ESSID" and "WEP Key" and using the same info in my DS, but it still doesn't work (or show up in connections).

---

### Post by sguart on 2006-09-19
for the ds wifi connection, please refer to nintendo's wifi connect page.

thanks,

sg

---

### Post by Frak on 2006-09-19
Try samba

---

### Post by compuguy1088 on 2006-09-19
> **Frak said:**
> Try samba
I don't think samba is what is needed to get your DS connected wirelessly...what your probibly looking for is to set up a wireless router with a WEP key, independent of another router, or mabe some Linux package that could make it emulate a router....

---

### Post by feap on 2006-09-19
> **compuguy1088 said:**
> I don't think samba is what is needed to get your DS connected wirelessly...what your probibly looking for is to set up a wireless router with a WEP key, independent of another router, or mabe some Linux package that could make it emulate a router....

Yes, that's my understanding, as well. The problem doesn't seem to be the DS as I see and have played with other wifi connections. I just need to set up  a wireless router on the ubuntu machine to which the DS can connect.

---

### Post by DiJEH on 2006-09-20
I had this problem a few days ago.. It took ages to fix and was a hell of a problem. Basicly even if I had WEP on (which the DS is ment to be able to use) it refused to work, but the second I turned it off it worked perfectly. You may want to try turning WEP off for a few minutes and see if it helps your DS at all.

Other wise play with the settings untill it works.

---

### Post by feap on 2006-09-20
> **DiJEH said:**
> I had this problem a few days ago.. It took ages to fix and was a hell of a problem. Basicly even if I had WEP on (which the DS is ment to be able to use) it refused to work, but the second I turned it off it worked perfectly. You may want to try turning WEP off for a few minutes and see if it helps your DS at all.

Other wise play with the settings untill it works.

Thanks for confirming that DS actually works with ubuntu! Do you mean I should play with the network settings under "wireless connection"? And how do I turn off WEP? Is it just by _not_ entering a WEP Key?

---

### Post by Frak on 2006-09-21
> **feap said:**
> Thanks for confirming that DS actually works with ubuntu! Do you mean I should play with the network settings under "wireless connection"? And how do I turn off WEP? Is it just by _not_ entering a WEP Key?
Exactly

---

