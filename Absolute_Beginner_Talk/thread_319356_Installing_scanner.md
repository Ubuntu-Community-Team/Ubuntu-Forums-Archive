---
title: "Installing scanner"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2006-12-15
I'm trying to install a scanner as it isn't seen when I go to Graphics > Xane Image Scanner. A window comes up and says "No device available"  How do I go to install a scanner from scratch please.  The scanner is a Xerox 2400 model.

---

### Post by Peter76 on 2006-12-15
Hi, I did a quick google on your scanner, and it turns out it isn't supported by sane; the default scanning backend in Ubuntu...

---

### Post by a.v.l on 2006-12-15
> **Peter76 said:**
> Hi, I did a quick google on your scanner, and it turns out it isn't supported by sane; the default scanning backend in Ubuntu...

Thanks very much.

---

### Post by matchstich on 2006-12-15
i have a acer/benq that is supported but i'll be dang if i can finger out how to get it working.
thanks
i have the firmware in my home folder. just can't finger out to get it to where ever it is supposed to

---

### Post by SuperMike on 2006-12-15
Hey, ya'll, I found a way to get scanners working in Ubunu when the SANE drivers don't detect it. Here's what I did.

1. I looked up my brand of scanner at the SANE official website. If I didn't find the driver there, I looked at which people or companies made the last scanner driver for that vendor of scanner.

2. I contacted that vendor to ask if they wouldn't mind using me as a guinea pig to add another scanner driver to their repretoire. To my surprise, the developer at ExactCODE took great interest in this! Why? Well, ExactCODE was trying to write an imaging system and they needed to be able to say they could support more scanners. So it was win-win.

3. The developer in Germany contacted me and had me download and install some USB sniffer software on Windows. I then installed my USB cable to the scanner, turned it on, ran 3 documents through the automatic document feeder, then 1 through the flatbed. I then turned the scanner off. He asked me to zip up the logfile for this and email it to him.

4. Twenty-four hours later, he had a couple drivers written in C that he wanted me to install. This was problematic and he was very patient with me. He told me a special procedure to go download the SANE-backends source, overwrite some of the driver files with his source code, and then compile and install it all in a very special way. I had to try this about 3 times before I followed the procedure properly and he was patient all day back and forth on email to help me get this right.

5. Sure enough, he had me type commands by the 3rd day, and it was feeding documents through my scanner. Now the whole world can benefit because the latest SANE-backends will contain this driver.

Cool, huh?

---

### Post by matchstich on 2006-12-16
[email]Guru@BenQ.com[/email] is the address for acer/benq if anyone wants to write and ask why they dont make drivers to work in ubuntu. i sent one

---

