---
title: "Major Problems! Can't Login Under Any Users......"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by ebozzz on 2006-12-14
Alright. When I left home this morning all was well. I return this even and it will not allow me to login. When I enter my user ID and password, I just get bounced back to the login prompt again. This occurs with every user on this box. What's the deal? Is there anyway to correct this? I have a few files saved on my desktop that I would like to save but nothing else critical. Any ideas would be **greatly** appreciated. Thanks!

---

### Post by taurus on 2006-12-14
Boot into recovery mode from GRUB menu and change the password for your login name, assuming it's **ebozzz**...

```
passwd **ebozzz**
```

---

### Post by ebozzz on 2006-12-14
> **taurus said:**
> Boot into recovery mode from GRUB menu and change the password for your login name, assuming it's **ebozzz**...

```
passwd **ebozzz**
```

Hi ya Taurus,

Thanks for the reply. That's not the user ID but I will give what you suggested a try. I am using the live disc at the moment. I think what I will do is login on another PC to follow the thread as suggestions are added.

---

### Post by taurus on 2006-12-14
Just replace that with whatever username that you use to log in.  I only used that as an example so if there is no **ebozzz** on your machine, don't use that name or you will get an error message...

---

### Post by ebozzz on 2006-12-14
> **taurus said:**
> Just replace that with whatever username that you use to log in.  I only used that as an example so if there is no **ebozzz** on your machine, don't use that name or you will get an error message...

I'm, clear on that. The password is already changed and I have rebooted. Trying now.

---

### Post by ebozzz on 2006-12-14
Alright, I changed the password

> passwd userid

I got..

> add UNIX password 

or something that effect. I then added the password and retyped it to confirm it. It went back to the command prompt and I entered..

> reboot 

I then tried to login and got the same results. Let me try one more time...... The problem is the same.

---

### Post by ebozzz on 2006-12-14
More info:

I went back into the recovery mode and changed the password for all users, total of 4 including myself, on this machine. I can not login under either user.

---

### Post by malcolm1234 on 2006-12-15
> **ebozzz said:**
> Alright. When I left home this morning all was well. I return this even and it will not allow me to login. When I enter my user ID and password, I just get bounced back to the login prompt again. This occurs with every user on this box. What's the deal? Is there anyway to correct this? I have a few files saved on my desktop that I would like to save but nothing else critical. Any ideas would be **greatly** appreciated. Thanks!


I have the same/similar problem (see [here](http://www.ubuntuforums.org/showthread.php?p=1889223)). My system is still usable because I can log in if I just keep re-login back in a few times (I have a timed login of a couple of seconds set up). It's a pain though and adds to the already quite long boot times I get in Edgy. I think I'll probably revert to Dapper.

M

---

### Post by ebozzz on 2006-12-15
> **malcolm1234 said:**
> I have the same/similar problem (see [here](http://www.ubuntuforums.org/showthread.php?p=1889223)). My system is still usable because I can log in if I just keep re-login back in a few times (I have a timed login of a couple of seconds set up). It's a pain though and adds to the already quite long boot times I get in Edgy. I think I'll probably revert to Dapper.

M

Thanks for the reply and the additional information. I hate the fact that others have experienced similar problems but I'm glad that I am not alone. I was beginning to think that I had a *dark cloud* hovering above me. :) I do wish that I had waited a little longer to see if there were any additional suggestions. There were some things to be learned from the issue. As it is, I reinstalled Edgy and everything is back up for now. With multiple users in the house, any down time can be hectic even though more than one PC is available for use.. Nothing critical was lost. It was just an inconvenience.

---

### Post by RistoE on 2006-12-16
You are not alone with this log in problem. I can't log in. Log in screen comes again and again. I'm using correct user id and password no question about that.

The problem started after I installed the recommended updates (all). These updates were max one week old. The computer is T-30 with mobile ati radeon 7500 and 512 ram and 2GHz cpu. Running Edgy.

My desktop computer runs on Edgy as well. Seems that I should wait before installing any further updates? :neutral:

EDIT: It is not impossible that my HD is full. Will check if that is the case.
EDIT2: GDM could not write. This probably means my hd is full. Have to look if it is safe to resize the partion.

EDIT3: SOLVED. HD was full and I deleted some old RAR files. Now able to login normally again!
I still have think how to add some space? Another partion for /HOME or resize the linux partion? This is not urgent however... :-)

---

### Post by ebozzz on 2006-12-16
> **RistoE said:**
> You are not alone with this log in problem. I can't log in. Log in screen comes again and again. I'm using correct user id and password no question about that.

The problem started after I installed the recommended updates (all). These updates were max one week old. The computer is T-30 with mobile ati radeon 7500 and 512 ram and 2GHz cpu. Running Edgy.

My desktop computer runs on Edgy as well. Seems that I should wait before installing any further updates? :neutral:

EDIT: It is not impossible that my HD is full. Will check if that is the case.
EDIT2: GDM could not write. This probably means my hd is full. Have to look if it is safe to resize the partion.

EDIT3: SOLVED. HD was full and I deleted some old RAR files. Now able to login normally again!
I still have think how to add some space? Another partion for /HOME or resize the linux partion? This is not urgent however... :-)

Thanks for the reply. what capacity was your hard drive or the partition that you had designated for Ubuntu? I was using a 10GB partition and I am positive that I had not used anywhere near that amount of space. Would you be kind enough to document how you resolved your situation?

Edit: This what I get from running the *free* command.

>              total       used       free     shared    buffers     cached
Mem:        515688     472288      43400          0      63644     211416
-/+ buffers/cache:     197228     318460
Swap:       425680          0     425680

---

### Post by ebozzz on 2006-12-16
The is what I get currently from running the *df -H* command.

Filesystem             Size   Used  Avail Use% Mounted on
/dev/hdc2              9.3G   3.0G   5.9G  34% /
varrun                 265M    91k   264M   1% /var/run
varlock                265M      0   265M   0% /var/lock
procbususb              11M    87k    11M   1% /proc/bus/usb
udev                    11M    87k    11M   1% /dev
devshm                 265M      0   265M   0% /dev/shm
lrm                    265M    19M   247M   7% /lib/modules/2.6.17-10-generic/volatile
/dev/hdc1               11G   3.2G   7.6G  30% /media/hdc1

I don't know of any reason that would have caused my previous install to look significantly different. Therefore, I am still confused as to why this occurred. :-?

---

### Post by ebozzz on 2006-12-16
If I run the *df* command, I get the following.

> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdc2              9029120   2836252   5734216  34% /
varrun                  257844        88    257756   1% /var/run
varlock                 257844         0    257844   0% /var/lock
procbususb               10240        84     10156   1% /proc/bus/usb
udev                     10240        84     10156   1% /dev
devshm                  257844         0    257844   0% /dev/shm
[COLOR="Blue"]lrm                     257844     17580    240264   7% /lib/modules/2.6.17-10-generic/volatile[/COLOR]
/dev/hdc1             10487300   3117352   7369948  30% /media/hdc1


What is the line highlighted in blue?

---

### Post by RistoE on 2006-12-16
what i did was simply
- press Esc when grub starts
- choose recovery mode
- ubuntu loads (without graphical interface)
- cd ..
- cd home
- cd xxxxx (my userid)
- looked around (ls command) and on Desktop  (cd Desktop) there was some extrafiles, deleted those with rm namexxx.ext
- I gave reboot command and thats it

My HD size is 12 GB (an old hd I threw in) and the linux partion is only about 3GB. I was better with unix over 15 years ago. I'm ageing.

---

### Post by ebozzz on 2006-12-16
Just an FYI, you can also enter the recovery mode when GRUB displays your boot options. It should be the second one from the top unless you have edited your list. 

Thanks for sharing your resolution. It will be helpful if I ever run into the same problem again. I am still confused as to why it happened in my case. If I knew I could use some precautionary measures to prevent it from taking place.

---

