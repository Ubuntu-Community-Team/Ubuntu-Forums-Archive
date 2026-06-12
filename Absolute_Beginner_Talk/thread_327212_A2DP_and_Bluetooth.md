---
title: "A2DP and Bluetooth"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by syalam on 2006-12-28
Hey Guys,

I am a new Ubuntu 6.10 user, I just recently made the switch from Windows so I'm totally new. I was wondering how I could get my Motorola HT820 headphones to work with Ubuntu? I stick my USB adaptor in but there is no indication that a new device has been inserted. When I turn on the headphones they usually pair automatically and I can listen to music, but music doesn't come through my headphones. Is there a bluetooth manager I could use to help me out? How can I get this working? Thanks.

---

### Post by DSXP on 2007-02-04
hey there!

I also own that headset and since I'm new to Ubuntu (Edgy) I have da same question.

But, googling, I found this:

[http://kubuntuforums.net/forums/index.php?topic=9534.msg38147](http://kubuntuforums.net/forums/index.php?topic=9534.msg38147)

Hope it works for you... I'll try and post ASAP.

Cheers!

-DSXP

---

### Post by syalam on 2007-02-04
```
modprobe snd-bt-sco
 apt-get install bluez-btsco
 hciconfig hci0 voice 0x0060
 hcitool scan
 # (shows device ID)
 btsco device_ID &
```

I tried that and it finds the MOTO HT820 but the last line gives me the following error:

syalam@syalam-laptop:~$ Error: hwdep next device (hw:0): Operation not permitted
Error: control open (hw:1): No such device

Any ideas?

---

### Post by zzarr on 2007-06-14
Hello!

I'm not new to Linux/Ubuntu and I'm using Fiesty.

I got a PC850 (Motorola dongle) as well as a HT820 headset.

But there isn't any driver for the PC850 dongle for Linux yet... sadly.

greetings zzarr

---

### Post by ffpcs on 2007-07-20
> **syalam said:**
> ```
modprobe snd-bt-sco
 apt-get install bluez-btsco
 hciconfig hci0 voice 0x0060
 hcitool scan
 # (shows device ID)
 btsco device_ID &
```

I tried that and it finds the MOTO HT820 but the last line gives me the following error:

syalam@syalam-laptop:~$ Error: hwdep next device (hw:0): Operation not permitted
Error: control open (hw:1): No such device

Any ideas?
As a COMPLETE noob, I have to ask the following questions:

What program do I use to ENTER the code suggested above?  Is it a shell script?  Is it code that is supposed to work spcifically with the Motorola PC850 USB adapter that comes with the HT820 headset?

---

### Post by FrostDust on 2007-09-16
Use the terminal, or Konsole, if you're using Kubuntu. It should be on the program menu, or on Ubuntu, Alt+F1 brings it up. That code is to install Bluetooth management software and scan for any devices. So far, I don't think it works for Motorola's HT820 headphones.

---

### Post by ulixes1983 on 2007-10-12
Hi,

i use the motorola HT 820 too.

And my works great!

I used this howto: [http://bluetooth-alsa.sourceforge.net/build.html](http://bluetooth-alsa.sourceforge.net/build.html)

But one thing: you must run a2dp as sudo, otherwise it does not work.

If you can speak German this will help you too: [http://wiki.schneidexe.de/linux/howtos/a2dp](http://wiki.schneidexe.de/linux/howtos/a2dp)

---

### Post by NuxIT on 2007-10-28
> **ulixes1983 said:**
> Hi,

i use the motorola HT 820 too.

And my works great!

I used this howto: [http://bluetooth-alsa.sourceforge.net/build.html](http://bluetooth-alsa.sourceforge.net/build.html)

But one thing: you must run a2dp as sudo, otherwise it does not work.

If you can speak German this will help you too: [http://wiki.schneidexe.de/linux/howtos/a2dp](http://wiki.schneidexe.de/linux/howtos/a2dp)

Hi, I tried following this guide but ran into a problem. I'm trying to get my Logictech bluetooth Headphones working. I managed to successfully get the hcitool to identify my device while it's in pairing mode.

The problem I get is when I try to follow this:
cd sbc
./bootstrap
./configure --prefix=/usr
make
sudo make install

I get this:

styles@t60:~/sbc$ ./bootstrap
./bootstrap: 7: aclocal: not found
./bootstrap: 7: glibtoolize: not found

i've tried it with and without the sudo. Am I missing something like a complier? BTW, I see the file boostrap in this /sbc directory. The file is green whatever that means?
TBH

---

