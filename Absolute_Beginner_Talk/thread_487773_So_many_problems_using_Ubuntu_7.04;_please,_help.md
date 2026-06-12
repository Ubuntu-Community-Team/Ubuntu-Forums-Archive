---
title: "So many problems using Ubuntu 7.04; please, help"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by thsa11 on 2007-06-29
Hi all,

I had to format my pc because of a virus and finally decided to get rid of windows, something i ve been planning for a long time. It is my first time using linux. I ve got a toshiba notebook A 70, pentium 4 speed at 3.06, 512 RAM, 60 Gb HD.

I got 3 main problems which i dont have a clue how to start to solve:

1 - Almost every time im trying to add or remove programs from my pc, it stuck, the mouse keeps moving but none buttons answer to the click, neither the switch off button. So every time i have to use the pc switch off button to restart it.

2 - I work also as a home broker at the share market. My agency said that my home broker program only works with internet explorer. Is there any similar program to be ran at linux or any thing i can do to turn mozilla able to open it?

3 - Sometimes Ubuntu gives me advices such as "some program couldnt run, type manually 'dpkg --configure -a'", for example. Where am I suppose to type it??

Thanks for all;

Thiago de Sá

---

### Post by Seisen on 2007-06-29
You can use wine and install internet explorer thier and to answer your third question put put that in the terminal like this

```
sudo dpkg --configure -a
``` to access the terminal go to Applications>Accessories>Terminal

---

### Post by Nyxess on 2007-06-29
the answer to question 3 is in the terminal (Applications->Accessories->terminal)

---

### Post by thsa11 on 2007-06-29
thanks guys, really happy with the answers!! 

A pity is that i tried to install the explorer as you said and, once again, the laptop stuck! Its the third time just today, one trying to install java plug in, another trying to install the ubuntu novelties and this last one with explorer...

Trying to install kopete now to use msn, hope it works!

1- Does anybody know why this is happening while downloading things? 

2- Less important but... does anybody know why when i go to hardware specifications all the blanks come as unknow! Nothing appears, neither processor speed, RAM, HD size...


Thanks for the help everybody!!

p.s.: as soon as i get this running properly on my pc i intend to be part on some translating team, willing for it.

---

### Post by hyper_ch on 2007-06-29
normally you install software from the repositories... you normally don't have to got to some website and download software...

---

### Post by Boris-- on 2007-06-29
1. for msn use Gaim, it works great. 

2. For IE emulation use wine or simmilar program (windows emulator). To install it type:
> sudo apt-get install wine. It will ask you for your root password, which should be the same as your login password. 

If you want to learn Ubuntu, you'll need to use console a lot. Oh, and most programs in Linux are installed from packages (the apt-get thing), not downloaded from web sites - for me it's a way better approach, it's fast and more user friendly. 

Hope you can solve your problems!

---

### Post by thsa11 on 2007-06-29
tranks guys!!! Im gonna do the wine thing, great!

Besides, im not using websites, the pc stuck while downloading from the repository. 

Im gonna learn how to use the console properly, thanks for the tips!

To use msn i got kopete, nice too.

Hope to be able to help people soon.

Bye

---

### Post by thsa11 on 2007-07-04
Looking at google, i found some people with the same major problem as me when trying to use ubuntu in Toshiba Notebooks A70 and A75, this might be the reason, even though i still havent got a clue on how to solve it, as im just a beginner. I hope the ubuntu developers have already faced this problem and worked out a solution.

Its a pity to say but after installing ubuntu 7.04 in my computer 4 times, i gave up using it meanwhile and now im using XP again, blarghhh. Still didnt give up, looking for someone nearby who knows how to deal with it, i wanna use ubuntu!

If anybody has any suggestion, please, let me know. I live in Sao Paulo, Brazil, Butanta district.

Thanks

---

### Post by Midahed on 2007-07-04
I can sympathise with your struggles.  I've only been running Ubuntu for a month or so, and it's been hard overcoming problem after problem.  In my case it's mainly because I'm running the 64-bit version...

If you have to use your laptop for work I'd suggest you should abandon the idea of just switching to Ubuntu.  Stick with Windows but, if you have the disk space, install Ubuntu in a dual-boot environment.  That way you can play with it when you have time and still have a reliable machine for your work.

Good luck!

Mike

---

### Post by ecs_pf5 on 2007-07-04
I agree with Mike. I'm suffering from the freezes too, amongst other problems, on a 64-bit machine.

I dual-boot with XP and just try and spend as much time as I can in Ubuntu, but drop back to XP as and when I have something pressing to do that just isn't working in Ubuntu.

Roll on the day when XP can go entirely.

64-bit is still just too young across the board, to be fully stable for end users like myself I suspect. That goes for all OSes. It should improve over time.

Isn't there some kind of virtual machine option too, so he could run XP 'inside' Ubuntu? I'm not sure on that. No experience with wine here as it doesn't like 64-bit

---

