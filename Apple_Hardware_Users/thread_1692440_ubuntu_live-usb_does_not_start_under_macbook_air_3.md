---
title: "ubuntu live-usb does not start under macbook air 3,1"
date: 2011-02-21
forum: Apple Hardware Users
---

### Post by pasithee on 2011-02-21
Hi all,

I downloaded ubuntu here [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) and follow step 2 to create a bootable usb. but when I restart my macboook air and press 'alt' during the restart process I cannot see the usb disk.
What I have missed?

thanks a lot for your help,
pasithee

---

### Post by sviola on 2011-02-21
Take a look at the bottom of this [Ubuntu wiki page]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick#MacBook%20Air%203,2"). It tells how to install on a MacBook with a USB Stick, and the second to last paragraph tells how to get it to show up.

I hope that helps!

---

### Post by ierpe on 2011-12-18
This didn't solve the issue for me.

I can see the usb stick in Egit, but it won't boot properly on it...

Any application I could use to boot on first with a CD, and then boot on the usb stick?

---

### Post by mackaframa85 on 2011-12-18
Your hard drive needs to be in GPT partition format to boot from usb.  Install refit and run the option to sync partitons and see if your partition scheme is in GPT format, or maybe check under disk utility.

---

