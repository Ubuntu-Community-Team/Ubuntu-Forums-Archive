---
title: "Mac New user installation issues"
date: 2021-06-16
forum: Apple Hardware Users
---

### Post by jayorchard on 2021-06-16
I really would appreciate your help
new Ubuntu installation on ten yr old iMac computer. Wrote over iOS. 

1). Once loaded I see four identical workspaces that are greyed out.  so light in colour cannot read. Mouse click does activate things however cannot identify what I am opening.  Cannot reduce to one workspace. 

2). Upon booting up I get “failed to set MokListRT. Invalid parameter. “

I would reinstall and start over in a heartbeat.  Big thank you for your help. New user. Excited to give this ago. Jay. London Ontario. 63 yrs old

---

### Post by oldfred on 2021-06-17
Moved to Apple sub-forum as Macs have some unique requirements.

Exactly which model Mac. 
Just about each version seems to need something different.

Some links I have saved, showing various issues.

iMac 13, 2 (late 2012) 27"  It Just Works! 
[https://ubuntuforums.org/showthread.php?t=2425170](https://ubuntuforums.org/showthread.php?t=2425170)

Apple's Late-2016 MacBook Pro Is Still A Wreck With Linux
[https://www.phoronix.com/scan.php?page=article&item=mbp2016-linux-wreck&num=1](https://www.phoronix.com/scan.php?page=article&item=mbp2016-linux-wreck&num=1)

Pre-2008 Macs mostly have IA32 EFI firmware while >=2008 Macs have mostly x86_64 EFI. All Macs capable of running Mac OS X Snow Leopard 64-bit Kernel have x86_64 EFI 1.x firmware.

---

### Post by scorp123 on 2021-06-17
> **jayorchard said:**
>  1). Once loaded I see four identical workspaces that are greyed out.  so light in colour cannot read. Mouse click does activate things however cannot identify what I am opening.  Cannot reduce to one workspace. 

No idea what you mean here. Can you photograph it and post a picture?


> **jayorchard said:**
> 
2). Upon booting up I get &#8220;failed to set MokListRT. Invalid parameter. &#8220;


You mean immediately after the Mac powers up? It's a message, white text on black background, visible maybe for 2-3 seconds .... aaaand pooof! it disappears? If it's the message I mean then it can be ignored. The Mac should work fine regardless.

---

### Post by oldfred on 2021-06-17
The moklist is related to UEFI Secure Boot, used with most PC.
But Mac have their own version of UEFI. 

Does your Mac even have Secure boot?
If not then there would not be a Secure boot key list that moklist could find.

---

### Post by jayorchard on 2021-06-18
Thank you for your help. I need to figure out the secure boot. With the four blurry workspace screens it is all but impossible to see where the mouse is or read any activated icons. My Mac is a 2009. I’m not in a position to see the details due to screen. I’ve really messed this.  Thanks everyone.

---

### Post by oldfred on 2021-06-18
Screen issues are usually video card/chip related.

This shows install to Mac and mentions nomodeset.
With PC we used to have to use nomodeset boot parameter until we installed the correct video driver.
Not sure if newer Ubuntu's safe boot which loads video & choosing optional proprietary drivers to get video driver installed works with Mac or not.

[https://www.lifewire.com/dual-boot-linux-and-mac-os-4125733](https://www.lifewire.com/dual-boot-linux-and-mac-os-4125733)

---

### Post by jayorchard on 2021-06-20
Thank you so much for this. J

---

