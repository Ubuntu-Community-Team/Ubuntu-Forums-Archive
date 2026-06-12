---
title: "AMD Turion(tm) 64 X2 Mobile Technology TL-50"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by philbygr on 2007-05-27
i have installed Ubuntu in a ASUS A6T laptop. before that i tried to install Debian. In Debian the system found my dual core prossesor, in ubuntu it see only the one (i think that is the reason i have to many freezes) i have tried to do many things, i read here but  i'm failed.. i'm begginer in Linux. 
 # cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 72
model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-50
stepping        : 2
cpu MHz         : 800.000
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
bogomips        : 1608.92
clflush size    : 64
 
that is what i see, when i tried to change config (# sudo gedit /boot/config-2.6.20-15-386)
i change only that # CONFIG_SMP=y
am i right? 

can anyone post the commands, i must enter to recognize the dual core prossesor? 

i have tried to follows the kernels advice whicj i found in a post but i'm failed.

thanx

---

### Post by Kobalt on 2007-05-27
Did you install the 64bit or the 32bit version of Ubuntu ?

---

### Post by philbygr on 2007-05-27
where i can find it? :p i install ubuntu-7.04-beta-desktop-i386 
these are my first steps in Linux....

---

### Post by Kobalt on 2007-05-27
Then it's the 32bit version. 
The command line you gave us the output shows "cpu MHz : 800.000" : I think that's what interesting you. It doesn't mean you CPU has 800Mhz capacity, it means it currently run at this speed. Your CPU charge isn't constant and on laptops it is adapted to the work load. 
Using the 32bit version of Ubuntu instead of a 64bit one is very unlikely to be the reason for your crashes. 
Indeed if you wanted to use the full power of your CPU you would run the 64bit Ubuntu. Check the [x86_64]("http://ubuntuforums.org/forumdisplay.php?f=134") section of this forum to learn more about the differences between the two versions.

---

### Post by philbygr on 2007-05-27
can i update or upgrade my version or i must install it again as first time?

sorry for my stupid questions :s

---

### Post by Kobalt on 2007-05-27
You cannot upgrade or migrate from a 32bit version to a 64bit. You'll need to do a clean install all the way back.

---

### Post by Austin_KW on 2007-05-27
You do not need the 64 bit install, the 32 bit will be fine and have less compatibility issues.
But as you noticed you are running the non SMP kernel. You cannot change this by editing the lernel config file as this is the file that was used to control the kernel build.

You probably want the generic kernel. If you do not have it you should be able to install it.
sudo aptitude install linux-image-generic

---

### Post by philbygr on 2007-05-27
0 packages upgraded, 0 newly installed, 0 to remove and 238 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
 that's mean that i have already install it?

---

### Post by Kobalt on 2007-05-27
Indeed, Ubuntu comes with the generic kernel installed by default. So unless you changed it (which I doubt), you run the generic kernel. Just to make sure you can run *uname -r* in a Terminal. 
You do need to upgrade though :) > 238 not upgraded

---

### Post by philbygr on 2007-05-27
#uname -r
2.6.20-15-386

when i tried to do all updates, the X cannot start :p 

i do some of them now :d

---

### Post by Kobalt on 2007-05-27
You don't have a generic kernel here. You use the 386 one. Given that you have the linux-image-generic package already installed that means you have both kernels installed but that you boot on the 386 one. You can change on which kernel you boot when you start your computer. When you get to the Grub screen, if you don't see a list then press Esc to see it, and select the generic kernel.

---

### Post by philbygr on 2007-05-27
4 min. to install updates and i go for reboot, u are right for that, i have already see 386 and generic kernel but i 'm afraid to do any changes at boot yet :p 
thanx!

---

### Post by Austin_KW on 2007-05-27
Or edit /boot/grub/menu.lst and add a "default x" where x is the offset to the kernel you want to boot, 0 for the first kernel, 1 for the second kernel ...; Count the "title" entries.

---

### Post by Kobalt on 2007-05-27
You're welcome.

---

### Post by philbygr on 2007-05-27
i start with generic- kernel. my linux see my cpu ok but now i have another problem..... i can't see the top of windows to move them or do anything else... and when i push the button whicj show my desktop it tells me, your window manager does not support the show desktop button, or you are not running a window manager. and i can't see the windows i have open in down bar.... 

i don't think that i like it :p

any ideas?

---

### Post by Kobalt on 2007-05-27
Did you install something like Beryl or Compiz ?

---

### Post by philbygr on 2007-05-27
i do somes of 238 updates :p i don't remember which.... i must install something to be in the default window manager?

---

### Post by philbygr on 2007-05-27
i see it now. i have compiz installed. what is that?

---

### Post by philbygr on 2007-05-27
i remove it but it still the same! what happends now?

---

### Post by philbygr on 2007-05-27
#metacity in a terminal. it is ok now

---

