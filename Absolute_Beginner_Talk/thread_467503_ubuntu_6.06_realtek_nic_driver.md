---
title: "ubuntu 6.06 realtek nic driver"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by prostock3 on 2007-06-07
Hi,

I"m trying to install Ubuntu server.  The install program cannot detect my network device(Realtek 8111B NIC).  I read on other posts that you need to create a driver module?  Could anyone step me through on how to do this?

Thanks in advance!

---

### Post by p_quarles on 2007-06-07
I've never had any problems with a wired network card (except for one that was broken) in Ubuntu, so I don't know much about configuring the driver. I looked it up, too, and Realtek cards are supposed to work out of the box. 

But, I do have one shot in the dark suggestion: maybe try installing Ubuntu server ed. 7.04. Might not work, but at least you'll know for sure. :-)

---

### Post by madmetal on 2007-06-07
> **prostock3 said:**
> Hi,

I"m trying to install Ubuntu server.  The install program cannot detect my network device(Realtek 8111B NIC).  I read on other posts that you need to create a driver module?  Could anyone step me through on how to do this?

Thanks in advance!

with a quick search i found this driver for your card..
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

---

### Post by prostock3 on 2007-06-07
thanks guys.. i'm a real newebie....the nic is on my motherboard aw9d max...if i download the driver, does this mean i need to compile a new kernel?

---

### Post by croto on 2007-06-10
Hey, have a look at 

[http://ubuntuforums.org/showthread.php?t=467757](http://ubuntuforums.org/showthread.php?t=467757)

we're trying to solve the same problem over there.

---

