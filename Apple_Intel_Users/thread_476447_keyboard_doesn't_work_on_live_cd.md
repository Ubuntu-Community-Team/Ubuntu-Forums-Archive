---
title: "keyboard doesn't work on live cd"
date: 2007-06-17
forum: Apple Intel Users
---

### Post by duffman25 on 2007-06-17
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/fedora/+source/syslinux/+bug/79172](https://bugs.launchpad.net/fedora/+source/syslinux/+bug/79172) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi

I have a macbook core 2 duo. When I pop in feisty live cd on it, I can't use the keyboard in grub (it doesn't work)

Any fix or explanation?

thanks

---

### Post by tgalati4 on 2007-06-17
"Luke, Use the Force.  Rely on your instincts.  Your senses deceive you."

Did you try an external USB keyboard?  Or a bluetooth keyboard?

Don't let a simple keyboard problem stop you from experiencing Ubuntu goodness.

If the Feisty Live CD doesn't give you a keyboard, then you shouldn't install it.

---

### Post by duffman25 on 2007-06-17
> **tgalati4 said:**
> "Luke, Use the Force.  Rely on your instincts.  Your senses deceive you."

Did you try an external USB keyboard?  Or a bluetooth keyboard?

Don't let a simple keyboard problem stop you from experiencing Ubuntu goodness.

If the Feisty Live CD doesn't give you a keyboard, then you shouldn't install it.

The problem is that there's no keyboard on grub. Once booted the keyboard works fine. Also, Id rather try to fix it than having to bring a usb keyboard with the laptop.

thanks

---

### Post by eric stockman on 2007-06-26
I have the same problem. The LiveCd is hard coded for a Querty-keyboard ?
This is hard on Azerty-keyboard users . Confronted with the same problem in an MS-environment I can emulate the Azerty-keys with alt + max 3 digits  p.e  a backslash is alt + 92  , # is  alt 35 , a tilde - is alt 126     etc....  
I wish I could do the same in an Ubuntu terminal .

---

### Post by ronocdh on 2007-06-26
> **duffman25 said:**
> The problem is that there's no keyboard on grub. Once booted the keyboard works fine. Also, Id rather try to fix it than having to bring a usb keyboard with the laptop.

thanks
This is a problem caused by lack of understanding of Apple's firmware. The rEFIt crowd [has acknowledged it]("http://refit.sourceforge.net/doc/c4s3_keyboard.html") and they offer the only advice I can: reboot and try again. It's a real pain, but you'll get the hang of it. Develop some keyboard voodoo, and you should be able to minimize the number of boots necessary. I scatter-tap on keys all across the keyboard as GRUB is loading, then rapidly alternate between the up and down arrow keys right before the GRUB screen shows up. I have absolutely no data whatsoever suggesting that this helps get the keyboard to respond, but it keeps me sane.

---

### Post by luisbg on 2007-06-29
I have the same problem, funny thing is that the keyboard works sometimes in grub and sometimes not. 

An other funny thing I've noticed is that if you plug a usb keyboard, press a key on it, then the laptop keyboard works.

my two cents,
luis

---

