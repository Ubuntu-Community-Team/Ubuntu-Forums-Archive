---
title: "BIOS update data incorrect"
date: 2012-05-28
forum: Any Other OS
---

### Post by Shadius on 2012-05-28
I received a desktop computer that has Windows XP on it, but when I boot up the computer it shows this:

> <BIOS:> BIOS update data incorrect. CPUID=00000F29
PCI device listing.....

And then column headings with **Bus No.**, **Device No.**, **Func No.**, **Vendor ID**, **Device ID**, **Device Class** and **IRQ**.

What does this mean and can it be fixed?

---

### Post by AnotherMuggle on 2012-05-28
> **Shadius said:**
> I received a desktop computer that has Windows XP on it, but when I boot up the computer it shows this:



And then column headings with **Bus No.**, **Device No.**, **Func No.**, **Vendor ID**, **Device ID**, **Device Class** and **IRQ**.

What does this mean and can it be fixed?

Does the computer boot successfully?  Is it a custom built machine or one from an OEM manufacturer?

I think you need to identify exactly what hardware is inside the PC, specifically the brand/model of the motherboard.  Then you can go to the hardware manufacturers website and see if they are offering any BIOS updates.

---

### Post by Shadius on 2012-05-28
> **tomkear2006 said:**
> Does the computer boot successfully?  Is it a custom built machine or one from an OEM manufacturer?

I think you need to identify exactly what hardware is inside the PC, specifically the brand/model of the motherboard.  Then you can go to the hardware manufacturers website and see if they are offering any BIOS updates.

It does boot into the Windows XP Media Center. I don't know if it's a custom built machine or an OEM machine. Is there a way to determine this? I received it from a friend. 

It's a SONY VAIO PCV-RS314P. I've opened it to try to identify the motherboard and all I can see is that it says "KIRIN" and also "VAIO". Is there a better way to identify the motherboard? Thanks for your help. :)

---

### Post by AnotherMuggle on 2012-05-28
> **Shadius said:**
> It does boot into the Windows XP Media Center. I don't know if it's a custom built machine or an OEM machine. Is there a way to determine this? I received it from a friend. 

It's a SONY VAIO PCV-RS314P. I've opened it to try to identify the motherboard and all I can see is that it says "KIRIN" and also "VAIO". Is there a better way to identify the motherboard? Thanks for your help. :)

That looks like an OEM machine.  I've just taken a look at the Sony website and it appears to be this one: [http://esupport.sony.com/US/perl/model-home.pl?mdl=PCVRS314P&LOC=3#]("http://esupport.sony.com/US/perl/model-home.pl?mdl=PCVRS314P&LOC=3#")

Unfortunately I don't see any BIOS updates available.  When the computer is first booting up you should see a message about pressing some key (often DEL or F8) to enter the setup.  I would try entering the setup (BIOS menu) and look for an option to reset all values to optimised defaults, or something similar.

---

### Post by Shadius on 2012-05-28
> **tomkear2006 said:**
> That looks like an OEM machine.  I've just taken a look at the Sony website and it appears to be this one: [http://esupport.sony.com/US/perl/model-home.pl?mdl=PCVRS314P&LOC=3#]("http://esupport.sony.com/US/perl/model-home.pl?mdl=PCVRS314P&LOC=3#")

Unfortunately I don't see any BIOS updates available.  When the computer is first booting up you should see a message about pressing some key (often DEL or F8) to enter the setup.  I would try entering the setup (BIOS menu) and look for an option to reset all values to optimised defaults, or something similar.

Yes, I believe that is the one also. I will try the BIOS menu. I'll post back to let you know what I see in the BIOS if I have problems. Thanks.

---

### Post by Senior_Buckethead on 2012-05-28
Easy to recognise if it is an OEM because it will be written on the Microsoft Product Sticker that will be attached to the computer. It will say something like 'Windows XP Media Center OEM'. Located just above the product code.

---

### Post by Shadius on 2012-05-28
> **Senior_Buckethead said:**
> Easy to recognise if it is an OEM because it will be written on the Microsoft Product Sticker that will be attached to the computer. It will say something like 'Windows XP Media Center OEM'. Located just above the product code.

In that case, it seems Windows XP Media Center wasn't the original operating system because the sticker says Windows XP Professional. So I guess they removed Windows XP Professional and installed Windows Media Center Edition instead.

---

### Post by Shadius on 2012-05-28
> **tomkear2006 said:**
> That looks like an OEM machine.  I've just taken a look at the Sony website and it appears to be this one: [http://esupport.sony.com/US/perl/model-home.pl?mdl=PCVRS314P&LOC=3#]("http://esupport.sony.com/US/perl/model-home.pl?mdl=PCVRS314P&LOC=3#")

Unfortunately I don't see any BIOS updates available.  When the computer is first booting up you should see a message about pressing some key (often DEL or F8) to enter the setup.  I would try entering the setup (BIOS menu) and look for an option to reset all values to optimised defaults, or something similar.

Is the option to reset all values to optimized defaults called "Load Setup Defaults"? I see it under the Exit tab in the BIOS.

---

### Post by oldos2er on 2012-05-28
Not a Ubuntu support question; moved to Other OS/Distro Talk.

---

### Post by AnotherMuggle on 2012-05-28
> **Shadius said:**
> Is the option to reset all values to optimized defaults called "Load Setup Defaults"? I see it under the Exit tab in the BIOS.

It's different from optimised defaults and some boards offer both options but in this case, try the "Load Setup Defaults" and see if it helps.

---

