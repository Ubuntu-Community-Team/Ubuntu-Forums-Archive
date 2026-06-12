---
title: "Boot freezes randomly &amp; other questions"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by Cuppa-Chino on 2006-08-30
Hi,

first I have spent time searching the forums but I have not found an exact replica of my problem:

my comp spec:

Ubuntu, kernel 2.6.15-26-686

P4 2.4GHz
1gb ram
Asrock P4Dual-880Pro motherboard based on VIA PT880 Pro
Soundblaster Audigy 2 ZS
Radeon 9500/9700 Powercolor 128mb AGP
Liteon DVD-Writer
Generic DVD-Rom
Edimax Wireless card based on RALink Rt61 chipset
Webcam ICM532 chipset based

so I installed Ubuntu (again I had tried previously but given up) and got the system up, after much ado got the wireless card working, etc etc
[obviously cannot get ATI Radeon to work but that is not my question].

Now it happens from time to time that the system fails to boot from time to time, this is truelly random, just now it did not boot twice and third time lucky - I have no problems with Windo$.... mem is fine

**which log should I check and what specifically look for** - so I can post that for more assistance

This is the one I am slightly worried about as I had previously taken an image of my Linux but now it does not appear stable any more, I do not really want to go back to that old image though.


_Next question_

have tried hibernating system in past but that does not seem to work, is there anything I can do to check requirements for hibernate?

_Next question_
how can I install SMP enabled kernel without loosing all my settings etc? will a synaptic kernel upgrade now take all the things with it - or will I have to add webcam ect manually?

---

### Post by Cuppa-Chino on 2006-09-02
Bump

---

### Post by CapnCaffeine on 2006-09-03
I suspect your freezing is from your hard drive running slowly, if you are running off of an ATA/IDE drive.

See this Howto for my Asrock 775Dual-VSTA motherboard which uses the PT880 Pro chipset.

[http://home.rochester.rr.com/msarnov/AsrockUbuntuHowTo.html](http://home.rochester.rr.com/msarnov/AsrockUbuntuHowTo.html)

You can run the 686 kernel which is SMP enabled and keep your settings. However, I suggest you try my HOWTO which will also enable your ATI video card.

Cappy.

---

### Post by Cuppa-Chino on 2006-09-04
Hi I do not think DMA is the issue, I managed to turn that on properly (I think)

I ran bonnie++ 
```
ubuntu@ubuntu:~$ bonnie++
Writing with putc()...done
Writing intelligently...done
Rewriting...done
Reading with getc()...done
Reading intelligently...done
start 'em...done...done...done...
Create files in sequential order...done.
Stat files in sequential order...done.
Delete files in sequential order...done.
Create files in random order...done.
Stat files in random order...done.
Delete files in random order...done.
Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
ubuntu   2G 25694  86 34366  20 12165   5 14105  61 26306   4  84.4   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16  1083  82 +++++ +++ 28930  83  1258  91 +++++ +++  3121  78
ubuntu,2G,25694,86,34366,20,12165,5,14105,61,26306,4,84.4,0,16,1083,82,+++++,+++,28930,83,1258,91,+++++,+++,3121,78

```

those speeds are not great but at least better than the 3-4mb/s you mentioned. will give your instructions a try though.

---

