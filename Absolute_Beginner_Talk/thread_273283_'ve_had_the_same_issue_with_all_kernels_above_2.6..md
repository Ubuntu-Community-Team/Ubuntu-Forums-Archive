---
title: "'ve had the same issue with all kernels above 2.6.10.
A8550 sound - poss fix"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by pompeyjohn on 2006-10-07
I have been googling around trying to get sound working on my Packard Bell laptop and found this

> I've had the same issue with all kernels above 2.6.10.
Passing irqpoll=noacpi to the kernel helped.
Here's the relevant part of my menu.lst.

Code:

kernel          /vmlinuz-2.6.15-26-386 root=/dev/sda6 ro vga=791 irqpoll=noacpi noapic nolapic single 

Which it is suggested might work. Can anyone translate this for me? I am not sure what needs to be done.

Thanks in advance
John

---

### Post by jordanmthomas on 2006-10-07
the line in question is in the file
```
/boot/grub/menu.lst
```

It suggests you find the kernel you are booting and add the irqpoll=noacpi option to it.
I'm not sure what it would do exactly, but I think it would disable the IRQ polling mechanism from checking acpi (power) states.  

You can give it a temporary try by rebooting and pressing 'e' on the kernel you want to boot.  At the end of the line, try adding irqpoll=noacpi, press b and see if it helps.  If so, you can modify menu.lst to make it permanent.

---

### Post by pompeyjohn on 2006-10-07
thanks 

that worked

well, it didnt solve the problem I was having

but it worked.

thanks again

if anyone knows how to get the sound on a Packard Bell A8550 working please please please tell me. I'll buy you chocolate if you do. no? oh well, it was worth a try.

---

### Post by svetj on 2006-11-05
Hi all.
I have a ECS Green 732 laptop with the same problem.
Is there any news?
Thanks a lot.
bye ;-)

---

### Post by pompeyjohn on 2006-11-06
Good luck with this. 

It seems that the chipset is unsupported, possibly because the manufacturer may or may not have released the datasheet on it.

Not a straight answer unfortunately, but the best I can offer.

I have cross posted about this issue all over the internet and got absolutely nowhere. No one seems interested. Most dissapointingly of all the places I asked for advice/assistance: the response from the Linux Audio Users list was .... nothing at all. In the past I have in the past offered up a lot of my time and effort to promoting linux audio, and to get a (lack of) response like that was very dissapointing. 

I plan on writing this up as  blog post soon to make people such as yourself aware on this issue.

sorry it is not better news, but like I said - good luck. I hope you get answers and assistance where I didnt.

---

### Post by svetj on 2006-11-06
Thank you pompeyjohn!
This is not a good news,
but your answer confirms my researches.
So now I'm thinking to buy a simple usb audio card.
Good luck to you, too.
bye ;-)

---

### Post by pompeyjohn on 2006-11-07
I have a laptop, so would need a pcmcia audio card - and they are a bit more expensive than usb :( 

Do keep us posted if you find anything. If and when I have any news I'll post here and across the other threads.

---

### Post by svetj on 2006-11-08
> **pompeyjohn said:**
> I have a laptop, so would need a pcmcia audio card - and they are a bit more expensive than usb :( 

Why only a pcmcia audio card?

Don't you have USB2 or firewire ports on your laptop?
There are many solutions.
It only depends on what you need:
if just playing some mp3 
([http://www.trust.com/products/product.aspx?artnr=14134](http://www.trust.com/products/product.aspx?artnr=14134))
or making audio recording ([http://www.edirol.it/europe/pages.asp?p=groups&idm=2&grp=203](http://www.edirol.it/europe/pages.asp?p=groups&idm=2&grp=203))

The advantage is that you can use these audio cards with desktop and laptops.

bye ;-)

---

### Post by pompeyjohn on 2006-11-08
> **svetj said:**
> Why only a pcmcia audio card?
Don't you have USB2 or firewire ports on your laptop?

Alas no firewire, and my usb ports are always in use :( 

thanks for the suggestions though :D

---

### Post by jam'ez on 2006-11-09
I have the similar laptop... Packard Bell A8202... Same audio chipset, sadly i have had the laptop since christmas (2005) and no luck what so ever since then. :(
Really is a downer, still have not brought a USB or PCMCIA sound card yet ](*,) :mrgreen:

---

