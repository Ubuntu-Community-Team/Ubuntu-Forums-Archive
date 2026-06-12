---
title: "Dial Up Problems"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by slackpipe on 2007-04-21
I have a US Robotics 5610 Modem.  It's a hardware pci modem.  I know it works in linux because i used it with linux before.  I can get it to dial out, but it hangs up during the handshake.  After digging around, i finally found the instructions i used to get it up in slack, now i just need to know what to do in ubuntu.  Hope that makes sense.

so...here's what i need to do:

Put the following in /etc/serial.conf:

/dev/ttyS4 uart 16550A port 0xd800 irq 9 ^fourport ^auto_irq skip_test baud_base 115200 spd_vhi autoconfig

(these become arguments for the setserial command during startup)

now i just tried to run the setserial command with these arguments and it tells me its (setserial's) not installed.  soooo, any ideas on what i should do?

thanx

sp

oh, and the modem works, i'm using it in xp (bah!) right now.  Please, help me get windows off my computer! :lolflag:

---

### Post by ieee488 on 2007-04-21
see if this link is helpful
[http://ubuntuforums.org/archive/index.php/t-8318.html](http://ubuntuforums.org/archive/index.php/t-8318.html)

I found it by Googling on "setserial Ubuntu"

---

### Post by slackpipe on 2007-04-21
doh!  i knew it would be something simple, that's why i posted in the beginner section.  lol

i think i googled setserial feisty fawn.

most appreciated, and quick too.

i'm off to linux, to try this out.  with any luck i'll post again from there.  :guitar:

---

### Post by slackpipe on 2007-04-21
w00t!!  I am online in ubuntu.  Thanks for your help.  once i got setserial installed it was just a matter of tinkering with it.

Now to get my anime playing, and it's gooooodbyyyye windows.  mwahahahahaha!

Thanx again,

sp

---

### Post by ieee488 on 2007-04-21
Glad to help. :) 

Even though I can boot into either Ubuntu or OpenSUSE along with Windows 2000, I have been lazy about doing that permanently. Shame on me. :rolleyes:

---

