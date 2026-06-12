---
title: "[SOLVED] Can't connect to my bluetooth mouse"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by twrock on 2008-01-15
I have a cirago USB bluetooth adapter and I'm trying to connect a bluetooth mouse. I'm getting the following response to my attempts to get connected. Any ideas for me?

> ron@ron-laptop:~$ hidd --search
Searching ...
        Connecting to device 00:0A:94:C2:14:40
HID create error 13 (Permission denied)
ron@ron-laptop:~$ hidd --connect 00:0A:94:C2:14:40
HID create error 13 (Permission denied)
ron@ron-laptop:~$ 

---

### Post by twrock on 2008-01-15
For anyone who is as noob as me, "permission denied" should have clued me in that I needed to use "sudo" in front of the connect command to get permission. So, yes, I do have my bluetooth mouse working with my cirago adapter. (Well, at least at the moment; who knows after I do a reboot.)

Incidentally, this thread was really useful for me to get things working: [http://wiki.eeeuser.com/howto:bluetoothdongles](http://wiki.eeeuser.com/howto:bluetoothdongles) 
There is at least one typo though. There is a line that reads
"Also, edit /etc/defaults/bluetooth so that the Human Interface Devices are enabled:", but "defaults" should be "default".

---

