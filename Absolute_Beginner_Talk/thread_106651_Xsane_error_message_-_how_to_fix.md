---
title: "Xsane error message - how to fix"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by bazcor on 2005-12-21
Hello and thanks for your time. I am trying to get my Genius Vivid3x to scan under Xsane. When I fire xsane up I get the error "Failed to open device 'gt68xx:libusb:002:002': Invalid argument.".

I have discovered the 'backend' (whatever that is!) is called GT68xx, do I need to install it? I am struggling with this stuff so please help a newb'.

TIA ... Barry

---

### Post by bazcor on 2005-12-21
OK I have managed to get this going now, it seems that placing the scanner firmware ccd548.fw into /usr/share/sane/gt68xx/ fixed the problem, although I did run through a few other things previously.

:) :)

---

