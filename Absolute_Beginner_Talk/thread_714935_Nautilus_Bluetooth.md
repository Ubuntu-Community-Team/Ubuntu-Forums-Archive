---
title: "Nautilus Bluetooth"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by uchihaitachi on 2008-03-04
I'm having trouble browing my E61i via the bluetooth connection in Nautilus

I've managed to get bluetooth up and running
Ran the following command
sudo apt-get install gnome-vfs-obexftp

I can use nautilus to browse the phone for 2s and then I'll get the error
Nautilus cannot display "obex://[38:...]/E....
Please select another view and try again

I'm also unable to send a file from my phone to the laptop.

Sending files to the phone is not an issue.

Suggestions?

---

### Post by finer recliner on 2008-03-04
follow this guide:
[http://arstechnica.com/journals/linux.ars/2007/12/10/using-a-bluetooth-phone-with-linux](http://arstechnica.com/journals/linux.ars/2007/12/10/using-a-bluetooth-phone-with-linux)

it worked very well for me.

make sure that your phone supports the obex bluetooth profile, i know my phone does not, so i cant use nautilus to browse it. but i use bitpim for interacting with it just fine.
check your phone's user manual to see which profiles it supports.

---

### Post by uchihaitachi on 2008-03-05
I'm using a E61i so yes it does support OBEX. Somehow I'm the only person in this forum that's facing such a problem. Others just can't browse the device as they didn't install the gnome ftp obex.

---

### Post by uchihaitachi on 2008-03-05
It seems that I'm stuck at the browsing with OBEX.
Does the rest of the article still apply?

---

### Post by finer recliner on 2008-03-05
you can complete the tutorial i mentioned above without having OBEX work. they just tell how you get your phone to work with bitpim, which is better for managing files on your phone anyways.

---

### Post by phenest on 2008-03-13
I'm able to send a file using gnome-obex-send file from a terminal, but if I use Nautilus and right click the file>Send To>then select my mobile... nothing happens.

The phone is paired and set to Trusted.

Ubuntu Hardy
Nokia 6288

---

### Post by phenest on 2008-03-13
Doh! Turns out I just have to browse the device with the Bluetooth Manager.

[EDIT]
Mind you, I can send files to the phone using the Bluetooth Manager's systray icon, but it won't work from Nautilus.

---

### Post by phenest on 2008-03-22
There is a bug report for this: [bug 146935]("https://bugs.launchpad.net/ubuntu/+source/nautilus-sendto/+bug/146935")

---

### Post by jagrav on 2008-05-07
Same problem. Can transfer from computer to phone but not the other way around. Same phone.

---

### Post by bzzzzz on 2008-06-10
I managed to resolve this problem by making sure I had the notification area enabled on the top task bar.

I right clicked on the panel and then add to panel.  Then scroll down until you find the notification area.  Then when your dongle is plugged in and bluetooth on phone turned on, hit the icon and browse device.

---

