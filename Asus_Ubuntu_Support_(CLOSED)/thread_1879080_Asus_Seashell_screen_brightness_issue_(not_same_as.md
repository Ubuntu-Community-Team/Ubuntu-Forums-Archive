---
title: "Asus Seashell screen brightness issue (not same as what I've found through search)"
date: 2011-11-10
forum: Asus Ubuntu Support (CLOSED)
---

### Post by RubberToRoad on 2011-11-10
Ok.  So I've struggled with this for quite some time with various versions of Ubuntu including netbook remix.  My screen starts out bright-ish at initial splash screen, then goes dimmer.  From there on out, I can get nowhere NEAR full bright.  If I try to use the dimmer controls, the screen will jump back and forth from bright to dark and even off completely with each move of the slider (or of the function keys).  

I'm dual boot and I'd have to say on the brightest setting (about two clicks down from full brightness... yes, I know its weird) its sitting somewhere around the 60% brightness setting in windows 7.

I'm kind of at a loss at this point.  I really like using Ubuntu but this just does not work for me. Be great in a dim room but most times I'm using my netbook its well lit around me.

Any ideas or suggestions?

---

### Post by FX2908 on 2011-11-13
i got a similar issue here. no solution either... i'm using asus 1215b, and ubuntu 10.04.

---

### Post by r_mano on 2011-11-16
Hmmm.. I had the same problem. I solved it (but it was a lot of time ago, do not know if it still works). 

Edit you /etc/default/grub file, adding (or creating) the line: 


```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor eeepc_laptop.hotplug_disabled=1 acpi_enforce_resources=lax"
```

All in one line. And then activate it with

```
sudo update-grub2 
```

I do not know which of the options is really useful now. The were all very useful with 10.04. 

Now that I see, my newer computer **do not** have a /etc/default/grub file, so I a m not sure if the thing changed with 11.10. Any guru here?

---

### Post by r_mano on 2011-11-16
> **r_mano said:**
> 
Now that I see, my newer computer **do not** have a /etc/default/grub file, so I a m not sure if the thing changed with 11.10. Any guru here?

Found a grub2 tutorial. I suppose that if you do not have a /etc/default/grub file, you have to create it. At least is worth a try. 

Look here: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by r_mano on 2011-11-23
Has been the problem solved? I think it's important to feedback, so that the information can be useful for other users.

---

### Post by chrislamuk on 2011-11-30
> **r_mano said:**
> Has been the problem solved? I think it's important to feedback, so that the information can be useful for other users.

I have the exact same problem and would like to know if it fixes the problem. I ave not got round to doing this yet as I'm a complete linux virgin and slowly figuring how to use the terminal etc.

Is someone can walk me though this process I can certainly try the fix.

---

### Post by r_mano on 2011-11-30
> **chrislamuk said:**
> 
Is someone can walk me though this process I can certainly try the fix.

It's easy, the only problem could be on how to recover the laptop if something goes wrong. Edit the /etc/default/grub file, for example 

```
sudo gedit /etc/default/grub
```

In a new installation the file should be new (nothing in it; if it's not the case, stop here and tell me what do you have in it). Copy in it the line posted before (exactly, in one line only): 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor eeepc_laptop.hotplug_disabled=1 acpi_enforce_resources=lax"
```

Save and exit form gedit, then execute 

```
sudo update-grub2
```

and then reboot. 

Works for me. If something goes wrong, you have to go back to the previous contents of the /etc/default/grub, maybe using a recover console (but it shouldn't happen --- you mileage may vary).

---

### Post by chrislamuk on 2011-12-01
> **r_mano said:**
> Has been the problem solved? I think it's important to feedback, so that the information can be useful for other users.

@r mano

your fix does in fact sort out the problem!! Many thanks with that, my enthusiasm in Ubuntu is restored!

---

### Post by r_mano on 2011-12-01
Thanks --- original poster, please, can you mark this thread as [solved]?

---

