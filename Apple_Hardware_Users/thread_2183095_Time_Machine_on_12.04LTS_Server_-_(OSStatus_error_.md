---
title: "Time Machine on 12.04LTS Server - (OSStatus error 2.)"
date: 2013-10-23
forum: Apple Hardware Users
---

### Post by Casey_Friday on 2013-10-23
I've set up afp on my 12.04 headless server, and it's working well, but I can't seem to get a Time Machine backup going.  It finds the two backup volumes (one for my wife, and one for me), and it has me log in, but then I get the OSStatus error 2, saying "Time Machine can't access the backup disk..."

I've already chowned the /media/raidmount/Casey's Time Machine/ folder, and set permissions from 755 to 775 to 777, and nothing is working.

[IMG]https://lh4.googleusercontent.com/-wmdROAmAb14/UmgG-bGyjCI/AAAAAAAAF6A/fOS7e-vxU0s/s800/Screen%2520Shot%25202013-10-23%2520at%252012.25.28%2520PM.png[/IMG]

[IMG]https://lh6.googleusercontent.com/-0nO3_B-9hxw/UmgG-T8YThI/AAAAAAAAF6E/eH5g70MTBIU/s800/Screen%2520Shot%25202013-10-23%2520at%252012.25.44%2520PM.png[/IMG]

[IMG]https://lh6.googleusercontent.com/-Oyf2ugJe8v8/UmgG-7IGI6I/AAAAAAAAF6I/lLa5Q0XeaGM/s800/Screen%2520Shot%25202013-10-23%2520at%252012.25.53%2520PM.png[/IMG]

Has anyone else had this issue, and if so, how did you fix it?

---

### Post by Casey_Friday on 2013-10-27
Any ideas?

---

### Post by bapoumba on 2013-10-27
No real idea, sorry.
There seem to be some workarounds and hints on page 2 here : [https://discussions.apple.com/thread/2165328?start=0&tstart=0](https://discussions.apple.com/thread/2165328?start=0&tstart=0)

There are quite a few google pages with that error.

---

### Post by Casey_Friday on 2013-10-29
I figured it out!  The folders in my RAID mount (under /media/raidmount/) were called **Casey's Time Machine** and **Jessica's Time Machine**.  It was the spaces in those filenames that were tricking the setup up.  I changed them to **casey_tm** and **jessica_tm**, and the backups work now!  AWESOME!

Most of the thanks goes to comment 78 in [this post]("http://pwntr.com/2012/03/03/easy-mac-os-x-lion-10-7-time-machine-backup-using-an-ubuntu-linux-server-11-10-12-04-lts-and-up/").

[IMG]https://lh6.googleusercontent.com/-Y_jpySDw7k8/Um_Pu5Fnl4I/AAAAAAAAF9Y/QfsBsLOoELU/s800/Screen%2520Shot%25202013-10-29%2520at%252010.09.37%2520AM.png[/IMG]

---

### Post by bapoumba on 2013-10-29
Glad to see you got it to work !

---

