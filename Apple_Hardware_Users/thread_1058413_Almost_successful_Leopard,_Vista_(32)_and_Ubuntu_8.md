---
title: "Almost successful Leopard, Vista (32) and Ubuntu 8.10 boot"
date: 2009-02-02
forum: Apple Hardware Users
---

### Post by merliomar on 2009-02-02
Hi partitioned and installed all three Os's in my macbook 4.1

All three systems can be booted from Refit, but still there are two things that I would like to fix:
I've been looking through the threads, which for newbies might be a bit complicated. :-)


_Linux boot._ It doesn't boot directly as it asks if it should boot my Vista partition, which is called Longhorn. So, once I choose Ubuntu on Refit I have to enter an option again. I want to know if this is normal, I find it quite weird to see this connection to Vista. During installation I was asked if I wanted to have access to some Vista accounts. Is this normal? Or is there something I can do about?

_Primary boot._ When I turn the computer on, it should boot directly to Mac OS - but this is not the case. After a while it boots into Refit. Mac os is the one I use most, so I hope there are any hints.

_How I installed all three if anyone needs to know._ I created Windows partition with boot camp, then created linux partition with disk utility.  Vista and Refit Installation. On Linux, I formated the intended partition and found a tiny partition that was unused, I installed there the swap file. On Refit MBR it's placed as the fifth partition.  Did these dd commands for backing up MBR (don't know if it worked). Booted into Vista and had to repair installation with Install DVD.

---

### Post by pxwpxw on 2009-02-02
That is a good standard triple boot install.

The ubuntu installer by default puts grub bootcode on the MBR, replacing vista boot code. So you boot vista or ubuntu via the 'Linux' grub menu.

The alternative is to install grub bootcode to the ubuntu partition, and reinstall vista bootcode to the MBR, giving choice of Linux or Windoows in the refit menu. But needs to be very carefully done.

IDK about the Vista accounts question.

Primary boot is to refit because that is the way the refit installer sets it up, replacing MacOSX, and this is renewed by the refit Blesser at each shutdown. Refit should show MacOSX as the default, and you can set the time delay in refit.conf.

I am not sure how to have a direct menu choice between refit and Mac OSX, probably requires reinstalling refit manually. May be an easy answer, possibly on the refit web site which is very informative. 
[http://refit.sourceforge.net/](http://refit.sourceforge.net/).

---

