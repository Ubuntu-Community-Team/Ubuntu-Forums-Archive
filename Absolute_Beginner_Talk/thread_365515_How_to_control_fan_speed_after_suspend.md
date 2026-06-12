---
title: "How to control fan speed after suspend"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by pudgewack on 2007-02-19
I am a Windows user by default, but I am currently looking to broaded my OS horizens.So I decided to give Ubuntu a try.  I am current running Edgy (dual boot with Vista) on my desktop (AMD X2 4600+, Abit KN8, 2 Gigs Crucial Ram, nV 7600GS).
So far, I am very impressed with Ubuntu.Most everything work from the install. Everything that did not automatically work, I was able to get it up and running without much problem.
However, there is a problem that I have not found a soltuon for. When I resume from suspending my computer, the fans (both on the Heatsink fan and case exaust fan) spin much faster that if I just turn-on/reboot the computer. How do I get the fans to run at the same speed/volatage after suspsend then they did before I suspended the computer?

I am using the Gnone sensors app to get the temps and RPMS.
Before suspend, HS fan is around 1600 rpms and case fan around 950 rpms (CPU at 25 deg C).
After suspend, HS fan is aroung 2300 rpms and case fan around 1500 prms (CPU at 22 deg C).

Can anyone lead me in the right dirrections about fixing this issue? Is this an Ubuntu issue or possible a BIOS issue?

Thanks in advance,
Matt

edit:  The main reason why I want to lower the rpms of the fans are for noise reasons.I am trying to make this a very quite computer.

---

### Post by energiya on 2007-02-20
You could look at [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29"). You can find there how to control fan speed. You could try the restart funtion. Maybe make it run when you resume. I never tried this, so I don't know if it works. BTW lm-sensors is great.

---

