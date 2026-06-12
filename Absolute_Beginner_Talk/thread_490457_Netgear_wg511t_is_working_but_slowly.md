---
title: "Netgear wg511t is working but slowly"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by GregoryMA on 2007-07-02
I recently installed a netgear wg511t wireless pcmcia card in my laptop.  It worked out-of-the-box but it is working slowly.  I think it is using propritary software.  Could that be why?  Should I use NDISwrapper?  Any help would be appreciated. 
Thanks, Greg.

---

### Post by arijarot on 2007-07-02
I'm no expert, but when this happens, my first go to solution would be to restart the wireless router.

---

### Post by GregoryMA on 2007-07-02
I tried restarting the router but it is still only running at 16kb/s.

---

### Post by Seisen on 2007-07-02
You can try using madwifi.

---

### Post by GregoryMA on 2007-07-04
How do I use madwifi?  I have looked around abit but there is not much info for feisty.  Most places say 'it just works'.  Do I have to download it or is it part of the distro?

---

### Post by betterspud on 2007-07-04
I'm not really an expert with these things, but I too have a WG511T card. My card was instantly recognised by Ubuntu and connected with no fuss at full speed. That might suggest that it's the router's settings that are limiting it's speed. It might be worthwhile checking everything there before making any changes within Linux.

---

### Post by arijarot on 2007-07-04
it's part of the kernel actually, for example, linux-restricted-modules-2.6.20-15-generic includes madwifi (Atheros). you can find it in synaptic...

---

### Post by GregoryMA on 2007-07-04
I think it is the router.  I am at a loss when it comes to adjusting the settings though.  I have never touched the thing.  Can anyone help?

---

### Post by arijarot on 2007-07-04
> **GregoryMA said:**
> I think it is the router.  I am at a loss when it comes to adjusting the settings though.  I have never touched the thing.  Can anyone help?

IMO, I would reset it.

---

### Post by GregoryMA on 2007-07-07
That worked.  Tres easy.  Thanks everyone for your help!
Greg.

---

