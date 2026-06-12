---
title: "Slow/not working external hd"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by ArnsteinK on 2008-01-14
I have a My Book(750gb) and it is REALLY slow on Ubuntu. Sometimes it's slow, and sometimes I cant even get to the main directory of the HD. It works fine on WIndows(bah). What to do?

---

### Post by ArnsteinK on 2008-01-14
Anyone?

---

### Post by Ryadt on 2008-01-14
do you dual boot with windows?

---

### Post by ArnsteinK on 2008-01-14
No. This is a laptop with only Ubuntu.

---

### Post by PetePete on 2008-01-14
run the command
tail -f /var/log/syslog

plug in the drive.

post the results of the command here..
might be that you have to do some editting on udev rules if the chipset isn't fully supported... but can only find out what it is by logs.

---

### Post by Ryadt on 2008-01-14
Ok...its just that I had a similar problem with my ext hd...I was dual booting with win xp and  everytime when it was crashing and I tried to boot in ubuntu, it was telling me that hd wasnt shut down properly...I had to reboot xp and then shut it down properly, then I could mount it on ubuntu...sorry cant help you

---

### Post by ArnsteinK on 2008-01-14
> **PetePete said:**
> run the command
tail -f /var/log/syslog

plug in the drive.

post the results of the command here..
might be that you have to do some editting on udev rules if the chipset isn't fully supported... but can only find out what it is by logs.

Should I run the command before plugging in the external hd?

---

### Post by PetePete on 2008-01-14
yes

---

### Post by ArnsteinK on 2008-01-14
Jan 14 15:46:09 arnstein-laptop NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Jan 14 15:46:10 arnstein-laptop avahi-daemon[4713]: Registering new address record for fe80::2c0:9fff:fe96:6829 on eth0.*.
Jan 14 15:46:19 arnstein-laptop kernel: [ 9136.196000] eth0: no IPv6 routers present
Jan 14 15:46:27 arnstein-laptop ntpdate[13080]: adjust time server 91.189.94.4 offset 0.145882 sec
Jan 14 15:46:27 arnstein-laptop kernel: [ 9144.028000] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jan 14 15:46:27 arnstein-laptop kernel: [ 9144.028000] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x25 data 8 in
Jan 14 15:46:27 arnstein-laptop kernel: [ 9144.028000]          res 58/00:01:00:00:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
Jan 14 15:46:27 arnstein-laptop kernel: [ 9144.028000] ata2: soft resetting port
Jan 14 15:46:28 arnstein-laptop kernel: [ 9144.668000] ata2.00: configured for UDMA/33
Jan 14 15:46:28 arnstein-laptop kernel: [ 9144.668000] ata2: EH complete

---

### Post by PetePete on 2008-01-14
sorry i cant help you, ive not got a clue, maybe someone else can!

ps.. upgrade to gutsy if you aren't running it, has improved hardware support.

---

### Post by ArnsteinK on 2008-01-14
Anyone? If not I have to install Windows:(

---

