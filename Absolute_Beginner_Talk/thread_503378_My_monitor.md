---
title: "My monitor"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by bollofinwe on 2007-07-17
Just a quickie really.

My monitor is a TV-monitor but has a VGA input. 

The main problem is that I can not access my BIOS using this monitor as it doesn't receive a signal with the correct resolution. (Only handles 800x600 or 1024x768 ). Or so I assume. Not only that - once I insert my disk and it boots that from CD the monitor does not recognize the signal then neither.

Is there a way I can install Ubuntu on my separate partition from windows?

Is there a way to change the resolution on the installer?

Or am I screwed and have to buy a new monitor?

Any help would be greatly appreciated and I am looking forward to entering the world of Linux, it is the way forward and I hope Microsoft know it ;)

---

### Post by w4ett on 2007-07-17
> **bollofinwe said:**
> Just a quickie really.

My monitor is a TV-monitor but has a VGA input. 

The main problem is that I can not access my BIOS using this monitor as it doesn't receive a signal with the correct resolution. (Only handles 800x600 or 1024x768). Or so I assume. Not only that - once I insert my disk and it boots that from CD the monitor does not recognize the signal then neither.

Is there a way I can install Ubuntu on my separate partition from windows?

Is there a way to change the resolution on the installer?

Or am I screwed and have to buy a new monitor?

Any help would be greatly appreciated and I am looking forward to entering the world of Linux, it is the way forward and I hope Microsoft know it ;)

Ubuntu will install in what is called a 'Dual Boot' configuration...the Live CD will do this for you.  It is a guided install.

to change the installer resolution press F4 (VGA) at the CD boot screen.

No new  monitor is needed.   Feel free to ask any questions that you need to.

PS:  Welcome to the community!

---

### Post by bollofinwe on 2007-07-17
Thanks alot man. 

These forums are really well thought out (Sidetrack I know)

I will try this in the morning, used my last CD-R on an i386 disc when, infact, I have a AMD 64 chip. 

One problem I have is that I don't think CD is on priority to boot. Anything I can do there?

Also, a bit off topic again. You got any links to beginners information on linux and Ubuntu?

---

### Post by w4ett on 2007-07-17
> **bollofinwe said:**
> Thanks alot man. 

These forums are really well thought out (Sidetrack I know)

I will try this in the morning, used my last CD-R on an i386 disc when, infact, I have a AMD 64 chip. 

One problem I have is that I don't think CD is on priority to boot. Anything I can do there?

Also, a bit off topic again. You got any links to beginners information on linux and Ubuntu?

Boot into your BIOS and set your boot priority to boot your CD/DVD drive as your 1st boot device.   Also maybe F11 might be a toggle from the POST screen.  

As far as info, I like this page:  [http://www.reallylinux.com/docs/consult.shtml](http://www.reallylinux.com/docs/consult.shtml)

Welcome to the community!...check back with any other questions that you have.  Good Luck!

---

### Post by bollofinwe on 2007-07-17
> **w4ett said:**
> Boot into your BIOS and set your boot priority to boot your CD/DVD drive as your 1st boot device.   Also maybe F11 might be a toggle from the POST screen.  

As far as info, I like this page:  [http://www.reallylinux.com/docs/consult.shtml](http://www.reallylinux.com/docs/consult.shtml)

Welcome to the community!...check back with any other questions that you have.  Good Luck!

Yeah, I know how to change boot sequence. It's just I cant see it as my monitor doesn't show my bios. If you get me.

S'ok tho. I worked out F11 takes me into boot menu and boot from CD is 2nd on the list. So I did it blind. I am now posting this off the liveCD. However its the i386 one - seems to work tho. However, I will wait until I got the 64 one when I come to install it.

I'll just do the same tomorrow when I have burn my 64 bit CD.

Thanks for the info!

---

### Post by w4ett on 2007-07-18
> **bollofinwe said:**
> Yeah, I know how to change boot sequence. It's just I cant see it as my monitor doesn't show my bios. If you get me.

S'ok tho. I worked out F11 takes me into boot menu and boot from CD is 2nd on the list. So I did it blind. I am now posting this off the liveCD. However its the i386 one - seems to work tho. However, I will wait until I got the 64 one when I come to install it.

I'll just do the same tomorrow when I have burn my 64 bit CD.

Thanks for the info!

What Mobo are you using (or prebuilt system...Dell, HP...etc, model number)?  Let's see...F1, F2, <insert>, <delete> are all keys used by manufacturers  in the POST Bootup sequence to enter SETUP (the Bios interface).

Tho...if you got F11 to work setting your boot priority, that should suffice for now.

---

### Post by kiv on 2007-07-18
> **bollofinwe said:**
> Yeah, I know how to change boot sequence. It's just I cant see it as my monitor doesn't show my bios. If you get me.

S'ok tho. I worked out F11 takes me into boot menu and boot from CD is 2nd on the list. So I did it blind. I am now posting this off the liveCD. However its the i386 one - seems to work tho. However, I will wait until I got the 64 one when I come to install it.

I'll just do the same tomorrow when I have burn my 64 bit CD.

Thanks for the info!

TBH you might be better off sticking with 32 bit.. some people may disagree... & I'm not entirely certain.. but there are always more issues with 64 bit... and usually little benefit..

If anyone else knows the ubuntu 64bit to be different, feel free to disagree.

---

