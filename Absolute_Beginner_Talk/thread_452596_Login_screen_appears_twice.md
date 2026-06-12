---
title: "Login screen appears twice"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Gleep on 2007-05-23
For a few weeks now, and I'm not sure what triggered it, but every time I log in, I've been having to do so twice before I'm brought to my desktop. Sometimes it will just load as normal, other times Gnome will detect itself running already (or I presume it's gnome) and terminate, and I will have to restart since I don't know how to start it again.

It's not as if it's something I can't live with, but it's grown somewhat annoying and obviously, it's a problem, if anyone knows what's wrong I'd be very grateful for any advice =]

Thanks in advance.

---

### Post by wpshooter on 2007-05-23
Are you saying that it does this on an ALWAYS/CONSISTENT/EVERYTIME basis or just most of the time ?

What version of Ubuntu is this ?

---

### Post by Gleep on 2007-05-23
> **wpshooter said:**
> Are you saying that it does this on an ALWAYS/CONSISTENT/EVERYTIME basis or just most of the time ?

What version of Ubuntu is this ?
Most of the time, there is the odd time when it doesn't happen, but it's hit or miss.

I'm using 7.04 (Feisty Fawn)

---

### Post by wpshooter on 2007-05-23
Did you use a version of Ubuntu prior to your use of Feisty ?  My guess is that this is probably a bug in Feisty.  I tried installing it on one of my systems recently and it did not take me very long to switch that machine back to Edgy.  I don't think Feisty is ready for prime time yet, to many bugs remaining.

Good luck.

---

### Post by Gleep on 2007-05-23
> **wpshooter said:**
> Did you use a version of Ubuntu prior to your use of Feisty ?  My guess is that this is probably a bug in Feisty.  I tried installing it on one of my systems recently and it did not take me very long to switch that machine back to Edgy.  I don't think Feisty is ready for prime time yet, to many bugs remaining.

Good luck.

Yes I used Edgy which was fine. Ah well *shrug*

---

### Post by kaaskop on 2007-06-12
I have to login twice too!

Only the second login I get a small applet with the picture I used to login to my Windows partition, I'll guess that little picture came with the windows migration.
But login twice is a bit much.

---

### Post by visionary on 2007-06-23
I am new to linux i have to admit that and this is my very first post on any unix related issues as i just migrated from XP to Ubuntu recently...as of now i do not have solution,...but recently i did switch user and logged in and ever since then i am encountering similiar problem. I also read somewhere this is a known problem in this distro...let's hope we see a solution soon

---

### Post by visionary on 2007-06-23
Folks...i am back.[COLOR="Red"]**Seems like mine has been solved now**[/COLOR]

Here is what i did...


_________________________________START_____________________________


1)I did a xserver reconfig. I deliberately choose VESA instead of my nvidia VGA driver
The command issued at terminal was>>>  **sudo dpkg-reconfigure xserver-xorg**

2)Then i installed fast user switch applet
The command issued at terminal was >>>  **sudo aptitude install fast-user-switch-applet**

3)I**rebooted**  the system

4)I **reinstalled** my VGA (Nvidia for me) driver using Automatix2 program. For those who do not know what is Automatix2, let me put it this way " a program with GUI which could be of great help to you to install plenty of drivers and applications". You can download the program from  [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

5)I **restarted** the system and it went fine.

__________________________________END_______________________________

Now i only need to log in once.What i see now is, there is a short delay before i get a chance to login.I can see the delay is caused because the system is "killing" the first bugged login window. This is much better than logging in twice. 

As i said i am new to linux, do not ask me what is the cause.You should ask some gurus...from my understanding, it  it could be caused by bug in user switching or the VGA driver itself.

Please let me know how did it work for you folks!
Cheers!

---

### Post by cadamr on 2007-06-25
SUCCESS!!! :o:o:o

I was having the same problem. I would log in, gnome would start, freeze, and return to the login prompt. The second login was usually successful.

I used the restricted drivers manager ( System >> Administration ) to uninstall and reinstall my nvidia driver. I rebooted after the uninstall and reinstall, but I'm not sure if that's necessary. This fixed it!!! WARNING: this overwrites your xorg.conf file. If you have customized it, make a backup! (I learned this the hard way :(  )

"sudo apt-get install --reinstall nvidia-glx" might do the same thing. You may have to run "nvidia-xconfig" afterwards???

---

### Post by cadamr on 2007-06-26
!!!?!?!?!?!!?!!?:(:(:(

Nevermind, that didn't fix it after all. It only worked one or two times, and went back to having to login twice. I'll try visionary's method.

---

### Post by Gleep on 2007-06-27
I'm getting sick to death of all the bugs at the moment... Logging in not twice, but sometimes up to 7 times with restarts in between, then when i finally log in, things like kopete not appearing in the panel up the top, which I kinda find useful... on top of that I can't get on some websites all of a sudden, but I can on windows...

I'm gonna try the fix above, if that doesn't work, it's time for a reinstall. *Mad* :(

---

### Post by Gleep on 2007-06-27
Having done that, my screen res is now absolutely ******. I reconfigured again, and it's still buggered. ARGH >_<

---

### Post by Ptero-4 on 2007-08-19
What are your computer specs? It might be one of those computers designed to be incompatible with linux.

---

### Post by gurth4ng on 2008-05-02
I am having the same problem after upgrading from 7.10 to 8.04.

every time i boot up my computer i have to login twice.

I've read about this problem being reported on the net for diferent versions of Ubuntu, so my guess something is messing up the login proccess during the upgrade?

which file is responsible for what happens during (after) the user login? maybe the answer is there..

---

### Post by flarkit on 2008-05-08
Same as gurth4ng - after upgrading from 7.10 to 8.04, I also find myself having to log in twice. I'm using the latest NV driver (169.12) and other than this frustrating glitch, I'm very happy with the upgrade.

---

### Post by phibuntu on 2008-05-20
Same thing for me.
But only when I log in in my (admin) user account. When my son or wife log in, there is no problem.
The problem must be somewhere in my configs (/home/).

As others, I have the problem since upgrading to 8.04.

---

### Post by phibuntu on 2008-05-20
... workaround ...
 

I removed the directory "/home/myself/.local" (by moving it to a temporay place).

After login, the directory was newly created, but it worked once.
THIS IS NOT A SOLUTION. Everything in your ".local" directory has to be reconfigured.

After second reboot, I have to login twice as ever.
But this tipp is a probably a hint to find the error...

... keep going.

By the way: Does anyone know, what this ".local" directory is for?

---

### Post by phibuntu on 2008-05-20
> **phibuntu said:**
> ... workaround ...
 

I removed the directory "/home/myself/.local" (by moving it to a temporay place).

After login, the directory was newly created, but it worked once.
THIS IS NOT A SOLUTION. Everything in your ".local" directory has to be reconfigured.

After second reboot, I have to login twice as ever.
But this tipp is a probably a hint to find the error...

... keep going.

By the way: Does anyone know, what this ".local" directory is for?


Sorry, did not help. it must be something else...

---

### Post by treggmo on 2008-05-21
I was having the same problem but only after changing the login screen at System > Administration > Login Window and clicking the Local tab at the top. I selected the "Happy Gnome" screen aand rebooted to try it. What I hadn't done is to click in the box to the left of the selection and the change wouldn't stick. I discovered later that I must click in the box to select my choice and then the change stuck. However, the initial setting was not automatically deselected so I had two selections made for the login window. This is to the best of my memory but I believe that is when the "login twice" issue started. I do know that I logged in many times successfully before I changed the the settings. I reset the screen to the default screen and deselected all others and it it logs in properly.

I am running 8.04 after a clean install from 7.10.

---

### Post by phibuntu on 2008-05-22
> **treggmo said:**
> I was having the same problem but only after changing the login screen at System > Administration > Login Window and clicking the Local tab at the top. I selected the "Happy Gnome" screen aand rebooted to try it. What I hadn't done is to click in the box to the left of the selection and the change wouldn't stick. I discovered later that I must click in the box to select my choice and then the change stuck. However, the initial setting was not automatically deselected so I had two selections made for the login window. This is to the best of my memory but I believe that is when the "login twice" issue started. I do know that I logged in many times successfully before I changed the the settings. I reset the screen to the default screen and deselected all others and it it logs in properly.



Similar problem for me. I changed the login session back to "gnome" instead of "use previous" and everything works fine now.
This also explains, why my wife and my son never had this problem on the same machine ;-D

I installed ubuntu 6, upgraded to 7 and now upgraded to 8.04.

---

### Post by staticsage on 2008-05-24
This just started happening for me as well. Fresh install of 8.04.

---

### Post by vprasaj on 2008-05-24
I have changed GDM to happy gnome and make session gnome default and it worked.
Maby you just have to change session to gnome and make it default like phibuntu said. (Post #20)

\\:D/

---

### Post by Bott on 2008-05-24
I've encountered this login twice issue with 8.04 for two days and have no idea why it started.

I did a reinstallation of GDM in Synaptic Package Manager and the problem seems to have gone way.

If only I could get rid of that Ubuntu main menu icon so easily...

---

### Post by staticsage on 2008-05-24
I changed my session on the login screen from Last Session to Gnome as phibuntu suggested, and the problem has disappeared.

---

### Post by j0shdt on 2008-06-18
Yup, me too. I changed the theme to "happy Gnome" without deselecting the default one. Gonna give it a try after rebooting.

---

