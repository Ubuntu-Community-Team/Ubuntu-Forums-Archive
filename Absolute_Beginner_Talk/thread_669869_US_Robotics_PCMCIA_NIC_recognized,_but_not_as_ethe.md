---
title: "US Robotics PCMCIA NIC recognized, but not as ethernet card"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by carpe_diem on 2008-01-16
Hi, everyone. I too am new to linux...wanted to migrate from windows for a long time, but never bit the bullet until now. I have a couple of questions that I can't seem to find the answers to, even after sifting through the threads on this site. Any help is greatly appreciated.

The machine is an old Compaq Presario 1245 laptop. 

The first issue I have is that there is no sound; from other posts I saw, it looks like this may not be an unusual problem. If I click on the sound icon, I receive an error message that states "The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured..." I looked in Add/Remove Programs and was going to try installing the GStreamer extra plugins to see if that helped, which led me to my next problem (no internet access).

The second issue is that I am unable to establish a wired internet connection via my US Robotics PCMCIA ethernet card. The device manager shows a 10/100 PCMCIA NIC TX, but the card does not appear in the Network Settings (the only connection available is a modem connection, and the laptop does have an internal modem). 

ifconfig shows:

lo        Link encap:Local Loopback
           inet addr:127.0.0.1  Mask:255.0.0.0
           UP LOOPBACK RUNNING MTU:16436    Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I'm guessing this is probably user error...I would really appreciate any and all help.

Thank you.

---

### Post by carpe_diem on 2008-01-17
Anyone? By the way, the install was gutsy.

---

### Post by Paulmd on 2008-01-17
In Ubuntu, old hardware typically either works right out of the box, or there's nothing you can do save to change it out. In case that's pessimistic, what is the model # of the nic, perhaps I can turn up some info on that card.

US robotics does not supply linux drivers on their website, last i checked.

---

### Post by carpe_diem on 2008-01-17
Hi. Thank you very much for your reply.

The US Robotics card is the USR7901...a dinosaur that I bought back in 2003 since the laptop didn't have an internal ethernet card. 

To be honest, I don't absolutely have to connect this machine to the internet if it'll be a lot of trouble. While trying to troubleshoot the sound problem, it seemed like the easiest way to install codecs, etc was to have internet access. 

The more pressing issue is really the sound problem. I intend to set it up as an educational machine for my daughter, and sound is definitely a necessity.

Any idea where I should start with troubleshooting the sound issue? 

Thanks again for your help.

---

### Post by Paulmd on 2008-01-17
> **carpe_diem said:**
> Hi. Thank you very much for your reply.

The US Robotics card is the USR7901...a dinosaur that I bought back in 2003 since the laptop didn't have an internal ethernet card. 

To be honest, I don't absolutely have to connect this machine to the internet if it'll be a lot of trouble. While trying to troubleshoot the sound problem, it seemed like the easiest way to install codecs, etc was to have internet access. 

The more pressing issue is really the sound problem. I intend to set it up as an educational machine for my daughter, and sound is definitely a necessity.

Any idea where I should start with troubleshooting the sound issue? 

Thanks again for your help.


Mixed news: the 7901 does not have linux drivers. But the 7901a DOES have a linux driver. If you have the 7901a, you're in luck. If not... try the drivers for the 7901a anyway, you may get lucky,  but don't expect them to work.

[http://www.usr.com/support/product-template.asp?prod=7901](http://www.usr.com/support/product-template.asp?prod=7901)

[http://www.usr.com/support/product-template.asp?prod=7901a](http://www.usr.com/support/product-template.asp?prod=7901a)

"Microsoft Windows 95, 98, NT 4.0, 2000, XP, Linux, and DOS
The following driver includes support for Microsoft Windows Windows 95/98/NT 4.0/2000/XP, Linux, and DOS. To download and install this driver:

    * Download and extract the files from USR_7901a.zip to a temporary location on your computer's hard disk drive.
    * Follow the instructions in the Readme.txt file to complete the driver installation."


I'll get back to you on the sound issue.

---

### Post by Paulmd on 2008-01-17
> **carpe_diem said:**
> Hi. Thank you very much for your reply.

The US Robotics card is the USR7901...a dinosaur that I bought back in 2003 since the laptop didn't have an internal ethernet card. 

To be honest, I don't absolutely have to connect this machine to the internet if it'll be a lot of trouble. While trying to troubleshoot the sound problem, it seemed like the easiest way to install codecs, etc was to have internet access. 

The more pressing issue is really the sound problem. I intend to set it up as an educational machine for my daughter, and sound is definitely a necessity.

Any idea where I should start with troubleshooting the sound issue? 

Thanks again for your help.

The sound issue:

The audio processor is an es1869. But linux drivers are not available from compaq, or from ess.

[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=20&lc=en&cc=us&dlc=en&product=94995&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=20&lc=en&cc=us&dlc=en&product=94995&lang=en)

[http://www.esstech.com/techsupp/drivers.shtm](http://www.esstech.com/techsupp/drivers.shtm)

I did find this: Since I don't have that sound card, so I can't test it myself to see if it works. 

[http://www.oliyiptong.com/blog/2006/07/15/old-hardware-help-in-ubuntu/](http://www.oliyiptong.com/blog/2006/07/15/old-hardware-help-in-ubuntu/)

---

### Post by carpe_diem on 2008-01-18
Thanks for the help! I tried the sound fix (downloaded the driver for the NIC too, I'll have to play with that tomorrow). 

I think the sound card settings in the options line may be incorrect for my card. I enabled alsa, then created the soundcard file using this:

alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1 isapnp=0 port=0×220 mpu_port=0×388 fm_port=0×330 irq=5 dma1=1 dma2=5

I then ran the test:

sudo modprobe snd-es18xx
sudo /etc/init.d/alsa-utils restart

Error message:

* Shutting down ALSA...
* warning: 'alsactl store' failed with error message 'alsactl: save_state:1253: No soundcards found...'...
* Setting up ALSA...

I just found some more info on this card on the alsa-project site: [http://www.alsa-project.org/main/index.php/Matrix:Module-es18xx](http://www.alsa-project.org/main/index.php/Matrix:Module-es18xx) 

Made it through the first step of creating the directory; just need to download the alsa driver package from another machine and move it over. Or get the NIC working on this one...I'll let you know how it turns out.

---

### Post by carpe_diem on 2008-01-18
Well, guys, it was fun while it lasted. I wanted to move to linux to *reduce* the amount of time it currently takes me to troubleshoot windows issues. So far I've spent way more time on the basics than I ever had to on such simple stuff with windows. This machine worked fine on windows xp, so I guess *sigh* I'll reinstall it. Thanks for your help.

---

