---
title: "[SOLVED] why, oh why, are Broadcom cards such a pain?"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by kryth on 2008-02-08
My card is fine. But I'm always seeing people having problems with them. Why is this?  They seem to be 'popular' in the sense that a lot of people have them.  And does anyone know if it's going to be fixed or many easier in Hardy?

---

### Post by PeterJS on 2008-02-08
The root of the problem is that broadcom wants nothing to do with open source, they aren't sharing the card specs, they aren't putting in any developers times for oss drivers. So the drivers that exist now are the ndis wrapped  windows drivers that weren't designed for linux at all, and the black box reverse engineered ones that load the firmware. FCC regulations on what you're allowed to open source don't help either, the intel drivers that are the freest of the wireless drivers, have the mandated binary blob that controls transmitting frequency.

---

### Post by Pogeymanz on 2008-02-08
This is semi-related:

Isn't using a firmware cutter legally "iffy"? I think I heard that somewhere.

Also, which is a more efficient method: fwcutter, or ndiswrapper?

---

### Post by stchman on 2008-02-08
Yes, Broadcom like Lexmark have poor support for Linux.  I won't buy either of their products.

Broadcom just needs to make make the specs known so the kernel people can implement a module.

---

### Post by klemens on 2008-02-08
dunno fwcutter, but i have good experiences with ndiswrapper

---

### Post by kryth on 2008-02-08
I wish I had know that intel's wireless drivers were the free-est, I would of upgraded when i ordered my laptop. Oh, well, like I said I've not problems. But I would of liked to given some bucks to ppl that support OSS.

Tangent tangent tanget

Can you 'easily' upgrade a wireless in a laptop?

---

### Post by kryth on 2008-02-08
Oh thanks, for the responses.

---

### Post by The Cog on 2008-02-08
My lappy had an "intel centrino" sticker on it. The wireless has always Just Worked (TM). With every version of Ubuntu I since Breezy. Some intel video does he 3D stuff out of the box too.

---

### Post by chirulais on 2008-02-08
> **EmosSuck777 said:**
> This is semi-related:

Isn't using a firmware cutter legally "iffy"? I think I heard that somewhere.

Also, which is a more efficient method: fwcutter, or ndiswrapper?

NDISWRAPPER ALL THE WAY!
 see fwcutter cant connect at long distances from the router while ndiswrapper can.

---

### Post by PeterJS on 2008-02-08
Yeah centrino wireless (ipw2x00 and ipw3945), were the cards I was referring to, and they've just worked for several versions now(all the ones I've used), also intel likes to use their own or nvida graphics cards, the whole ATI/AMD merger kinda put a damper on that, the intel cards just work, and the nvidia binary support isn't bad. Someday the ATI oss radeon-hd driver will be better and open source, but that day is not today, or any time this year, next year's not looking so good either I hear.

---

