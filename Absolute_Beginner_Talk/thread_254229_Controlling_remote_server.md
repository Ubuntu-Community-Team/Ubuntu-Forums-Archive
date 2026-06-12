---
title: "Controlling remote server"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by gantww on 2006-09-09
Hello all,
I've used VNC before to control machines remotely on Windows. I've even used it in the past to control a Linux system from a windows one. Now, however, I will be attempting to control an Ubuntu Server from an Ubuntu laptop. Would you suggest VNC, or is there something better since I am going Linux to Linux?

Thanks,
Will

---

### Post by kdnoel on 2006-09-09
I have just finished setting up an ubuntu server and dual booting a Dell laptop... I only need access to the server in the closet (no monitor/keyboard) and I went with ssh.
It is awesome... call a terminal screen and ssh to the server and go. My server is for backup and I run Samba with a public directory for my 3 windoz machines.
I am a newbie to linux and am luving it!
:D

---

### Post by bodhi.zazen on 2006-09-09
I second ssh.

alternate webmin [Webmin](http://www.webmin.com/)

---

### Post by steve.horsley on 2006-09-09
> **bodhi.zazen said:**
> I second ssh.

I beg to differ. I would recommend ssh -X. ;)

---

