---
title: "Edgy will not detect modem"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by Eddie Wilson on 2006-11-07
Hello All,
Well we were warned. I've run 5.10, 6.06, and last night I installed Edgy 6.10. Edgy will not detect my modem. Its an external 56k which I bought when I first started using 5.10. I've never had any problems with this modem. It will work in Windows Xp. Ive tried several things and just can't it to work. Does anybody have any clue to what is wrong. Thanks for your help.
Eddie

---

### Post by Bachstelze on 2006-11-07
Did it work OOTB in pervious Ubuntus ?

---

### Post by caravel on 2006-11-07
> **Eddie Wilson said:**
> Hello All,
Well we were warned. I've run 5.10, 6.06, and last night I installed Edgy 6.10. Edgy will not detect my modem. Its an external 56k which I bought when I first started using 5.10. I've never had any problems with this modem. It will work in Windows Xp. Ive tried several things and just can't it to work. Does anybody have any clue to what is wrong. Thanks for your help.
Eddie

If it's an external serial modem, then there is no need to detect it.  IIRC it will just work by using pppd, with an X front end such as kppp, and dialing out using ttyS0 or ttyS1 (COM1 or COM2) as the modem device.

---

### Post by Eddie Wilson on 2006-11-07
The modem did work in Ubuntu 5.10 and Ubuntu 6.06. Have set up the modem several times and it will not dial. Did so the terminal and also networking which has always worked for me. Edgy is the only one I've had problems with.
Thank You
Eddie

---

### Post by unisol on 2006-11-07
try using sudo /etc/wvdialconf/wvdial.conf to see what port it is being detected on. if you have an alternate means of downloading d/l gnomeppp and install it it should work

---

### Post by Eddie Wilson on 2006-11-07
Thanks, I'll try that. Also where would I download gnomeppp it I can't do it in Ubuntu?
Eddie

---

### Post by caravel on 2006-11-07
Try: sudo apt-get install gnome-ppp

---

### Post by Eddie Wilson on 2006-11-07
That will work if I already have it on my system.
Thanks,
Iguana

---

### Post by caravel on 2006-11-08
> **Eddie Wilson said:**
> That will work if I already have it on my system.
Thanks,
Iguana

That will fetch it from the server and install it.  Try it. ;)

---

### Post by Eddie Wilson on 2006-11-08
Tried to fetch the gnome-ppp but because Edgy won't operate my modem there is no hope of that. All of the tricks would not work. No problem with Kubuntu 6.06 so I reinstalled Ubuntu Dapper 6.06 and had no problem at all setting everything back up. I've got a 10 gig part. on my hard drive that I use to test with. I'll reload Edgy on that so I can play with it. I will still use Dapper as my main os. Thanks everybody for their help and I wish we could have fixed it.
Eddie

---

