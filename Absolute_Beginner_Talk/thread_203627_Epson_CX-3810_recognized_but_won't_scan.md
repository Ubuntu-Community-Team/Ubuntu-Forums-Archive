---
title: "Epson CX-3810 recognized but won't scan"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by JerryC on 2006-06-25
I spent the last 4 hours searching this forum trying to get Ubuntu to recognize the scanner.  The printer works OK.  I finally got it to be recognized by putting the following line in /etc/sane.d/epson.conf:  "usb 0x04b8 0x0818"
When I try to scan using either The Gimp or Xsane Image Scanner, I get the error:  Failed to start the scanner: "Error during device I/O".  Any ideas?

JC

---

### Post by catlett on 2006-06-25
Did you install libsane-extras? If not try installing it and see what happens. That solved it for me but it was a while ago when I dealt with the issue. Hopefully it is still the same now.

```
sudo apt-get install libsane-extras
```

---

### Post by JerryC on 2006-06-25
I kept working with it after I posted that message.  I have since sucessfully scanned a photograph.  I have no idea what I did to make it work.  I had installed that software before I wrote the message.  Thanks for your time though.

JC

---

