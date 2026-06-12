---
title: "No Sound in Ubuntu &quot;The audio device is busy. Is another application using it?&quot;"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by RobbieB on 2008-01-20
So I updated to 7.10 awhile ago, but generally I've stopped using Ubuntu altogether now, simply because I have no sound any more.

All my sound worked fine when I was using 6.06, when I finally updated to 7.10 however, it disappeared never to return again =[

There are no system sounds, and if I try to play a multimedia file I receive the error message:
"The audio device is busy. Is another application using it?"

Restarting my computer does nothing, and I haven't installed any extra packages other than ones that appear in the "Add/Remove" list under Applications.

Any ideas?

---

### Post by zipperback on 2008-01-20
How did you update?

What kind of sound card do you have?


- zipperback
:popcorn:

---

### Post by RobbieB on 2008-01-20
I updated via the Ubuntu update manager when it popped up saying 'a new version of ubuntu is available'. The update seemed to go perfectly (no suspicious/error messages).

I have an ASUS P5B motherboard, onboard audio. All I can find about the onboard audio is that is uses a "Analog Devices AD1988A codec". The motherboard manual doesn't specify the audio chip.

---

### Post by bwtranch on 2008-01-20
Could you specify the output of the system?

---

### Post by RobbieB on 2008-01-20
I'm not sure what you mean by the output of the system.

I have 5.1 speakers connected to the sound card if that is what you mean?

But then the problem seems to be that it can't send a signal to the sound card because it's marked as 'busy'...

---

### Post by bwtranch on 2008-01-20
Sorry, i didn't know what level of user you are, if you go to the terminal, please post the output of lspci and ifconfig

You can do this by going to App->Acc->Terminal and entering the commands. Then paste those into the reply for all to see.

This is called a CLI Command Line Interface. This is the stuff we deal with. I'm not trying to be mean or anything, but, if you can't deal with this....well the terminal is it. You can do a lot of things in GUI and that's OK, but if you don't know how to use the terminal, you will never understand Unix/Linux.  (or computers, really)

---

### Post by Christmas on 2008-01-20
I have an Asus P5B-Deluxe. When I installed Ubuntu, the modules for my sound card were automatically loaded and I had sound without any configuring. However, try the following commands:
```
sudo modprobe snd-pcm-oss
sudo modprobe snd-hda-intel
sudo modprobe snd-pcm
sudo modprobe snd
```
Make sure your soundcard is not muted. Also try to install 'modconf'.
```
sudo apt-get install modconf
```
Then run it as root 'sudo modconf' and try to load other sound modules, and see which one gives results. Try the command 'lspci | grep Audio'. My output for this is:
```
TTY3 $ lspci|grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
05:02.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
TTY3 $ 
```
You probably have the same Audio Device, so it should work, you just have to load the proper modules if they are not already loaded.

---

### Post by RobbieB on 2008-01-20
lspci
```

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GT] (rev a1)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:02.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:18:F3:07:3C:09  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe07:3c09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:180079 (175.8 KB)  TX bytes:17598 (17.1 KB)
          Interrupt:17 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9300 (9.0 KB)  TX bytes:9300 (9.0 KB)

```

---

### Post by RobbieB on 2008-01-20
Christmas:
My lspci output from that command was the same as yours except for the Audio Capture device, which I'm guessing is just an extra feature you have and I don't ;)
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

```

Loading the sound modules seemed to go fine, except for 
```
sudo modprobe snd-hda-intel
```

It spat out the error 
```
FATAL: Module snd_hda_intel not found.
```

Still no sound. I've installed modconf and will try running that now...

---

### Post by bharadwaj on 2008-01-20
try re-installing the multimedia codecs, enable restricted drivers if any..
System->Adminstrator->Restricted Driver Manager.
"bwtranch" how can you just ask anyone the output of system with out even specifying output of particular thing? system output may even refer to showing up of configuration or even glx gares.

---

### Post by Christmas on 2008-01-20
It's just my TV-Tunner, I should have deleted that line :) Well... I must admit I don't know how to get that module in place. Maybe someone who does can help you? Again, install 'modconf' and try to load that module using it (though I guess it shouldn't be any difference, since the module cannot be found). Also, the command
```
lsmod | grep snd
```
should give you all the loaded snd modules.

LE: I googled it and came into this: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/134206](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/134206)

I'ts a lot of reading but you may find a response there.

---

### Post by RobbieB on 2008-01-20
I've got my restricted drivers enabled, there was only my nvidia drivers, and some 'lucent/agere linmodem controller' drivers installed. 

Not sure how to go about reinstalling multimedia codecs?

Also, when I was looking through my sound preferences (with everything on the default 'auto-detect'), I tried to test the sound playback and got the error message:

"audiotestsrc wave=sine freq=512 ! 
audioconvert ! audioresample ! 
gconfaudiosink: Could not open resource for writing."

---

### Post by RobbieB on 2008-01-20
ah Christmas, that looks like it's my problem.

bit heavy going with it all. I haven't compiled anything before, but I'll give what they are mentioning a go.

thanks =]

---

### Post by Christmas on 2008-01-20
Glad to help. I just hope it'll work for you. Also, [this](https://help.ubuntu.com/community/HdaIntelSoundHowto) is the Wiki page for Hda Intel Sound, maybe you can follow those instructions.

---

### Post by RobbieB on 2008-01-20
*bangs head against wall*

I think I'll just give up and just format and reinstall 6.06 x/

or just go back to windows till the next LTS release lol (assuming they fix it)

---

### Post by Christmas on 2008-01-20
May I recommend [Debian Lenny 'Testing'](http://www.debian.org/devel/debian-installer/) which I use and as I already said, the sound worked out of the box? Ubuntu is based on Debian anyway. Download it under 'Current weekly snapshot of Debian testing'.

---

