---
title: "wheres the actual driver?"
date: 2008-01-20
forum: Apple Intel Users
---

### Post by stealthsniper96 on 2008-01-20
forgive if this is a stupid question, but im new to linux. im trying to get the wifi on my C2D macbook working and am having no luck. so i downloaded the madwifi folder to my usb drive, which i then copied over to my linux partition. but theres all kina files and junk inside it, is there one thats just the driver that i could install in terminal?

---

### Post by Steveway on 2008-01-20
What version of Ubuntu do you have?
Afaik the Madwifi-drivers for Atheros cards is included by default and needs just to be enabled in the restricted-driver-manager. At least in Gutsy.

---

### Post by stealthsniper96 on 2008-01-20
> **Steveway said:**
> What version of Ubuntu do you have?
Afaik the Madwifi-drivers for Atheros cards is included by default and needs just to be enabled in the restricted-driver-manager. At least in Gutsy.

gutsy. how do i enable it?

---

### Post by cyberdork33 on 2008-01-20
Which Macbook do you have? Please give output of lspci. The driver in the repos does not work for the majority of Macs.

---

### Post by stealthsniper96 on 2008-01-20
> **cyberdork33 said:**
> Which Macbook do you have? Please give output of lspci. The driver in the repos does not work for the majority of Macs.

say what?

---

### Post by cyberdork33 on 2008-01-20
Which Macbook do you have? > Tell us which version of the Macbook you have. There have been several variations in hardware already

Give the output of lspci. > type "lspci" in a terminal and tell us what you get.

The driver in the repos does not work for the majority of Macs. > The method that Steveway is suggesting will likely not help you.



There is ALOT of documentation for Ubuntu on Macs, in order to give you the best info, we need to know specifics.
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)


Being so new to linux (and it sounds like the terminal in general), it may be best to do a little reading about the basics.
[http://linuxcommand.org/](http://linuxcommand.org/)
[http://www.fortunecity.com/skyscraper/y2k/60/primer/primer.html](http://www.fortunecity.com/skyscraper/y2k/60/primer/primer.html)

---

### Post by Steveway on 2008-01-21
> **cyberdork33 said:**
> Which Macbook do you have? Please give output of lspci. The driver in the repos does not work for the majority of Macs.

Well you learn something new everyday.
So did they change those cards on purpose? Or why didn't they stick with the default cards that we mere mortals use?

---

### Post by stealthsniper96 on 2008-01-21
> **cyberdork33 said:**
> Give the output of lspci. > type "lspci" in a terminal and tell us what you get.


yea i thought that was a terminal command, but all i get back is "command not found", thats why i asked.

---

### Post by cyberdork33 on 2008-01-21
> **Steveway said:**
> Well you learn something new everyday.
So did they change those cards on purpose? Or why didn't they stick with the default cards that we mere mortals use?
Apple usually uses VERY new hardware, and it is not often supported right away in Linux (due to the development lag for proprietary hardware). The Atheros cards were simply not yet supported by the driver version included with Gutsy. Add to that the often oddities that are encountered because Apple uses custom firmware and whatnot, and you often get incompatibilities.  You just have to get the newer code from the madwifi project and compile yourself.

> **stealthsniper96 said:**
> yea i thought that was a terminal command, but all i get back is "command not found", thats why i asked.
Be sure you are typing the correct letters... the lowercase L looks like an uppercase i. 

the command is lspci (starting with a lowercase L)

---

