---
title: "booting system"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by richarjohn on 2007-03-13
i have just installed ubuntu 6.10 on my hard drive with a boot menu, when i select to boot ubuntu,it booted ok the first few times but now some times it hangs at about 20% when booting and have to ,switch the computer off and start from the boot loader again,this some times takes two or three goes before the o/p system runs.
my m/c is 1.8 ghz intel
                28gb h/d
               500sdram
any help  or direction to correct this would be appreciated as i would like to run this o/p system as my default
     regards richarjohn

---

### Post by bikeboy on 2007-03-13
Sounds strange that it's intermittent.

One thing to try is a few boot options. To do this, when you get the menu to select the OS you want to boot, highlight the Ubuntu one and press the "e" key. Scroll along to the end and add the following
```
 noapic nolapic
```

So it might look something like this:```
/boot/vmlinuz-2.6.20-9-generic root=UUID=f44def62-84be-4938-8f5a-517a37af97fa ro quiet splash noapic nolapic
```

Yours won't be exactly like mine, but you should get the idea. Once you've changed it, press enter and then the "b" key to try out the changes. It's not a permanent change so if you muck something up it will be normal the next time around. If the changes work we can show you how to make them permanent.

Another thing to try might be to remove the "quiet" part of that line so you can see where it freezes.

---

