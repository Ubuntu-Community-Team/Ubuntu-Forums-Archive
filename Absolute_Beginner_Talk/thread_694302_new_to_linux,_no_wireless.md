---
title: "new to linux, no wireless"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by rattelm on 2008-02-11
borrowed a copy of linux from a friend and my wireless does not work and i'm not hard wired
what do i do,

---

### Post by twistedbydesign on 2008-02-11
You are probably using a broadcom wireless card. They aren't supported very well
I've never dealt with them personally but i know a lot of people are able to get them working with ndiswrapper. I dont know how'd you go about using that on a live CD though.
I'd just research ndiswrapper a bit and see what you can come up with.

---

### Post by rattelm on 2008-02-11
how do i find out what wireless device i have and is there somewhere i can get the drivers if needed?

---

### Post by twistedbydesign on 2008-02-11
I'm not sure, search for broadcom or wireless and look at other people's posts...i know i've seen many where people were walked through getting them running. Like i said, i really haven't dealt with it personally.
Good luck though!

---

### Post by oedha on 2008-02-11
lspci
type that on terminal.....andd see the item network controller.....
report here....what's it tell

---

### Post by oedha on 2008-02-11
or.......open terminal and type
sudo lshw -short -class network
it will tell you what kind of network hardware you have

---

### Post by rattelm on 2008-02-11
Typed in ls usb and it told me 0457 0163 silicon integrated systems

---

### Post by oedha on 2008-02-11
are you using wireless usb ?
i can't help you with this....sorry :(

---

### Post by rattelm on 2008-02-11
> **oedha said:**
> or.......open terminal and type
sudo lshw -short -class network
it will tell you what kind of network hardware you have

That gave me 82541gl gigabit ethernet control . Yes it is a usb wireless adapter

---

### Post by redyoshi49q on 2008-02-12
After a bit of Google searching, I came across this [here]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/"):

> #
Card: Senao SUB-316 USB Donge 802.11g USB 2.0 Adapter

    *
      Chipset: sis163u (Silicon Integrated Systems Corp)
    *
      usbid: 0457:0163
    *
      Driver: Supplied on CD, SiS163u.INF
    *
      Other: It works perfectly with ndiswrapper-1.19 and 1.21, I use Ubuntu Dapper Drake.

There's a good chance that ndiswrapper will get your USB device working.  Unfortunately, it's been a while since I set up ndiswrapper, so I don't completely remember how to get ndiswrapper to work...

---

