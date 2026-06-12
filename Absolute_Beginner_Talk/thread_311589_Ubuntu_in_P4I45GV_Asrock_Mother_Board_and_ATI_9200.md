---
title: "Ubuntu in P4I45GV Asrock Mother Board and ATI 9200"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by zachariaz on 2006-12-03
I got P4I45GV motherboard and additional ATI9200 AGP card, P4I45GV has a built-in video. Im having problem istalling Ubuntu 6.10 since Im new in ubuntu and never tried any Linux, can somebody help me what to do? When I change my primary video in BIOS to the built-in, the installation is good, but when I change it to AGP ATI9200, the installation just hangs. Is there any way I could do this right? 

Thanks in advance...

---

### Post by 56phil on 2006-12-03
You need the ATI video driver. Try installing Edgy using the text based alternate install CD, or the on-board video. Then, install the video driver to use your ATI card using these [instructions]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide").

---

### Post by zachariaz on 2006-12-03
Thank you for giving time replying.

I have already tried and sucessfully installed Edgy using my on-board video, but this is not my normal use - I have ATI9200 card I use in my XP (dual boot). When I switch my BIOS to normal usage - (with my AGP ATI900 as my primary video), Edgy just hungs.

I tried using the driver and the procedure you've mentioned (while in on-board video), but it doesnt work when I switched to my primary ATI card.

...just doesnt work.
...help.

---

### Post by widjajayd on 2006-12-30
Yes, I got same problem with you
it seems the problem is from  **P4I45GV Asrock Mother Board **

I have P4I45GV Asrock Mother Board + Nvidia FX 5200
I did the procedure using onboard video then install nvidia FX 5200 but it keeps hang
and the dapper/edgy live CD is not working also

and safe mode also hang

last line is EIP is at clear_local_apic :???:

---

