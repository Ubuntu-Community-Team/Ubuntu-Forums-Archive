---
title: "ubuntu reinstallatoin plz help"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by articwolf939 on 2008-02-12
ok had vista and ubuntu  on one partition dual booting just fine using GRUB and i decied i wanted to wipe everything clean and start all over, i like to do it time from time so i put in my windows vista reinstallation DVD and let it do its thing,

when it came time i put in my windows driver DVD to load the drive in then in restarted to continue to load drivers and GRUB kicked in and gave me a error 22 and would let me contine the installtion and i cant figgure out how to get past it.

i was able to reinstall ubuntu just fine cos it was GRUB but i cant install vista because of it. is there anyway to get ride of GRUB from ubuntu so when i restart i can load vista? so far everything ive tried, doesnt work so any ideas?

---

### Post by kpkeerthi on 2008-02-12
I'm little lost here. So you want to install vista using your recovery DVD but you are unable to boot off the DVD?

---

### Post by articwolf939 on 2008-02-12
> **kpkeerthi said:**
> I'm little lost here. So you want to install vista using your recovery DVD but you are unable to boot off the DVD?

well yes and  no want to install vista using my DVD but i cant because when it restarts in the middle of the instaltion GRUB wont let it continue it gives me this error 22 becaus grub cant find any ubuntu files it needs cos ubuntu isnt installed yet, u understand now?

so i need to get rid of grub i believe

---

### Post by kpkeerthi on 2008-02-12
Yeah... OK. 

Have you changed the boot order in your BIOS? Move your CD device to the top as the first item in the list so that when the system reboots (in the middle of vista installation) it boots off the Vista DVD again. 

Once you are done with the installation your GRUB will be gone and will be replaced with Vista Loader.

---

### Post by articwolf939 on 2008-02-12
[QUOTE=kpkeerthi;4314885]Yeah... OK. 

Have you changed the boot order in your BIOS? Move your CD device to the top as the first item in the list so that when the system reboots (in the middle of vista installation) it boots off the Vista DVD again. 

Once you are done with the installation your GRUB will be gone and will be replaced with Vista Loader.[/QUOTE

well no my BOIS wont let me change things w\o the changeing the password and it wont let me change it thats anther problem and different time but i belive i have done it manualy ill retry it but any other suguestions?

---

### Post by kpkeerthi on 2008-02-12
There is usually a key (F12, in my case), that when pressed when at the very first start up screen where you see your BIOS loading, should let you choose the device to boot from.

---

