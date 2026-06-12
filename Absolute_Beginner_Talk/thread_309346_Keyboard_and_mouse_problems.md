---
title: "Keyboard and mouse problems"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by SandersCraddock on 2006-11-29
Downloaded Ubuntu several days ago. First thing I must get out the way is, it is absolutely fantastic, it runs so smoothly. However I had a couple of major problems with my mouse and keyboard. My keyboard and mouse are both entirely unresponsive when used in ubuntu, however in Windows they are fine. They both are using the regular ps/2 connectors, however my mouse uses a usb to ps/2 adapter, so I plugged the mouse straight into the usb socket and it worked fine. That cleared up my mouse problem but my keyboard doesn't have an adapter. The wierd thing is in the bootup menu (with the option to start ubuntu, start it safe graphics mode etc.) the keyboard works fine. Can anyone point me in the right direction?

Just incase you need the info:
Packard Bell ps/2 keyboard
Microsoft optical wheel mouse USB and PS/2 compatible

Any help would be appreciated.

Alex Craddock

---

### Post by BoneKracker on 2006-11-29
This is just a guess, but it seems likely to me the problem is your X configuration (which is kept in a file /etc/X11/xorg.conf).  There's a section that looks something like this that may be misconfigured (don't copy this -- yours needs to be set specifically for your hardware and what's below didn't even come from an ubuntu system -- but the "Section" headings are the same and should point you to the part I would check out).  There may be helpful instructions at the top of the file as well.

```
Section "InputDevice"
        Identifier      "Keyboard0"
        Driver          "kbd"
        Option          "XkbLayout"     "en_US"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
EndSection

Section "InputDevice"
        Identifier      "Mouse0"
        Driver          "mouse"
        Option          "Protocol"      "auto"
        Option          "Device"        "/dev/input/mice"
        Option          "ZAxisMapping"  "4 5 6 7"
EndSection
```

To learn about configuring this, go the command line and type:
man xorg.conf

There should also be lots of documentation in the X directory or in the doc directory (I'm not on an ubuntu system right now, so I can't tell you where that is right now).

---

### Post by SandersCraddock on 2006-11-29
KK thanks. If it helps I am still using the CD so I dunno if I should install ubuntu to hard disk. I am a little worried I will have a big inopperable os on my hard drive. Anyone else got any ideas?

Alex Craddock

---

### Post by BoneKracker on 2006-11-29
Oh, I thought you had installed it.  The LiveCD has pretty good support for most hardware and loads what's needed.  Disregard what I said about the xorg configuration.

Here are a couple questions that might help narrow down what the difficulty is:

Do you have another ps/2 keyboard in the house?  If so, when you boot up the cd with that keyboard plugged it, how does it work?

If you have a usb keyboard, when you boot up with that how does it work?

What kind of computer is it?  Do you know what motherboard it is and/or what chipset the motherboard uses?

---

### Post by SandersCraddock on 2006-11-30
Will check the keyboards. Here are my system specs:


  Processor #1 : Intel Pentium 4 / 8FD08379
      Platform : Socket478 (mPGA478 Socket)
 Vendor String : GenuineIntel
      CPU Type : Original OEM Processor (0)
        Family : 15 (0)
         Model : 2  (0)
   Stepping ID : 9  (-)
      Brand ID : 9  (-)
          APIC : 0
HT Log.CPU Cnt : ----
   Name String : Intel(R) Pentium(R) 4 CPU 2.60GHz

Internal Clock : 2605.77 MHz
    System Bus :  801.78 MHz QDR
  System Clock :  200.44 MHz
Scalable Speed :  200.00 MHz
    Multiplier :   13.0  

    L1 I-Cache :  ----
    L1 D-Cache :    8K Byte
    L1 T-Cache :   12K uOps
    L1  Cache  :  ----
    L2  Cache  :  512K Byte
    L2  Speed  : 2605.77 MHz (Full)

    MMX   Unit : Supported
    SSE   Unit : Supported
   SSE2   Unit : Supported
   SSE3   Unit : Not Supported
   MMX2   Unit : Not Supported
  3DNow!  Unit : Not Supported
  3DNow!+ Unit : Not Supported

   Host Bridge : 8086:2570.02 [Intel 865G/PE/P/GV/848P]
IDE Controller : 8086:24DB.02 [Intel 82801EB (ICH5)]
    VGA Device : 1002:5961.01 [ATI RADEON 9200 Series]
  Memory  Size : 512M Byte
  Memory Clock : ----

    OS Version : Windows XP  Version 5.1.2600 Service Pack 2
-------------- : -----------------------------------
    StdFunc 0  : 00000002 756E6547 6C65746E 49656E69
    StdFunc 1  : 00000F29 00020809 00004400 BFEBFBFF
    StdFunc 2  : 665B5001 00000000 00000000 007B7040
    ExtFunc 0  : 80000004 00000000 00000000 00000000
    ExtFunc 1  : 00000000 00000000 00000000 00000000
    ExtFunc 2  : 20202020 20202020 20202020 6E492020
    ExtFunc 3  : 286C6574 50202952 69746E65 52286D75
    ExtFunc 4  : 20342029 20555043 30362E32 007A4847
    00000017h  : 000A0000 00000000 00000000 00000000
    0000001Bh  : 00000000 FEE00900 00000000 00000000
    0000002Bh  : 00000000 0000008E 00000000 00000000
    0000002Ch  : 00000000 0D12000D 00000000 00000000
    0000019Ah  : 00000000 00000008 00000000 00000000
    000001A0h  : 00000000 00000089 00000000 00000000

##--- Date 11/30/2006, Time 17:28:53 / 2.0.0.0

---

### Post by BoneKracker on 2006-11-30
Ok.  Looks like very standard hardware to me.

Personally, my next step would be to try a usb keyboard and try a different ps/2 keyboard, if I had one available.  Beyond that, you'll need someone else's help.

By the way, I'm using a an old ps/2 keyboard and ps/2 mouse at this very moment.

The computer itself isn't a Packard Bell (like your kbd), is it?  I owned one once and swore I never would again.

---

### Post by SandersCraddock on 2006-11-30
lol yeah computer is Packard Bell. 'Tis a nightmare, installed some new ram a while ago and the case took so long to put back together with all the twiddly clips and whatnot that in the endi just brought out the hammer. But it gets me by. Thanks for the suggestions mate, will report back when i have tried another keyboard.

---

### Post by SandersCraddock on 2006-11-30
yey new keyboard sorted everyting(ish).

Alex Craddock

---

### Post by SandersCraddock on 2006-12-04
kk I have a problem. Both keyboards work... intermintently, I think the mouse is sorted.

Alex Craddock

---

### Post by SandersCraddock on 2006-12-12
Problem solved had to take off some USB support in the BIOS.

Alex Craddock

---

