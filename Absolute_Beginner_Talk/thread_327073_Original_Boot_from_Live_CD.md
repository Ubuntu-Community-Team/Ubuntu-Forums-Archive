---
title: "Original Boot from Live CD"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by Torn Welly on 2006-12-28
I just finished downloading a Ubuntu Desktop CD. It works fine in one laptop, but not the other. I get a message as follows: /bin/sh:can't access tty; job control turned off

Can any one help?

---

### Post by jvc26 on 2006-12-28
When do you get this error? Is it once you have set bios to boot from cd, it does so and then you get the error? Or do you get the error once it has loaded the cd and is then at the selection screen of options? Its odd that it should boot on one laptop and not on the other.
Il

---

### Post by Torn Welly on 2006-12-29
The message appears after I get the list of options. (after I press "enter" at the options page) 
Option ! is highlighted - " Start or install..."  Thereafter the Ubuntu logo appears and seems to be trying to load, but then the message appears.

There is additional information appearing after the initial message as follows: (Initramfs) irq 15: nobody cared (try booting with the "irqpoll" option)
Disabling IRQ 15

On my other (newer) Laptop everything went smoothly

---

### Post by gn2 on 2006-12-29
There are a variety of different boot options to try, I think F6 brings them up.
The "noapic nolapic" option was the key to getting my P3 laptop going with Ubuntu (and other Linux Distros)

---

### Post by Torn Welly on 2006-12-29
:p :p Thanks for the help - I am now up and running

---

