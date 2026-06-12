---
title: "How does Ubuntu perform on early 2011 15&quot; macbook Pro?"
date: 2011-04-16
forum: Apple Hardware Users
---

### Post by BjornW on 2011-04-16
I'm very much interested in running Ubuntu (64bit) on the new 15" macbook pro (8,2), but I would like to get a bit more info about it. So if you own a 15" macbook pro could you please help me by answering the following questions:

1) Can you switch of the AMD Radeon GPU to save power?
2) Does the Thunderbolt port allow you to use an external monitor?
3) What is the battery life under Ubuntu? (please describe your usage)

Some more 'advanced' questions:

4) Is the quadcore benificial for running full disk encryption (due to the extended AES in Intel's 2.2 i7 cpu)?
5) What kind of IO throughput do you get with and without full disk encryption (please describe if you use SSD or HD incl RPM)
6) Can you tell me the exact type of Broadcom wireless chip used for wifi?

I would very much appreciate any answers to these question, thanks in advance!

---

### Post by Sloth on 2011-04-16
I have an 8,3 (17"), which is very similar.

(1) You can supposedly boot using EFI to use the integrated *Intel* graphics, but I've never managed to get that working.  The AMD GPU works perfectly.

(2) Yes, works like a charm.

(3) Battery life is good.  Tweaking everything to low power, I get the machine down to about 20W of power usage, which should be good for 4 hours or so.

(4) No idea.

(5) W/o encryption - and with an OCZ vertex 3 and my kernel tweaks to run in AHCI mode, here's a bonnie++.  I would say pretty good.

```
Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
niobe        15808M  1231  99 260462  20 127881  17 +++++ +++ 307127  20  6199 104
Latency             10080us     101ms     871ms    4213us   14837us    5930us
Version  1.96       ------Sequential Create------ --------Random Create--------
niobe               -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
Latency               581us     308us     380us     365us      16us     401us

```


(6) 03:00.0 Network controller: Broadcom Corporation Device 4331 (rev 02)

---

### Post by j0p4 on 2011-04-24
> **Sloth said:**
> I have an 8,3 (17"), which is very similar.

(...)
(
(3) Battery life is good.  Tweaking everything to low power, I get the machine down to about 20W of power usage, which should be good for 4 hours or so.

(...)


How many hours did you get over the OS X ?

Any troubles with the Wi-fi?

thks!:D

---

### Post by chili555 on 2011-06-21
> **Sloth said:**
> 
(6) 03:00.0 Network controller: Broadcom Corporation Device 4331 (rev 02)Using which driver?

---

### Post by inphektion on 2011-06-22
> **Sloth said:**
> I have an 8,3 (17"), which is very similar.

(1) You can supposedly boot using EFI to use the integrated *Intel* graphics, but I've never managed to get that working.  The AMD GPU works perfectly.

(2) Yes, works like a charm.

(3) Battery life is good.  Tweaking everything to low power, I get the machine down to about 20W of power usage, which should be good for 4 hours or so.

(4) No idea.

(5) W/o encryption - and with an OCZ vertex 3 and my kernel tweaks to run in AHCI mode, here's a bonnie++.  I would say pretty good.

```
Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
niobe        15808M  1231  99 260462  20 127881  17 +++++ +++ 307127  20  6199 104
Latency             10080us     101ms     871ms    4213us   14837us    5930us
Version  1.96       ------Sequential Create------ --------Random Create--------
niobe               -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
Latency               581us     308us     380us     365us      16us     401us

```


(6) 03:00.0 Network controller: Broadcom Corporation Device 4331 (rev 02)

I'd love to know any tweaks you did or anything you did to get the wifi working.  I really want to upgrade my 17" 5,2 to the 8,3 but looked like there was a bit i'd have trouble getting to work.  mainly wifi.  but i also planned to get the vertex 3, what kernel tweaks did you make for ahci mode?

---

