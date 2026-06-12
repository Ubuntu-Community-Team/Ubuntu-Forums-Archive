---
title: "Howto keep keyboard usb settings from boot"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by shareMenaPeace on 2007-12-26
Hello, 
i can use my keyboard when booting my desktop computer, but once im at the login or inside ubuntu or kubuntu it is not working anymore.

I belive this is a USB HUB problem - maybe BIOS related.

Chicony wired keyboard model KB 9885
is supported ...

Is there a way to keep this during booting, with a boot option assigned?

Or can i later add this to xorg.conf?

Also posted here 
[http://ubuntuforums.org/showthread.php?t=650136](http://ubuntuforums.org/showthread.php?t=650136)

Thanks for tips and tricks.

---

### Post by kestrel1 on 2007-12-26
Have you got the keybord connected to on-board USB, PCI card USB or through a USB hub connected to either of these?
I would have the keyboard connected directly to onboard USB first, to make sure that it works okay.

---

### Post by shareMenaPeace on 2007-12-26
Sorry i was not correct, its not a USB keyboard ... a old keyboard with a normal standard keyboard slotstick.

But i belive this has todo something with my USB stuff in the computer, because if i boot windows, i need a 2nd mouse pluged in with an adapter at teh default MOUSE PORT(not USB port but the adapter uses the usb mouse and goes to the deault mouse port / right beside the keyboard default port.... IF i use a standard mouse with default plug, i can not write in windows either ... infront of the computer and below the default keyboard and mouse ports are more usb ports .... I can use the keyboar din boot grub menu, but not later, so is there a way to keep the grub keybaord settings?
After booting windows XP with the mouse and adapter i can remove it and use a USB mouse ..but if i boto i need to stick the default mouse back ....
strange is it...

Also booting LIVE CD and than choosing from preferences - keyboard panel ...CHERYO 9885 makes no diffrence ...

---

### Post by kestrel1 on 2007-12-26
I assume you mean a PS/2 keyboard?
Personally, I would try another keyboard first, especially as it is not working in Windows either. Sounds like it may be faulty. PS/2 & USB are totally seperate. Using a USB mouse with an adapter, just makes it a PS/2 mouse.

---

### Post by shareMenaPeace on 2007-12-26
I tired another keyboard *usb* from ebay ... but the ESC key was not working ...so i opened it ...now its not workign anymore :)  A cable broke ....and i have no stuff to fix this ....any other option?

A boot command ....?
Bios setting?

---

### Post by kestrel1 on 2007-12-26
Keyboards are as cheap as chips these days. Get a new one.
Don't know what country you are in but here is one on a UK site: [http://www.ebuyer.com/product/105529](http://www.ebuyer.com/product/105529)

---

### Post by shareMenaPeace on 2007-12-26
ty, i just thought i can stick with it ..well its very old and not nice anymore..so i propably go todo this ...just sad that i cannot install kubuntu now on my desktop computer :)

And i hope this is the problem ... i mean its in the supported list .. sooo this might be no solution ...


CHeers:popcorn:

---

### Post by kestrel1 on 2007-12-26
It is always possible that the keyboard/mouse controllers are faulty, which would mean a new mobo. I would say the keyboard is the cheaper option at present. If that doesn't work though you may need to be looking at the mobo. Another thought, have you checked the settings in the BIOS. There could be something causing a problem in there. If in doubt, set your BIOS to failsafe settings.

---

### Post by shareMenaPeace on 2007-12-26
I will do this later, well i run this machine since ... 15 month or someting, but always XP ... and i will get a keyboard, but i buy from a store i know, they have luminated usb keyboards for 18 euros. As i mentioned i bought a usb keyboard (luminated) from ebay but it was not working correct .. it was cheap 10 euros but 5 euros shipping ...

thank you

---

