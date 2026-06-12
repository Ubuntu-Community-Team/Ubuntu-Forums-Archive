---
title: "Ubuntu locks up at login screen !!"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by walter1971 on 2006-07-16
Hi All,

Have just spent two days installing different versions of Ubuntu. Finally after reading the forums found out that I should use the alternate iso. Installed and booted but keep getting to login screen and it locks up.

I am running the following

CPU - AMD Athlon 64
Mem - 1gb
HDD - Seagate 40gb
Video card - nVidia FX-5700
Gigabyte motherboard.

I am new to linux but by all accounts the one to use by the forums is Ubuntu. Could anybody please give me some ideas please?????](*,)

---

### Post by rockfloyd on 2006-07-17
hate to say it bud but maybe you should try another distro. sometimes certain distros and certain hardware just don't mix.

---

### Post by Thenotsowyzewun on 2006-07-17
Hi,

Do you get an [infinite sound loop]("http://www.ubuntuforums.org/archive/index.php/t-201507.html")? Fix / workaround courtesy of Brandon ([Metrix]("http://ubuntuforums.org/member.php?u=127556") on the forums):

1. Let Ubuntu get to the login screen. when the sound driver starts screwing up, hit ctrl + alt + F1 to get to a terminal and login
2. cd /etc/init.d
3. sudo ./alsa-utils stop <the sound should stop repeating>
4. ps -ef |grep aplay
5. sudo kill the aplay pid's
6. hit alt + F7 (takes you back to your login screen)
7. login (if it locks up again, do step 4 and 5 again except to grep and kill esd

Other than that there's no precents.

---

### Post by walter1971 on 2006-07-17
Hey Guy's

I have found one problem. After lots of reading through forums I found out about the xorg.conf. I found out that the default nvidia drivers are not correct and do not work. I ran the reconfig of the xorg file and and changed the driver to vesa. I got straight in on the loing screen and thing don't lock.

BUT BUT....Now I am experiencing random lock up at other points through the process. I also had the sound go into a loop like was mentioned above. I suspect that it has to do with the auto configuration process. I think that is has not worked correctly and I will have to manually configure all. 

Can you tel me where I can find a good guide through this process.

Thanks for you help guy's   :-k :-k

---

