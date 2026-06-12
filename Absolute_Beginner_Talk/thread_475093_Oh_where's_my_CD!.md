---
title: "Oh where's my CD?!"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Gafanhoto on 2007-06-15
Ok, so I'm a newbie who managed to install Slackware 11 with KDE but isn't able to install Ubuntu 7.04.

Downloaded the command-line install ISO, verified checksum, burned CD, verified CD's checksum, booted from CD and got to the main install page. 
Everything seems to do fine until the system tries to mount the CD filesystem. After a long period a message is displayed stating that the CD couldn't be mounted.

As I said before, I have Slack11 running( and WindowsXP), and had no trouble to mount the CD drive. The thing is that it gets mounted from /dev/hdd and not /dev/cdrom as I first expected.

So the question is:

Wich device does Ubuntu use to try to mount the CD?

Regards,

Gafanhoto

---

### Post by FleetAdmiral74 on 2007-06-15
I can't really help with your problem...but I just wanted to say its really interesting you got Slackware up but not Ubuntu! Thats like being able to replace a computer motherboard, but not be able to change the batteries in your wireless mouse. :D

---

### Post by Bachstelze on 2007-06-15
Why don't you use Slack then ? It's a great distro !

It's very weird that Ubuntu doesn't detect your CPU though, what motherboard do you have ?

---

### Post by FleetAdmiral74 on 2007-06-15
> **HymnToLife said:**
> Why don't you use Slack then ? It's a great distro !

It's very weird that Ubuntu doesn't detect your CPU though, what motherboard do you have ?

lol, maybe I totally missed it. Where does he mention his processor, i thought the prob was w/ his CD drive!

---

### Post by Bachstelze on 2007-06-15
I meant the CD drive, of course. It's late here :p

---

### Post by Gafanhoto on 2007-06-17
My motherboard is an A8NX-X with an AMD64.
Regarding installing slackware, it was pretty straigthforward. Burned the CD and everything just worked.
I want to take a look at Ubuntu because it seems to have more support than slack.
As I said, I can't mount from /dev/cdrom . Is it a link to /dev/hdd?

Thanks

---

### Post by reset3x on 2007-06-17
you may want to try /dev/hdc

EDIT:
Doh!!! I meant /dev/scd0

---

