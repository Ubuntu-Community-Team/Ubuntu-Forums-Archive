---
title: "powertop: A USB device is active 100,0% of the time:"
date: 2008-11-14
forum: Apple Hardware Users
---

### Post by lv1001 on 2008-11-14
Hi,

Besides some other problems I have since upgrading to intrepid, the battery runtime is much worse than whath it used to be in hardy.

So I tried powertop with the result:

A USB device is active 100,0% of the time:
USB Gerät  6-2 : Apple Internal Keyboard / Trackpad (Apple Computer)

This is a Macbook pro 3,1 (Santa Rosa) using the xserver-xorg-input-synaptics driver from the mactel-support ppa.

Can anyone confirm this? I did not find anything about this in the forum or the web.

Thanks
  LV

---

### Post by kosumi68 on 2008-11-14
I get that a lot too, but I believe what changed are the suggestions from powertop, not your usb stack. I see no degradation of power consumption with intrepid - rather the contrary. Perhaps intrepid by default uses more power than hardy. I keep the brightness low, run with powersave governor, with laptop-mode-tools, without compiz, and tweak parameters in firefox-3. After enabling autosuspend, I get down to 80 weakups per second, consuming 8.5 watt. Long term battery estimate: 4.5 hours.

---

### Post by stream303 on 2008-11-15
Interesting - I see this too with PowerTop, although with PPC you don't see any of the cpu states - just the major causes for wakeups.

Something to look into for sure... even though my performance is ok.

---

### Post by lv1001 on 2008-11-15
Hmm, while your performance seems ok and 85 wakeups really is not alot, below is my powertop output. Unfortunately it is in german, but I think it is understandable nevertheless.
What is knotify for? But even without that 83 wakeups, there would be many left.
The huge discrepancy between ACPI and "long term" is something else that bothers me, but that had been like this in hardy and feisty before.

Thanks,
  LV

-----------------------------------------------------------------------

Cn                 Verweildauer       P-States (Frequenzen)
C0 (Prozessor läuft)    ( 7,6%)         2,21 GHz     0,0%
C0                0,0ms ( 0,0%)         2,00 GHz     0,0%
C1                0,0ms ( 0,0%)         1,80 GHz     0,0%
C2                1,2ms ( 0,1%)          800 MHz   100,0%
C4                3,6ms (92,3%)

Aufwachen pro Sekunde : 256,9   Intervall: 10,0s
Stromverbrauch (nach ACPI): 15,0W (1,7 Std.) (Langzeit: 11,6W, 2,3 Std.)

Häufigste Ursachen für das Aufwachen:
  29,5% ( 83,2)          knotify4 : schedule_timeout (process_timeout)
  25,0% ( 70,5)       <interrupt> : uhci_hcd:usb2, uhci_hcd:usb4, ath, nvidia
  17,5% ( 49,5)              kwin : schedule_timeout (process_timeout)
   5,1% ( 14,5)   USB Gerät  6-2 : Apple Internal Keyboard / Trackpad (Apple Computer)
   3,8% ( 10,8)      <kernel IPI> : Rescheduling interrupts
   3,7% ( 10,5)           kontact : schedule_timeout (process_timeout)
   3,5% ( 10,0)   hald-addon-cpuf : queue_delayed_work (delayed_work_timer_fn)
   2,9% (  8,2)   <kernel module> : usb_hcd_poll_rh_status (rh_timer_func)
   2,2% (  6,3)             artsd : schedule_timeout (process_timeout)
   1,1% (  3,2)            plasma : schedule_timeout (process_timeout)
   0,7% (  2,0)      <kernel IPI> : function call interrupts
   0,4% (  1,2)           krunner : schedule_timeout (process_timeout)
   0,4% (  1,1)              Xorg : do_setitimer (it_real_fn)
   0,4% (  1,0)              Xorg : nv_start_rc_timer (nv_kern_rc_timer)
   0,4% (  1,0)             artsd : do_setitimer (it_real_fn)
   0,4% (  1,0)     <kernel core> : sky2_link_up (sky2_watchdog)
   0,4% (  1,0)           klipper : schedule_timeout (process_timeout)
   0,4% (  1,0)          mouseemu : schedule_timeout (process_timeout)
   0,4% (  1,0)          mouseemu : do_nanosleep (hrtimer_wakeup)
   0,2% (  0,6)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer)
   0,2% (  0,5)             ath9k : ieee80211_sta_work (ieee80211_sta_timer)
   0,2% (  0,5)         gpg-agent : schedule_timeout (process_timeout)

A USB device is active 100,0% of the time:
USB Gerät  6-2 : Apple Internal Keyboard / Trackpad (Apple Computer)

---

### Post by _mario_ on 2008-11-15
> **kosumi68 said:**
> I keep the brightness low, run with powersave governor, with laptop-mode-tools, without compiz, and tweak parameters in firefox-3. After enabling autosuspend, I get down to 80 weakups per second, consuming 8.5 watt. Long term battery estimate: 4.5 hours.
how did you tweak your firefox? because i agree: it's consuming a lot of power right now.

thanks & ciao,
Mario

---

