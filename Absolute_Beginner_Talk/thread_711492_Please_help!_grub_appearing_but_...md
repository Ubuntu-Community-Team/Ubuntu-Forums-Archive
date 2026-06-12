---
title: "Please help! grub appearing but .."
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by neoragexxx on 2008-02-29
i did restore windows using my vista dvd .

i had ubuntu 7.10 installed before with grub working fine. i was expecting for grub to disappear after the vista restore but i see grub and then it says under error 17 

i have no idea what that is !

when i follow the instructions to reinstall grub , after the command find /boot/grub/stage1

it says not found :(


any help will be very appreciated

---

### Post by forrestcupp on 2008-02-29
So did you install Vista with the intent of not using Ubuntu anymore?  If you got rid of Ubuntu, then you don't even have the directory and setup files for GRUB anymore, and that's why you're getting the error.

If that is your problem, I had that problem a while back.  The only way I found to get rid of grub and only have Vista's bootloader was to use the [Super Grub](http://sgd.benjamin-butschko.de/) disk.  It has an option to restore the Windows boot loader.  If it doesn't have an option for Vista, the XP option works.  That's what I had to do.  After that, I didn't have grub anymore, it just booted to Windows.

Of course it wasn't long before I had Ubuntu installed again.

But if you are still wanting to dual boot, you'll have to give some more info on what you did.

---

### Post by ChaosParser on 2008-02-29
Boot from the Vista DVD, use recovery console to fixboot.

---

### Post by Thingymebob on 2008-02-29
assuming you no longer want grub

# Insert your Windows Vista Install DVD and boot from it.
# After selecting your language options choose the &#8220;Repair your computer&#8221; option in the bottom left corner.
# Select your Windows Vista Installation and continue 
# Open a new Command Prompt window
# When command prompt is open, type the following commands 

```
Bootrec /fixboot
Bootrec /fixmbr
```

---

### Post by neoragexxx on 2008-03-01
thanks guys i apparently i didn't realize that the recovery dvd of vista will delete my ubuntu partition !! no it wasn't my intention not to use ubuntu anymore.. i reinstalled ubuntu after the vista again

---

