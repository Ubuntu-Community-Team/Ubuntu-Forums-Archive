---
title: "Powertop results (confusing)"
date: 2010-04-27
forum: Any Other OS
---

### Post by keljaden on 2010-04-27
So I have been using mint KDE on my laptop for a while now, when I use the battery widgets profile to go into extreme powersave, my results in power top are so;

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (10.6%)         1.87 Ghz   100.0%
polling           0.0ms ( 0.0%)         1.60 Ghz     0.0%
C1 mwait          0.0ms ( 0.0%)         1333 Mhz     0.0%
C2 mwait          0.0ms ( 0.0%)         1067 Mhz     0.0%
C3 mwait          2.9ms (89.4%)          800 Mhz     0.0%


I am confused as these results,  Is my CPU still running at the 1.87 ghz the whole time, or is it running at the lower 800mghz like it should be.

here is my results on extreme powersave
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 4.6%)         1.87 Ghz    50.0%
polling           0.0ms ( 0.0%)         1.60 Ghz     0.0%
C1 mwait          0.0ms ( 0.0%)         1333 Mhz     0.0%
C2 mwait          0.0ms ( 0.0%)         1067 Mhz     0.0%
C3 mwait          3.0ms (95.4%)          800 Mhz    50.0%

Wakeups-from-idle per second : 319.9    interval: 15.0s
Power usage (ACPI estimate): 20.1W (2.5 hours) (long term: 193.5W,/0.3h)

Top causes for wakeups:
  36.7% (152.3)       <interrupt> : PS/2 keyboard/mouse/touchpad
  17.0% ( 70.5)       <interrupt> : extra timer interrupt
   9.0% ( 37.2)              Xorg : hrtimer_start_range_ns (hrtimer_wakeup)
   7.4% ( 30.8)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer)
   7.0% ( 29.1)       <interrupt> : eth2
   5.5% ( 22.7)      <kernel IPI> : Rescheduling interrupts
   3.9% ( 16.3)           firefox : hrtimer_start_range_ns (hrtimer_wakeup)
   2.6% ( 10.8)       <interrupt> : ata_piix
   1.8% (  7.5)    plasma-desktop : hrtimer_start_range_ns (hrtimer_wakeup)
   1.7% (  6.9)       <interrupt> : i915@pci:0000:00:02.0
   1.4% (  6.0)        pm-suspend : add_timer (wl_timer)
   0.8% (  3.4)     <kernel core> : hrtimer_start (tick_sched_timer)
   0.8% (  3.2)          knotify4 : hrtimer_start_range_ns (hrtimer_wakeup)

I normally get 4 hours of battery life while in windows7 (backlight/brightness off).  What else can I do to help get linux to that state?  I am still a novice so I might not understand a bunch of terminal stuff. 2.6 hours in linux is unacceptable IMO. 

I also made all the recommendations power top has made for me.

Help

---

### Post by yankee83 on 2011-09-26
Hi,

Have you managed to solve this problem?

---

