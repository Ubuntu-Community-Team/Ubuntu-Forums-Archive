---
title: "[SOLVED] Howto use this Abit NF-M2S driver?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by guhpraset on 2007-06-01
I have installed Dapper on Abit NF-M2S, but it have no sound at all, i guess it failed to detect the soundcard. So i look for the driver, and i found them **_[here.]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false#2")_**

The question is, which one i have to choose and how to use it?

I need a guide for complete Idiot, please.

Thankyou.

---

### Post by crispy_420 on 2007-06-02
If you unpack that file the instructions are in the Readme.txt file. It looks like you just need to be in that directory and run "sudo ./install" from terminal. That is the auto method or it looks like you have the option of installing each part from source.

---

### Post by guhpraset on 2007-06-04
i have an error message after i enter "sudo ./install"

it said "configure: error: no acceptable C compiler found in $PATH"

*googling*

---

### Post by crispy_420 on 2007-06-07
Install gcc, I think.

---

### Post by guhpraset on 2007-06-09
Yes. You are right.

But now i have change my OS to Ubuntu FEISTY, and the sound is working without problem, without having to install any driver. Amazing :P I think everybody have to upgrade their ubuntu if they want to have easier life.

Thankyou

---

