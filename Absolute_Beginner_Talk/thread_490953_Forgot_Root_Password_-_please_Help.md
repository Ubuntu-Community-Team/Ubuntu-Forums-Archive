---
title: "Forgot Root Password - please Help"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Stanislaw on 2007-07-03
I`ve just started to use Ubuntu Feisty Fawn 7.04 i386 (desktop)  few days ago, and already made a serious, stupid error! 
I didn`t know, that actually there is no root account in Ubuntu, so I wanted to make difference beetween me as a user and me as  administartor, so I changed  the password for root in System - Administartion - Users, Groups, and also denied administartive rights to me as a user (to the first and only user created during the installation)! I am pretty sure that I remembered the password for the "root" user, but unfortunatly the Ubuntu doesn`t mean so :p! Now half of the System - Administartion menu is for me invisible, and I can`t do anything administartive! So far I`ve tried many things, including the one from this forum to chanhge and REMEMBER the password for root, but all of them failed

1. I have booted brom live disk, mounted a disk, but when I came to the chroot part it just notify me that:
**"That action is not permitted" ** I`ve mounted the disk in directory /media/recovery and issued a command
**chroot /media/recovery /bin/bash**, but I couldn`t do anything

2. I`ve booted from Grub in single user mode by witing in appropriate field "single init=/bin/bash
The Grub throw a prompt that looks something like this
**root@none**,... than I`ve tried to rewrite the root passwd by issuing command **passwd**, but it failed because** "The token ring is locked"** or something like that, I find on the net a solution for that also (**Ive just had to make disk readable/ writeable with command mount -o remount,rw /** , It acctualy allowed me to change password, but has accepted only one character, i.e as soon as I type the first character for the new password it asked me to retype the password, and on the end notified me that a **password is changed succesfully**, aha, yeah :)  I`ve tried to use that new single character password in Ubuntu but it failed!


So if anyone has a solution to this problem of mine please help! And yeah, I`am apsolute beginner in Linux/Ubuntu so suppose I do not know nothing, so please explain me the solution in detail i.e what exactly should I type/clck and where!

Thanks!

---

### Post by meborc on 2007-07-03
you can gain the root privileges when booting into the recovery mode (second line in grub)

now you should be able to change the root password again...

---

### Post by seetho on 2007-07-03
You are better off just backing up your important data then do a reinstall.  It'll be faster than trying all that stuff you described.

Learn from the experience and carry on.  I've done many reinstalls in my early Ubuntu days.

---

### Post by cogadh on 2007-07-03
Why re-install when you can follow meborc's advice and just use the "passwd" command to change the password? It doesn't make any sense to toss out a perfectly functional system just because a password was lost. That's giving up way too easily and honestly, a reinstall is much harder to do than a password change, even with Ubuntu's easy-as-pie install.

---

### Post by seetho on 2007-07-03
You are right.  It escaped me that you can go into recovery mode to change the password.  Then again it does not hurt to do reinstall a few time just to get things working just the way you want.  Like you say: easy as pie!

---

### Post by Stanislaw on 2007-07-03
I`ve succeded, YEAH!

The whole problem was in the fact that I denied administartive rights to the user created during the install. Effectivly I denied myself administartive rights! So when the system prompts me for the password it prompts me for the password of the currently loged user, (which must have administartive rights) ! But as I deny myself administartive rights it does not accept it! This colud be dealed with faster if I colud log in as a root in GNOME, so than I could just allow me back my administartive rights! I noticed that there is that possibility, but I`ll couldn`t do it because I didn`t have administrative rights!. Anyway the solution is this!

1. When the GRUB propmts you for the options highlight the option Ubuntu.... (recovery)
2. press e
2. Higlight the option beggining with kernel.... 
3. press e
4. append to the end (after single) **init=/bin/bash**. there must be an empty space between single and this
5. then after a few secconds a system throws something like this
root@none...
6. type **mount -o remount,rw / ** this allow read write permissions for disk
7 type **passwd**
8. Type new password
9.Retype the new password
10.Reset
11. In the GRUB just choose Ubuntu ....(recovery)
12 type your **new**  **root password**
13. From now on you can deal with the acounts  as a root from console, In my case I just had to type **adduser stanislav admin**  thus restoring my administartive rights!
14. Reset.
15. Enjoy :D

@meborc - Thank you very much

@seetho - This way of reinstalling , and so, is just the way of following the way of lesser resistance!  No good ever comes from that! Anyway thank you for your post! At least you are not lazy to write your opinion!

---

### Post by seetho on 2007-07-03
> **Stanislaw said:**
> 
@seetho - This way of reinstalling , and so, is just the way of following the way of lesser resistance!  No good ever comes from that! Anyway thank you for your post! At least you are not lazy to write your opinion!

I'm glad you managed to fix your problem.  Sometimes when you have a gazillion other things to do, the only choice is to go the way of least resistance, but you are right - you learn the most when you actually take the time to try to fix problems.  I wish I had that luxury - unfortunately not always.

---

### Post by meborc on 2007-07-03
> **Stanislaw said:**
> I`ve succeded, YEAH!

The whole problem was in the fact that I denied administartive rights to the user created during the install. Effectivly I denied myself administartive rights! So when the system prompts me for the password it prompts me for the password of the currently loged user, (which must have administartive rights) ! But as I deny myself administartive rights it does not accept it! This colud be dealed with faster if I colud log in as a root in GNOME, so than I could just allow me back my administartive rights! I noticed that there is that possibility, but I`ll couldn`t do it because I didn`t have administrative rights!. Anyway the solution is this!

1. When the GRUB propmts you for the options highlight the option Ubuntu.... (recovery)
2. press e
2. Higlight the option beggining with kernel.... 
3. press e
4. append to the end (after single) **init=/bin/bash**. there must be an empty space between single and this
5. then after a few secconds a system throws something like this
root@none...
6. type **mount -o remount,rw / ** this allow read write permissions for disk
7 type **passwd**
8. Type new password
9.Retype the new password
10.Reset
11. In the GRUB just choose Ubuntu ....(recovery)
12 type your **new**  **root password**
13. From now on you can deal with the acounts  as a root from console, In my case I just had to type **adduser stanislav admin**  thus restoring my administartive rights!
14. Reset.
15. Enjoy :D

@meborc - Thank you very much

@seetho - This way of reinstalling , and so, is just the way of following the way of lesser resistance!  No good ever comes from that! Anyway thank you for your post! At least you are not lazy to write your opinion!

you rock... good luck with learning linux way... although it seems that you really don't need luck ;)

---

### Post by bodhi.zazen on 2007-07-03
> **Stanislaw said:**
> @seetho - This way of reinstalling , and so, is just the way of following the way of lesser resistance!  No good ever comes from that! Anyway thank you for your post! At least you are not lazy to write your opinion!

Yea, that is a way of setting the root password.

You *could* have just :

1. Boot to recovery mode. This will boot you to a command line interface, logged in as root, no password required. To start x just enter either *startx* or */etc/init.d/gdm start*

2. But, you do not need to run X.
```
nano /etc/group
```
Add you user name, comma delineated, to the end of " admin:x:117:" reboot, viola

3. I mention this because, although there is nothing wrong with setting a root password per se, it is considered by some to be a security risk and in not necessary to fix your system ;)

4. To remove (lock) the root account after setting a password :

```
sudo passwd -l
```

---

### Post by Stanislaw on 2007-07-03
> **bodhi.zazen said:**
> Yea, that is a way of setting the root password.

You *could* have just :

1. Boot to recovery mode. This will boot you to a command line interface, logged in as root, no password required. To start x just enter either *startx* or */etc/init.d/gdm start*

2. But, you do not need to run X.
```
nano /etc/group
```
Add you user name, comma delineated, to the end of " admin:x:117:" reboot, viola

3. I mention this because, although there is nothing wrong with setting a root password per se, it is considered by some to be a security risk and in not necessary to fix your system ;)

4. To remove (lock) the root account after setting a password :

```
sudo passwd -l
```


Acctually it did ask me about "root password required for maintance"! Said something like enter root password for maintanance or press CTRL - D to continue! And it logged me as a root only when I typed the root password, which I previously seted in manner described above! Cause in that time I didn`t know what my root password! But if I`ve press CTRL - D, it would load GNOME and all other stuff, but not as a root, so again I didn`t have administartive rights

Maybe it is a new security feature in Feisty Fawn 7.04! I don`t know! Anyway the root password is obligatory if you want to be logged as a root in recovery mod, well at least on my computer! So virtaly you have to hack in, with little editing in Grub,

---

