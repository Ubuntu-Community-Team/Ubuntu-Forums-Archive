---
title: "empty /tmp on shutdown"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by gagatz on 2007-04-26
Hello, I want the /tmp directory to be emptied on every shutdown of the system. I think there should be written some kind of script to do this, and copied into /etc/rc0.d/ but I don't know how to do this.
Basically what i want is a command like

rm -r /tmp/.
or
sudo rm -r /tmp/.

to be run on shutdown. 

Does anyone have an idea on how to manage this?

thanks, niko

---

### Post by PaulFXH on 2007-04-26
This is [exactly]("http://www.arsgeek.com/?p=1515") what you're looking for.

---

### Post by Rinzwind on 2007-04-26
How to clean /tmp/ folder contents on shutdown

sudo cp /etc/init.d/sysklogd /etc/init.d/sysklogd_backup
gksudo gedit /etc/init.d/sysklogd

    * Find this section 

...
 stop)
  log_begin_msg "Stopping system log daemon..."
  start-stop-daemon --stop --quiet --oknodo --exec $binpath --pidfile $pidfile
  log_end_msg $?
...

    * Add the following line below it 

  rm -fr /tmp/* /tmp/.??*

    * Save the edited file 


FROM: [http://ubuntuguide.org/wiki/Ubuntu:Edgy/TipsAndTricks#Clean_up_Ubuntu_GNU.2FLinux_System](http://ubuntuguide.org/wiki/Ubuntu:Edgy/TipsAndTricks#Clean_up_Ubuntu_GNU.2FLinux_System)

---

### Post by bapoumba on 2007-04-26
/tmp files should be automatically cleared out each time you reboot, or on some set schedule.
> /tmp
    Here you'll find temporary files, most of them created by the system. This directory is generally erased on a regular basis, or every time you reboot the system. You can create files here if you want, just be aware they might get deleted automatically. 

[http://www.debian.org/doc/manuals/user/ch-files.html]("http://www.debian.org/doc/manuals/user/ch-files.html")

---

### Post by PaulFXH on 2007-04-26
> /tmp files should be automatically cleared out each time you reboot, or on some set schedule.
Do you mean the SYSTEM automatically dumps them on every reboot or you have to do something in order for them to automatically get dumped or what?
Certainly,  on my machine they don't get dumped automatically.
Can you please clarify your statement?
Thanks
Paul

---

### Post by bapoumba on 2007-04-26
> **PaulFXH said:**
> Do you mean the SYSTEM automatically dumps them on every reboot or you have to do something in order for them to automatically get dumped or what?
Certainly,  on my machine they don't get dumped automatically.
Can you please clarify your statement?
Thanks
Paul
Hi, it's from the link I gave you in the previous post. I've always thought /tmp was cleared on a regular basis (5 or7 days), if not at every boot. At least on debian.

Looking around, I found this:
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/18661]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/18661")
Interesting.

---

### Post by PaulFXH on 2007-04-26
@bapoumba
Thanks for the reply. It seems this topic is quite a bit more profound than I had assumed. Need to some reading but, in the meantime, I'm going to rely on the hack I offered in my first post.

---

### Post by bapoumba on 2007-04-27
@ PaulFXH: you're welcome. Fine with me. Please let us know if you come up with something.

---

### Post by sisco311 on 2007-04-27
```
man rcS
```

---

