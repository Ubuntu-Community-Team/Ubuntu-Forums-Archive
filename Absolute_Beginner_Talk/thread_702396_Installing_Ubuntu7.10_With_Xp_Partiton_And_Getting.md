---
title: "Installing Ubuntu7.10 With Xp Partiton And Getting Rid Of The Blak Screen On Boot"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by marko-slo-27 on 2008-02-20
HI i am a newbie and i had problems to install ubuntu7.10 
i found the solutions in this forums but the answers are spread across the forum so i decided to out a new thread
i can tell what i did to install ubuntu(i have windows xp installed and amd64 +geforce 8800gts graphic card)
:


Burn the live cd in your os ....
boot from cd
when the boot screen loads up press f6 and go to the end of the command line and delete QUITE SPLASH
press enter
now i was able to enter into the system live cd 
find in the menu the partion manager ithink is in system
make 2 partion one small for swap(i did 3 gb) and other for your system ubuntu(minimum 7gb) 
install from desktop
manually select the partitons  and edit them. turn the small one on swap and the big one to / infront
install....
restart..
select ubuntu....
if the screen goes black this is what i did
start in recovery mode ....and type
sudo nano -w /boot/grub/menu.lst
list and delete the quite splash entries
save and exit 
restart thats it 
i hope it was helpfull in my case solved the problems with black screen on boot:guitar:

---

### Post by mikewhatever on 2008-02-22
Most probably, you just need to install the nvidia driver for your card. There is a GUI took for that, but since you get black screens, get back to recovery mode and type <apt-get install nvidia-glx-new>. That should download and install the driver + dependencies, so you must have internet connection. Afterwards, try booting into regular mode. If you get an error about xserver unable to start, that means it has to be reconfigured with <sudo dpkg-reconfigure xserver-xorg>.

---

