---
title: "scanner"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by veritas366 on 2006-01-28
I downloaded a linux driver for the epson perfection 4180 but the directions are unclear.   I THINK it is  a sane frontend.  In any event, when I have it plugged in, neither the program itself nor sane detect any scanner whatsoever.  I specifically bought this scanner because I'd found the driver for it.  Here's where the driver lives:

[http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)

I know I haven't given much info, but the only output I ever get is no scanner detected.  I feel as if there are steps I haven't done correctly.  Should I also have "xsane"?  "quiteinsane"?  Should I NOT have either of those.

Trying again (after kernel update) I see that sane detects the scanner but xsane says no device available (it says it in a popup...so it's not in the terminal output. ) 

found USB scanner (vendor=0x04b8 [EPSON], product=0x0118 [EPSON Scanner]) at libusb:001:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

When I use Image Scan (the program from avasys) it just says can't send data to scanner.  

So what do I need to do to make it work?

---

### Post by Stinger on 2006-02-01
I'm afraid you scanner isn't supported by [SANE]("http://www.sane-project.org/") yet , I can't find it 
in the [Supported Epson section]("http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-EPSON").

I did a search too using [epson perfection 4180]("http://www.sane-project.org/cgi-bin/driver.pl?manu=epson&model=4180&bus=any&v=&p=") , it shows your scanner is supported in the epkowa backend and not included in SANE.

So it seems you are doing the right thing , trying to setup the epkowa backend , but I have no experience in doing so.

I found this [FAQ onthe epkowa backend]("http://www.avasys.jp/english/linux_e/faq_scan.html") in case you haven't seen it.

My advice would be to get scanner that is supported by SANE at the first given chance (yes I know it involves money) , or [contact the SANE developers]("http://www.sane-project.org/imprint.html") to see if the was any chance of getting your device supported.

Hope it helps.
:-k

---

