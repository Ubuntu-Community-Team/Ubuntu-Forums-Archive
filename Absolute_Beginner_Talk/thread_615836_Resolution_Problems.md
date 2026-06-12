---
title: "Resolution Problems"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by mzdawg on 2007-11-17
I installed ubuntu on my computer, and the login screen appears and I can get to the desktop. But the resolution is wrong! The screen is blurry and jumbled up and I can`t change the resolution, hence the unreadable desktop. So is there a way to get to the terminal while the computer is starting up, and login  and change the resolution there?

---

### Post by Inxsible on 2007-11-17
what video card do you have?

---

### Post by mzdawg on 2007-11-17
Its ATI. Don`t know the name. BTW the resolution was working before, but I messed it up.

---

### Post by Inxsible on 2007-11-17
> **mzdawg said:**
> Its ATI. Don`t know the name. BTW the resolution was working before, but I messed it up.you can start with a clean slate by doing the following and then enable the resolutions that you want.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```then```
sudo dpkg-reconfigure -phigh xserver-xorg
```Choose all the resolutions that you want to enable.

---

### Post by mzdawg on 2007-11-17
ok but how do i get to the terminal

---

### Post by daimaru on 2007-11-17
ctrl+alt+f1
EDIT:
and i would use 
```

sudo dpkg-reconfigure xserver-xorg

```
the -phigh part messed up for me

---

### Post by mzdawg on 2007-11-17
ok thx guys I`ll try it out

---

### Post by Inxsible on 2007-11-17
> **daimaru said:**
> ctrl+alt+f1
EDIT:
and i would use 
```

sudo dpkg-reconfigure xserver-xorg

```the -phigh part messed up for mewhat was it that got messed up?

---

### Post by daimaru on 2007-11-17
im not sure but using the -phigh option got me to have a blank screen after running it so i did the reconfigure without it and i had the full setup menu etc. after that everything worked. 
im not saying that the -phigh won't work it just didn't when i tried it .
EDIT: by the way what does the -phigh option do ?

---

### Post by Inxsible on 2007-11-17
> **daimaru said:**
> EDIT: by the way what does the -phigh option do ?I am not sure why you had problems.

But -p is to set the priority.
I quote from the man pages
> -pvalue, --priority=value
           Specify the minimum priority of question that will be displayed.
           dpkg-reconfigure normally shows low priority questions no matter
           what your default priority is. See debconf(7) for a list.

---

### Post by Brautigam on 2007-11-17
what resolution and name brand of monitor? i may be able to help. your welcome. :popcorn:

---

### Post by mzdawg on 2007-11-17
ok i am trying to login in but it says grub. How do i log iin and type commands while the pc is booting up.

---

### Post by Raj_Dharwad on 2007-11-18
> **Brautigam said:**
> what resolution and name brand of monitor? i may be able to help. your welcome. :popcorn:

Dear Ubuntu Guru's,

I recently purchased a DELL 22inch wide screen flat panel monitor, i am running on gutsy, after reading a lot i was finally able to adjust the screen resolution to the optimal which is 1680x1050 but it doesnt fill the screen, i have a Nvidia Geforce FX 5200 128MB video card. So many times has it actually refused to accept tht resolution but later somehow it accepts it, one more prob is that i am not able to change the refresh rate to 60hz which is optimal & recommended, the only option i have is 50hz. Even though the res says 1680x1050 but it actually extends more than my screen and when i move my mouse to the corners the screen just extends till the border.:confused: It is some how bigger, how can i change the refresh rate to 60hz, any help is much appreciated. If you guys need to email me i dont mind somebody please help !!!!!!! anybody !!!!!!!!! my ekiga id is [email]rajdharwad1982@ekiga.net[/email].

regards,

Raj

---

