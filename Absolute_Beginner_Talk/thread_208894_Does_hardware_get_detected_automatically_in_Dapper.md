---
title: "Does hardware get detected automatically in Dapper?"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by mcintyre321 on 2006-07-04
Hi there. I recently reformatted my Windows server and installed Dapper from DVD, bought a Freecom DVB-T USB stick and am now trying to get it working.

I have been following the instructions from here [http://popey.com/cgi-bin/wiki.pl?NigelsHushBox](http://popey.com/cgi-bin/wiki.pl?NigelsHushBox) but when I get to the third step, insert "Freecom DVB-T Card" the guide expects something to happen. When I plug my card in, nothing happens at all. Not even a message saying unknown device detected.

This is making me wonder if perhaps my USB ports aren't working correctly. My mouse and keyboard and USB hard disk seem to work (but then maybe they are working at USB 1.1 speeds not 2? is that likely?). What do you think? Is *something *meant to happen when i insert a usb device?

[SIZE="1"]PS This is a cross post coz i think i put this message in the wrong forum earlier[/SIZE]

---

### Post by givré on 2006-07-04
the event you can see on this site don't come like that in the terminal.
```
dmesg | tail -n 50
```should show this.

---

