---
title: "wine internet configuration"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2006-12-25
How can I configure the internet connection in wine?  I am using a dial up modem. I've already tried with this:

ls -la ~/.wine/dosdevices/ln -s /dev/ttyS0 com1

And it appears to recognize my modem, but when I try to connect with a program it just remains on Connecting....

what should I do to configure it?

---

### Post by lucky_chouhan on 2006-12-26
It is not possible because wine is able to run windows programs not hardware.

run a program or run a hardware useing wine (both are very different process)

not possible.

it is possible in 2 ways.

1. find the info about your modem (it support linux).
2. find the linux driver of your modem.

---

