---
title: "dual boot - grub not loading kernel"
date: 2007-10-26
forum: Apple Intel Users
---

### Post by phuturism on 2007-10-26
I have a dual boot macbook partitioned with boot camp so you get the mac/windows icons at startup - select windows, and it launches grub then ubuntu.  

Recently though grub just sits there.  Doesn't load the kernel.  I couldn't even type into the grub command line but after updating firmware I now can.  

Can I "repair" grub from the command line so it loads the kernel?

Thanks

---

### Post by cyberdork33 on 2007-10-26
> **phuturism said:**
> I have a dual boot macbook partitioned with boot camp so you get the mac/windows icons at startup - select windows, and it launches grub then ubuntu.  

Recently though grub just sits there.  Doesn't load the kernel.  I couldn't even type into the grub command line but after updating firmware I now can.  

Can I "repair" grub from the command line so it loads the kernel?

Thanks
um.. maybe. but it depends on what the issue is. Can you try choosing different kernel choices?

When you highlight an entry in grub, you can edit the entry by pressing 'e' the changes you make will not be saved though, you would still have to edit the menu.lst file.

---

### Post by phuturism on 2007-10-26
Ok, thanks.  It doesn't offer any entries - it just gives me a grub> prompt.  So I guess I would have to tell it what kernel to look for  and where to find it.

I might try a reinstall of grub from the live CD into the "windows" partition and see if that solves the problem.

---

### Post by cyberdork33 on 2007-10-26
> **phuturism said:**
> Ok, thanks.  It doesn't offer any entries - it just gives me a grub> prompt.  So I guess I would have to tell it what kernel to look for  and where to find it.

I might try a reinstall of grub from the live CD into the "windows" partition and see if that solves the problem.
ya you have a problem. grub is running, but it does not see the config file or anything.

---

