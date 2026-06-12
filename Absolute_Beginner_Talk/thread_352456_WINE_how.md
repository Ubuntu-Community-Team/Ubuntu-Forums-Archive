---
title: "WINE: how?"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Cortesio on 2007-02-03
is there an easy way to install WINE without connecting to the internet? I need to setup a modem on my laptop running on linux.

---

### Post by meng on 2007-02-03
Which modem? Why would you think wine is the answer to setting up your modem?

---

### Post by kregg on 2007-02-03
Wine would usually be downloaded from the internet, so not really.

Unless you could somehow get the files and install it yourself.

I don't really know much about this. I used Automatix2 for wine installation :D

---

### Post by jvc26 on 2007-02-03
You may well be able to run your modem without wine - what modem is it? To install wine would usually require access to the internet as you download it from the repositories.
Il

---

### Post by Cortesio on 2007-02-03
I have downloaded the WINE package from another computer and transferred it via a USB stick, but what do I do now? I need WINE to run a .exe file to install the modem. Or maybe there's an alternative?

---

### Post by meng on 2007-02-03
As has been mentioned already, I don't think that will help you. Please tell us what modem you have.

---

### Post by Cortesio on 2007-02-03
Its a speedtouch ADSL Modem.

---

### Post by meng on 2007-02-03
Use the forum search tool to find a thread on this topic, with the solution. That's a very common modem, and I'm sure other folks got it working. You have to overcome the idea that things in Linux work by copying what Windows does, that's not the case at all. So you don't use Windows drivers or executables to get your hardware recognized/configured (ndiswrapper for SOME wireless cards is a notable exception, but even then it's quite different from the Windows way).

---

### Post by lamego on 2007-02-03
As far as I know you can't use a windows modem driver with Wine. The device driver access is always provided the the hosting OS (Linux).

---

### Post by Cortesio on 2007-02-03
Thanks for the advise. Any second opinions? (just in case)

---

### Post by meng on 2007-02-03
> **Cortesio said:**
> Thanks for the advise. Any second opinions? (just in case)
Not sure if you had overlooked my post. When I did the search myself a couple of minutes ago, there are a lot of threads on this topic, and it's a bit complicated, but it does look like there are solutions. So I really recommend you buckle down and start reading about the subject!

---

### Post by mdsmedia on 2007-02-03
2nd opinion?

Listen to what Meng says!!

If you need to use Wine to run your modem, get another modem. (I'm SURE you don't)

Just my opinion.

---

### Post by Cortesio on 2007-02-03
Thanks for the advise guys. I JUST installed linux today, so I'm still new to everything. WINE seemed to be the most logical way of installing it.

---

### Post by meng on 2007-02-03
> **Cortesio said:**
> Thanks for the advise guys. I JUST installed linux today, so I'm still new to everything. WINE seemed to be the most logical way of installing it.
That's a common belief. But it's wrong, it's NOT the logical solution.

---

### Post by mdsmedia on 2007-02-03
I'm no expert, but I use WINE for one program only, and I still don't know how to use WINE properly.

WINE is for Windows programs (which actually work on WINE) that you can't do without. That's why I say ...if you need WINE to run  your modem, find another modem.

Some internal, inbuilt modems, like winmodems are problematic. I'm not sure what the current status is, because I've never had to use them.

For programs you use that are Windows-only, try to find alternatives in Linux....use Synaptic Package Manager (System...Administration...Synaptic...) and search for the TASK you want to perform. Don't expect your Windows programs to work in Linux. There are alternatives.

But for things like modems, find a Linux solution to get them working. Wine is probably not your best solution.

---

### Post by andrew.46 on 2007-02-04
Hi Cortesiao,

 Saw you mention a Speedtouch:

> **Cortesio said:**
> Its a speedtouch ADSL Modem.

 I have a Speedtouch 585 and I have connected my computer running Xubuntu to it via ethernet. No drivers were required at all in this case. Which Speedtouch do you have?

                          Andrew

---

### Post by Cortesio on 2007-02-05
It's a speedtouch 330 (black version)

---

### Post by meng on 2007-02-05
There are plenty of threads here discussing that model.

---

