---
title: "1st time installation problem"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by pavlick on 2008-02-04
HI,

I finally decided that I wanted to try Ubuntu, and Wubi was my best choice. I ran the installation for Windows, and when I booted into Wubi, installation continued. After the 2nd restart, I booted into Wubi once again, excited to try it out, but while Wubi was starting up, half-way, the splash screen turned into a black screen, I've waited about 15-20 min and nothing happened, no harddrive activity. So i did a hard reboot. the next thing i know, when i try to boot wubi or windows, my computer restarts. So i cannot but into Wubi or into my Windows. Please help, is there any way around this? What did i do wrong?

Thank you.

---

### Post by LowSky on 2008-02-04
I like how WUBi says its safe, and yet here you are with a messed up windows install...

Wubi is a beta product, and like all beta shouldn't be trusted.

Most likely you will need to fix your Windows Install (use the recovery option)

if you want to try out ubuntu use the LiceCD, it doesnt install anything and therfore can't mess up what is already installed

---

### Post by bodhi.zazen on 2008-02-04
Boot your windows recovery disk , 

Windows will come with some screens and look at "repair an existing XP" or something like that.

NOT THE AUTOMATIC REPAIR it will bring you nowhere.

You get three options,install windows,repair an existing XP or quit.

Choose "repair" ; You get a black screen where the existing install [a number] is displayed.

Choose that number and then it asks for your administrator password.

Type in ADMINISTRATOR if you don't know otherwise and pray it's the right one.

Then you get a prompt.

Type fixboot and see what it tells you.

If this doesn't work type fixmbr and you get a warning about messing up things,but ignore,and proceed.

This should make your windows bootable again.

See also: [http://ubuntuforums.org/showthread.php?&t=303765](http://ubuntuforums.org/showthread.php?&t=303765)

---

### Post by pavlick on 2008-02-04
Thank You!

---

