---
title: "no sound...."
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by waggingwabbit on 2008-04-13
can anyone help me out with this? I started out having sound and now I dont...not really sure why. I have a creative audigy 2zs or something like that. I've tried the alsamixer thing people have recommended in other threads but it did nothing for me. I have no sound anywhere (im pretty sure atleast). any ideas guys? x.x

---

### Post by Gulyan on 2008-04-13
do you have sound from the live cd?

---

### Post by waggingwabbit on 2008-04-14
im pretty sure i did...my sound card i tihnk is properly detected....

---

### Post by mc4man on 2008-04-14
The first thing to try with creative cards is to double click the speaker icon in upper panel.There should be a switches tab, open it and set the output jack to the opposite of current setting, - checked>uncheck, unchecked>check

---

### Post by waggingwabbit on 2008-04-14
that didnt help =[

---

### Post by AmitT on 2008-04-14
> **waggingwabbit said:**
> can anyone help me out with this? I started out having sound and now I dont...not really sure why. I have a creative audigy 2zs or something like that. I've tried the alsamixer thing people have recommended in other threads but it did nothing for me. I have no sound anywhere (im pretty sure atleast). any ideas guys? x.x

I have the same problem with realtek HDA chip and ubuntu 8.04.

---

### Post by waggingwabbit on 2008-04-14
I'm on gutsy. I've just solved my problem though. i followed the trouble shooting on this site:
[http://linux.iuplog.com/default.asp?item=94639](http://linux.iuplog.com/default.asp?item=94639)

i think the last thing it said to do fixed it for me.

"Run alsamixer and turn off IEC related options
IEC is an input to certain high end sound cards that support optical (fiber optic) sound feed from such things as DVD players etc.. My sound card is SIS on board and certainly doesn't have ability of using IEC. But Ubuntu turned on those options by default.
To turn off those options, rum "alsamixer" (without quote) in gnome terminal. You can move around each option with your arrow key (right and left key.) Move to every IEC related options, turn off all of those options (use keyboard "m" to turn off.) After turning off hit "Esc" key to save, and type "sudo alsactl store" so that it is saved permanently. "

at first i thought it didn't work, but after restarting my computer i got my sound back =D i hope this helps anyone else who has this problem!

---

### Post by Crafty Kisses on 2008-04-14
Post the following output:
```
lspci
```

---

### Post by northern lights on 2008-04-14
Please post the output of ```
cat /proc/asound/cards
```

---

### Post by waggingwabbit on 2008-04-14
Its solved. turning off IEC from alsamixer did it for me o.o

---

### Post by Inxsible on 2008-04-14
> **waggingwabbit said:**
> Its solved. turning off IEC from alsamixer did it for me o.oGood. You can mark your thread solved by clicking on Thread Tools>>Mark Thread As Solved.

just in case..you didnt know

---

### Post by AmitT on 2008-04-15
```
:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent]
01:00.1 Display controller: ATI Technologies Inc RV370 secondary [Sapphire X550 Silent]
03:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

```
```
:~$ cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory

```

---

### Post by Chelives1928 on 2008-06-22
> **mc4man said:**
> The first thing to try with creative cards is to double click the speaker icon in upper panel.There should be a switches tab, open it and set the output jack to the opposite of current setting, - checked>uncheck, unchecked>check

dude you have no idea how glad i am that i stubmled upon this thread.   I've been trying to get audio to work and it was as simple as unchecking something.   thanks man

---

