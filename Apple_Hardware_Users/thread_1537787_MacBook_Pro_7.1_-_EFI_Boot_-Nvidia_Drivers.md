---
title: "MacBook Pro 7.1 - EFI Boot -Nvidia Drivers"
date: 2010-07-24
forum: Apple Hardware Users
---

### Post by dgbarlow on 2010-07-24
Next week I should have a new MacBook Pro 17" 7.1 on which I intend to dual boot Linux with Snow Leopard. I have been doing my homework and note a Catch 22 in my installation options.

1.  I can install via boot camp or similar methods which use an emulated bios. In this case I have the Sata Driver problem, which means essentially booting from a patched disc to install and later adding DMA support. The patches to the kernel force use of a less than optimal driver as a quick-fix.

2.  I can install using an efi boot loader (for instance, Grub 2) and boot directly from EFI with no emulated bios.  Apparently, in this case there is no problem with SATA but the proprietary NVidia Driver will not work, as it apparently require data from BIOS.  I'm not sure about the opensource Noveau driver. I'm also not sure if this has been addressed by Nvidia.

I'd appreciate any comments as to whether I have understood the current situation correctly, any updates to this situation and whether any one else has experienced success with the direct EFI boot method.

---

### Post by labaom on 2010-07-24
> **dgbarlow said:**
> Next week I should have a new MacBook Pro 17" 7.1 on which I intend to dual boot Linux with Snow Leopard. I have been doing my homework and note a Catch 22 in my installation options.

1.  I can install via boot camp or similar methods which use an emulated bios. In this case I have the Sata Driver problem, which means essentially booting from a patched disc to install and later adding DMA support. The patches to the kernel force use of a less than optimal driver as a quick-fix.

2.  I can install using an efi boot loader (for instance, Grub 2) and boot directly from EFI with no emulated bios.  Apparently, in this case there is no problem with SATA but the proprietary NVidia Driver will not work, as it apparently require data from BIOS.  I'm not sure about the opensource Noveau driver. I'm also not sure if this has been addressed by Nvidia.

I'd appreciate any comments as to whether I have understood the current situation correctly, any updates to this situation and whether any one else has experienced success with the direct EFI boot method.

It would he better for you to use a daily build of Ubuntu like it says on the wiki. That way you do not need to patch anything. I would also suggest you use refit boot loader. Then partition your drive in disk utility and then install ubuntu. Make sure in the last step in the install you click advance and check install bootlader if it isnt and make it install to where your ubuntu partition is instead of your whole hardrive.

---

### Post by dgbarlow on 2010-07-24
Thanks for the advice.  I will probably give it a try with direct efi boot using Grub 2 first.  Then, if that is not satisfactory I will install refit and follow your advice.  Using a daily build is an excellent idea.

---

### Post by labaom on 2010-07-25
> **dgbarlow said:**
> Thanks for the advice.  I will probably give it a try with direct efi boot using Grub 2 first.  Then, if that is not satisfactory I will install refit and follow your advice.  Using a daily build is an excellent idea.

Its all from the wiki.

---

### Post by HadesBego on 2010-08-23
right, the dialy biuld seems to be the only option to install on newer Macbook pro (7,1), but server is so slow!...always.

---

### Post by blueridgedog on 2010-08-25
I installed the daily build on my new MBPro 7,1 last week with no issues using refit boot loader and partitions created inside Mac OS.  Details are here: [https://help.ubuntu.com/community/MacBookPro7-1/Lucid](https://help.ubuntu.com/community/MacBookPro7-1/Lucid)

You will need a wired connection to download the wireless restricted driver.

---

### Post by ggael80 on 2010-12-03
[hi, ]("http://www.uluga.ubuntuforums.org/member.php?u=719761")

[dgbarlow: could you confirm that Linux is running well on your 17" MBP 7.1 ? including the NVidia graphics card with the proprietary drivers ? and what about graphics card hot switching ?]("http://www.uluga.ubuntuforums.org/member.php?u=719761")

thanks a lot !

---

