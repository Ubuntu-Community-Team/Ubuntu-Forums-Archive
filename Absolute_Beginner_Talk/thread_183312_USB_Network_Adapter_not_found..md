---
title: "USB Network Adapter not found."
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by SZF2001 on 2006-05-27
[I went out and bought this](http://www.amazon.com/gp/product/B00005AW1H/sr=8-1/qid=1148767378/ref=pd_bbs_1/002-7729884-3415267?_encoding=UTF8). Cost like $15.

The version is 4.1.

I have installed ndis and it's tools. I go to the Windows Wireless thing through the Administration menu, put the WUSB11v4.inf file with my adapter plugged into the computer.

It tells me there is no hardware present, and yet, I can see it, connected to the USB slot, and the light glowing on it.

I try it through the terminal. It tells me my .inf file or drivers or whatever is invalid.

What did I do wrong. I'm about to freakin' cry here.

---

### Post by az on 2006-05-27
[QUOTE=SZF2001][I went out and bought this](http://www.amazon.com/gp/product/B00005AW1H/sr=8-1/qid=1148767378/ref=pd_bbs_1/002-7729884-3415267?_encoding=UTF8). Cost like $15.

The version is 4.1.

I have installed ndis and it's tools. I go to the Windows Wireless thing through the Administration menu, put the WUSB11v4.inf file with my adapter plugged into the computer.

It tells me there is no hardware present, and yet, I can see it, connected to the USB slot, and the light glowing on it.

I try it through the terminal. It tells me my .inf file or drivers or whatever is invalid.

What did I do wrong. I'm about to freakin' cry here.[/QUOTE]

You probably don't need ndiswrapper.  The linux driver are being loaded for you automagically.

Boot your Ubuntu box, then insert the thing.  Wait about ten seconds and then run
tail /var/log/messages

and post the output.

---

