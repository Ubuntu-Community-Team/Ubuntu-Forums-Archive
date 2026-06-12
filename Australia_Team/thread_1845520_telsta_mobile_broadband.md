---
title: "telsta mobile broadband"
date: 2011-09-17
forum: Australia Team
---

### Post by saccam on 2011-09-17
Hi there, can anyone tell me how to set up a Telsta mobile broadband next g on ubuntu as telsta say they do not support ubuntu.

Thanks
Saccam

---

### Post by Jared Norris on 2011-09-17
It will depend on what sort of modem it is and what version of Ubuntu it is.

The team has set up a page at [https://wiki.ubuntu.com/AustralianTeam/Projects/WirelessBroadbandInformation]("https://wiki.ubuntu.com/AustralianTeam/Projects/WirelessBroadbandInformation") that would be a great starting point.

If you've had a look through that and still having issues please let us know (if you can find out) what modem it is and what version of Ubuntu you're using.

---

### Post by ikt on 2011-09-27
> **head_victim said:**
> If you've had a look through that and still having issues please let us know (if you can find out) what modem it is and what version of Ubuntu you're using.

Going to look into getting an internode test modem (Huawei E160E) and doing a quick screencast and tutorial on setting it up.

---

### Post by OptikalOz on 2011-10-04
I can confirm that Vodaphone Mobile Broadband"Prepaid" works on Ubuntu 11.04 It actually works better under Ubuntu then it did windows, Working with it under windows it continuous dropped out, So i am i quite happy so far with my transition into Linux. I did have to reboot to get it working.

Daryl

---

### Post by pjd99 on 2011-10-04
I've had success with my Nokia E51 and a BigPond Turbo USB adapter (lsusb: ONDA Communication S.p.A. ZTE MF636). 

For Telstra Bigpond Mobile, settings may need to be altered for different type of plan:
On Mobile Broadband tab:
Number: *99#
User [EMAIL="name@bigpond.com"]name@bigpond.com[/EMAIL]
password

APN: telstra.bigpond

PPP Settings
Allowed methods: CHAP
untick point-to-point encryption and echo, tick the rest.


EDIT: Network manager contains profiles for Telstra. Use the NextG one. Wow, a lot easier nowadays.

---

