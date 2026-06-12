---
title: "extremely silly behavior from Ubuntu 7.10"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by loldrup on 2007-11-08
I have a rather frest installation of ubuntu 7.10. Often, when I scroll through documents (be it slashdot.org or a PDF-document), ubuntu will suddently freeze my mouse and keyboard and put the fan speed of my IBM Thinkpad T40p laptop to the max, as if the CPU is 100% busy doing something. The only thing I can do is to cut the power.

This behavior is worse than my old crappy installation of Windows 98, almost 10 years ago. Does ubuntu really not have a better protection of the kernel than windows 98 had?

I don't have any fancy hardware attached (all I have is a logitech USB-mouse and a HP Laserjet 1015).

Personally I believe it will take at about 10 years more before Ubuntu (and linux) is ready for the desktop in a mature form. I do agree that alot of progress has been made since 1998, but obviously not enough. I can't use this as my primary desktop platform.

---

### Post by Rafadagaffer on 2007-11-08
So you are basing your entire opinion on an operating system due to the fact that it locks up and not even trying to investigate the problem. :mad:

Open up System Monitor the next time you boot your laptop. Take a note of the process that uses the processor the most when your problem occurs. Post back in this thread, I'm sure someone will be able to help you

---

### Post by mivo on 2007-11-08
Or open a terminal window and type **sudo top** -- and watch what is hogging the CPU when you experience slow downs. It is probably something that can be corrected without much trouble. :)

---

### Post by philinux on 2007-11-08
At least lets find if there is something simple like trackerd causing the problem. Easily fixed.

---

### Post by PmDematagoda on 2007-11-08
> **loldrup said:**
> 
I don't have any fancy hardware attached (all I have is a logitech USB-mouse and a HP Laserjet 1015).


Fancy hardware doesn't really matter since you may have certain "Basic" hardware that may be incompatible with Ubuntu, so we could have better progress with your problem if you could post the specifications of your PC.

> Does ubuntu really not have a better protection of the kernel than windows 98 had?


Yes, in actuality the kernel is isolated from the rest of the OS as much as possible so that even if one part of the OS fails, you can still keep on using Linux/Ubuntu. This is not the case in Windows which is the main reason that Windows is so vulnerable against even the simplest of attacks or problems. In Windows, if one part fails, then you most probably cannot work with the entire OS.

---

### Post by adam.tropics on 2007-11-08
Some of that seems similar to [this thread]("http://ubuntuforums.org/showthread.php?t=604001") which you discarded, even though I see some of the same names trying to help....I know it can be incredibly frustrating, but stick with it! Oh and if you still haven't got anywhere with Ruby....another thread you posted, try [this one.]("http://www.urbanpuddle.com/articles/2007/05/09/install-ruby-on-rails-on-ubuntu-feisty-fawn")...take note of bits about repos (but make sure they are gutsy not feisty...sorry, slightly old guide)!

---

### Post by kvonb on 2007-11-08
-

---

### Post by loldrup on 2007-11-08
> **mivo said:**
> Or open a terminal window and type **sudo top** -- and watch what is hogging the CPU when you experience slow downs. It is probably something that can be corrected without much trouble. :)

I can't do that - the mouse and keyboard freezes when it happens. I only have a chance to find out if I have the system monitor window or the top app open when it happens, and then only if they are so keen as to keep monitoring after the lockup happens.
I have now turned them both on, so they are visible next to my browser/PDF-reader and am waiting for the crash to happen again.

---

### Post by loldrup on 2007-11-08
> **Rafadagaffer said:**
> So you are basing your entire opinion on an operating system due to the fact that it locks up and not even trying to investigate the problem. :mad:


I do so because the operating system is like a chain. If one important link fails, then the chain gets a high degrade in value. The Ubuntu OS may have alot of nice features, but if I can use them, because of the failure of one link in the chain, it's of no use that they are nice and nifty.

> **Rafadagaffer said:**
> Open up System Monitor the next time you boot your laptop. Take a note of the process that uses the processor the most when your problem occurs. Post back in this thread, I'm sure someone will be able to help you

I will do so

---

### Post by loldrup on 2007-11-08
> **adam.tropics said:**
> Some of that seems similar to [this thread]("http://ubuntuforums.org/showthread.php?t=604001") which you discarded, even though I see some of the same names trying to help....


Really sorry about that - I don't know why I totally forgot that thread :/

> **adam.tropics said:**
> 
I know it can be incredibly frustrating, but stick with it! Oh and if you still haven't got anywhere with Ruby....another thread you posted, try [this one.]("http://www.urbanpuddle.com/articles/2007/05/09/install-ruby-on-rails-on-ubuntu-feisty-fawn")...take note of bits about repos (but make sure they are gutsy not feisty...sorry, slightly old guide)!

I found some other thread describing the problem, and then I followed their solution :)

---

### Post by loldrup on 2007-11-08
> **PmDematagoda said:**
> Fancy hardware doesn't really matter since you may have certain "Basic" hardware that may be incompatible with Ubuntu, so we could have better progress with your problem if you could post the specifications of your PC.


Its a IBM Thinkpad T40p. You can see the specs here:

Chipset  	 Intel 855PM
Processor  	Intel Mobile Pentium M at 1.6GHz
Memory 512MB
Hard drive 	40GB
Display 	14.1" TFT display 1400x1050
Graphics 	64MB RADEON 9000
CD and DVD drive 	CD-RW/DVD drive
Networking 	802.11ab or 802.11b wireless (I don't know if it has a )

Very detailed specifications:
[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-58185](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-58185)

> **PmDematagoda said:**
> Yes, in actuality the kernel is isolated from the rest of the OS as much as possible so that even if one part of the OS fails, you can still keep on using Linux/Ubuntu.

It's a pitty these features doesn't prevent the mouse and keyboard from locking up.

---

### Post by mivo on 2007-11-08
> **loldrup said:**
> I have now turned them both on, so they are visible next to my browser/PDF-reader and am waiting for the crash to happen again.

Good. :) This way you should be able to see what hogs your CPU. Tracker and Scrollkeeper are possible culprits, though normally neither should slow your system to a lock-up even when they do their initial work. But anyway, **top** (started with sudo) should give you a hint what is going on.

---

### Post by adam.tropics on 2007-11-08
I had problems with tracker. Disabled it for now, but will look into it later. You can disable it from System-->Preferences-->Sessions

---

### Post by loldrup on 2007-11-09
The problem hasn't reoccured yet, so I can't come it any closer. Will wait patiently..

---

