---
title: "Kernel panic during boot with 3.5 on Asus Zenbook UX32VD"
date: 2012-07-09
forum: Asus Ubuntu Support (CLOSED)
---

### Post by liveag on 2012-07-09
I bought my Zenbook a few days ago and found the 3.2 kernel lacked some drivers I needed (useful touchpad driver, brightness buttons, etc.)
So I upgraded to 3.5 via the xorg-edgers repository.
For about a day everything seemed to go fine, but now I'm having kernel panics or freezes during every boot. 3.2 still works fine (I'm writing this with Ubuntu booted on 3.2)

This what I've been able to extract from the syslog:
```
  Jul  9 17:16:48 guru NetworkManager[1459]:  (wlan0): supplicant interface state: associating -> associated
Jul  9 17:16:48 guru kernel: [  214.646247] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646257] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646263] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646269] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646274] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646280] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646285] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646291] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646296] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646302] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646307] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646313] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646317] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646324] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646328] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646334] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646339] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646345] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646350] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646356] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646361] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646367] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646372] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646378] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646383] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646389] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646394] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646400] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646405] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646411] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646416] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646422] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646427] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646433] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646438] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646444] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646449] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646455] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646460] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646466] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646470] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646476] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646481] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646487] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Jul  9 17:16:48 guru kernel: [  214.646492] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646498] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Jul  9 17:16:48 guru kernel: [  214.646503] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646509] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Jul  9 17:16:48 guru kernel: [  214.646514] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646520] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Jul  9 17:16:48 guru kernel: [  214.646525] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646531] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Jul  9 17:16:48 guru kernel: [  214.646536] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646542] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Jul  9 17:16:48 guru kernel: [  214.646547] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646553] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Jul  9 17:16:48 guru kernel: [  214.646558] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646564] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Jul  9 17:16:48 guru kernel: [  214.646568] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646574] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Jul  9 17:16:48 guru kernel: [  214.646579] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646585] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Jul  9 17:16:48 guru kernel: [  214.646590] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
Jul  9 17:16:48 guru kernel: [  214.646596] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
Jul  9 17:16:48 guru kernel: [  214.646601] cfg80211: Disabling freq 5745 MHz
Jul  9 17:16:48 guru kernel: [  214.646604] cfg80211: Disabling freq 5765 MHz
Jul  9 17:16:48 guru kernel: [  214.646608] cfg80211: Disabling freq 5785 MHz
Jul  9 17:16:48 guru kernel: [  214.646611] cfg80211: Disabling freq 5805 MHz
Jul  9 17:16:48 guru kernel: [  214.646614] cfg80211: Disabling freq 5825 MHz
Jul  9 17:16:48 guru kernel: [  214.646647] cfg80211: Regulatory domain changed to country: AT
Jul  9 17:16:48 guru kernel: [  214.646652] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul  9 17:16:48 guru kernel: [  214.646657] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646666] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646674] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Jul  9 17:16:48 guru kernel: [  214.646683] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
Jul  9 17:16:48 guru NetworkManager[1459]:  (wlan0): supplicant interface state: associated -> 4-way handshake
Jul  9 17:16:48 guru wpa_supplicant[1793]: WPA: Key negotiation completed with 00:12:80:e1:8c:50 [PTK=CCMP GTK=TKIP]
Jul  9 17:16:48 guru wpa_supplicant[1793]: CTRL-EVENT-CONNECTED - Connection to 00:12:80:e1:8c:50 completed (reauth) [id=0 id_str=]
Jul  9 17:16:48 guru NetworkManager[1459]:  (wlan0): supplicant interface state: 4-way handshake -> completed
Jul  9 17:17:01 guru CRON[4219]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  9 17:18:44 guru kernel: [  330.341044] CPU0: Package power limit notification (total events = 495)
Jul  9 17:18:44 guru kernel: [  330.341050] CPU3: Package power limit notification (total events = 495)
Jul  9 17:18:44 guru kernel: [  330.341067] CPU2: Package power limit notification (total events = 495)
Jul  9 17:18:44 guru kernel: [  330.341071] CPU1: Package power limit notification (total events = 495)
Jul  9 17:18:44 guru kernel: [  330.348217] CPU0: Package power limit normal
Jul  9 17:18:44 guru kernel: [  330.348226] CPU2: Package power limit normal
Jul  9 17:18:44 guru kernel: [  330.348265] CPU3: Package power limit normal
Jul  9 17:18:44 guru kernel: [  330.348280] CPU1: Package power limit normal
Jul  9 17:19:49 guru kernel: Kernel logging (proc) stopped.
Jul  9 17:19:49 guru rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1422" x-info="http://www.rsyslog.com"] exiting on signal 15.

```Especially the "Package power limit notification" seems to happen a lot in the new kernel but I can't quite pinpoint the problem. Maybe it is because the kernel tries to clock the cpu to 2.4 GHz (maximum frequency according to cpufreq) although the cpu is designed to run on 1.9 GHz most of the time. Also, it could be a problem with the kernel misinterpreting flags in the new Ivy Bridge architecture or something similar.

If anyone could point me to a solution, I'd be very grateful.

---

### Post by fab.head on 2012-07-11
I don't know whether this could help solve your issue, but I've just found an updated version of the bios for your model (UX32VD).
The date of the file is July 10th, so it's pretty new:

[http://nbtsd.asustreiber.de/BIOS/UX32VDAS.207.zip]("http://nbtsd.asustreiber.de/BIOS/UX32VDAS.207.zip")

I've just downloaded an updated bios for my model (UX31A) from the very same site (link [here]("http://nbtsd.asustreiber.de/BIOS/?C=M;O=D")), and all seems to be fine.

---

### Post by peter rus on 2012-07-15
Please have a look at [http://ubuntuforums.org/showpost.php?p=12105892&postcount=60](http://ubuntuforums.org/showpost.php?p=12105892&postcount=60)

---

