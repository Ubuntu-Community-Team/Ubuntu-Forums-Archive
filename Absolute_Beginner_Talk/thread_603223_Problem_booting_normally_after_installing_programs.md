---
title: "Problem booting normally after installing programs"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by 00sh on 2007-11-04
Hi, i've just installed gstreamer, kmplayer, and i enabled the ati driver which was restricted. However after the ati driver was installed i was prompted to make a restart. When i restarted it hangs during the load with a dark screen and nothing works. So i had to go to recovery mode to boot it up. After disabling the resrticted driver i tried restarting normally but it still hangs at the loading page giving me a blank black page and after 5mins its still hangs there. Can anyone help??

Im running a ati radeon xpress 200M graphic card.
Notebook model samsung r40
dual booted with vista business 32bit.

---

### Post by wPwLUi3N on 2007-11-05
are you sure you have properly installed the ATI Graphic card driver. Have you used some command line steps?

If you have a backup try this -

1. Make a fresh install
2. Use "ENVY" software to load driver.

Some packages can damage your system severly it is better to always keep a data back up  when you are still not working on a working enviorment.

Also any package can be responsible .. so always reboot after installing every package so tha you can be sure which one damage your system.

---

### Post by 00sh on 2007-11-05
No i just clicked the restricted software driver and it installed itself instantly. However, the system is running significantly slower after the installation and the network speed is crawling. Network speed proves to be alot faster when im running vista as compared to ubuntu i can't even connect to msn in ubuntu keeps prompting me connection erro.

---

### Post by daimaru on 2007-11-05
if you only get a black screen when restarting try hitting ctrl+alt+f1
then log in with your user and pass 
in terminal type
```
sudo dpkg-reconfigure xserver-xorg
```
select the right graphics driver etc and maybe on next reboot it will work :)

EDIT: please include your system specs in your profile ... makes it way easier to help without having to ask what graphics card etc you have

---

