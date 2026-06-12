---
title: "upgrade supeneded in between, cannot get to  my desktop"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by mbhardwaj on 2008-02-11
Hi
I was updating ubuntu after installing it, but due to some reasons the updating (while it was installing and stuff) got interrupted and my laptop rebooted,
Now i can get till the log in portion , but if i choose gnome nothing happens, i get a blank blue screen ( reminds me of the blue screen of death! :P)
whereas when i failsafe mode everything works fine almost,
how can i find what went wrong and correct it.
any help would be highlly appreciated.
Thanks

---

### Post by ashokpappu on 2008-02-11
are u able to boot in diagnosis mode from grub option?

---

### Post by mbhardwaj on 2008-02-11
yeah  i am able to do that,
I am able to start everything in GNOME failsafe mode,
but in GNOME session, i get only a blank blue screen and a cursor,all this started happening after that interrupt while upgrading.
thanks

---

### Post by tj111 on 2008-02-11
The problem is probably with your xserver.  If you can get to a command line, run the following command (after a failed login into gnome).
```

dmesg | tail - n 20

```
That should output the last 20 errors on your system.  If you decide it is an x-server issue, the following command will reset your xorg.conf (x-server settings) to their default state.  
```

sudo dpkg reconfigure -phigh xserver-xorg

```
Once 8.04 comes out ina  few months most of these problems will hopefully be fixed permanently.

---

### Post by mbhardwaj on 2008-02-11
when i try and do 

> 
sudo dpkg reconfigure xserver-xorg

it gives me the following error,

> 
/usr/sbin/dpkg-reconfigure :xserver-xorg is broken or not fullu installed 

how do i solve this problem....

I also get and erros "failed to Initialize HAL" when i log in in fail safe mode as well..
thanks

---

### Post by hyper_ch on 2008-02-11
in safe mode:

```

apt-get dist-upgrade

```

---

### Post by PmDematagoda on 2008-02-11
You could also try:-
```
apt-get install -f
```
or
```
dpkg --configure -a
```
on Recovery Mode if the commands suggested by hyper_ch do not work.

---

### Post by hyper_ch on 2008-02-11
> **PmDematagoda said:**
> on Recovery Mode if the commands suggested by hyper_ch do not work.
If upgrade was interrupted, very likely my command does not work... should have thought of that before ;)

---

### Post by mbhardwaj on 2008-02-11
ok this is what i did 

now when i tried
> sudo apt-get install --reinstall xserver-xorg

i got 
> dpkg was interrupted , you must manually run 'dpkg--configure -a'

i did that, took about 15 odd minutes and i was up and running ubuntu properly again, only one problem
I do not know what this command did???? and now on my grub option i have 3 options like
ubuntu 2..... 
ubuntu 2....(recovery)
ubuntu2....
ubuntu2....(recovery)
ubuntu.....
ubuntu(recovery)

before executing this i just had two?

could you please tell me what i did with that command, that worked.....

Thanks a lot for all the help !!!!

but i guess i need just a bit more, now when i log in , the Network option does nto detect my wireless network adapter....
though it does list on the command lspci

---

### Post by hyper_ch on 2008-02-11
Is the number all the same? I guess it's not - it seems you have now 3 kernels installed.

---

### Post by mbhardwaj on 2008-02-11
yeah the number is not the same, 
does it matter i have 3 kernel s installed?
can i uninstall them...?

---

### Post by hyper_ch on 2008-02-11
I would keep at least 2 kernels ;)

the previous one - that you konw works well and the newest one... so if the newest one has issues, you can still boot into the older one... so I'd unistall the oldest of those three.

---

