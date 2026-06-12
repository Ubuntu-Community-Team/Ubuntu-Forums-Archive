---
title: "1 Question: Regarding my printer."
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by i-m-p on 2006-10-01
Hi,

My printer is canon pixus ip2200. Canon sells this particular printer only in Japan and doesn't have a driver at Canon website. Canon Europe has a pixma ip2200 driver but I was told by Canon these are two totally different printers. Therefore I think this printer ,ip2200, won't work untill either Canon release the driver or someone rather than canon make a driver for ubuntu. 

All I can do therefore is I have to buy another printer since it virtually impossible ,at least now, for me to make a driver otherwise no printer for my ubuntu. What do you think?

If I had to buy an another printer ,albeit which I really don't want to,it seems to me HP is the most linux friendly one.
In order to use printer smoothly on ubuntu choose one printer from HP is maybe the best thing I can do. What do you think?

Any of your thoughts or/and suggestions are welcome.

Sincerely,

---

### Post by Sef on 2006-10-01
HP and Epson are the best to buy.  Here is LinuxPrinting's [Suggested Printers.]("http://linuxprinting.org/suggested.html")

---

### Post by Imsati on 2006-10-01
Yes, Epson is nice. I love my Stylus. Wife loves her Brother though--hooked up to XP, so I'm not sure how compatible with Linux, but very decent and near-perfect glossy photos.

---

### Post by i-m-p on 2006-10-01
Epson and HP might be the better choices.

It would be probably better to buy a printer which is already included in ubuntu.

Cheers,

---

### Post by gn2 on 2006-10-01
> **i-m-p said:**
> Hi,

My printer is canon pixus ip2200. Canon sells this particular printer only in Japan and doesn't have a driver at Canon website. Canon Europe has a pixma ip2200 driver but I was told by Canon these are two totally different printers. Therefore I think this printer ,ip2200, won't work untill either Canon release the driver or someone rather than canon make a driver for ubuntu. 


What exactly are the differences, I bet they didn't tell you?

As far as I can see, it's just the AC power voltage that's different.

Won't hurt to try the European Pixma driver because the two printers are broadly similar. (Even the quoted noise output 44dB)

---

### Post by i-m-p on 2006-10-02
> Won't hurt to try the European Pixma driver because the two printers are broadly similar. 

You might be right.
I will try when I have a time. Actually I tried to install it once before I contact Canon Japan to confirm they're different. I thought they are the same.
But try to install that driver which canon provides was not something I could handle by myself.

Thanks.

---

### Post by ppl on 2006-10-02
If u could manage to install Windows XP in VMware server, u can try to install the Windows driver in the virtual machine. I succeed with my Canon i560 which using USB cable.

There is a great howto about install Windows in VMware server in the forum. But you need enable USB controller for your virtual machine which is not on by default,that is the only thing you need change.But I think if your Ubuntu box cannot recognize your printer model correctly this method wouldn't work.That means when you type:
```
lsusb 
```
in terminal, the output should list your printer model.

---

### Post by gn2 on 2006-10-02
You need to investigate the Canon Japan Website, and find a BJC printer that uses the same cartridges as yours.

Chances are the driver for that printer might work.

---

