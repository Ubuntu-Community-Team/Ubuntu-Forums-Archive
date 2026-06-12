---
title: "[SOLVED] sudo ___: command not found"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by KriSoft on 2008-02-24
After many year of hesitation I finally installed Linux on my computer.  As I'm no computer wizard I went for a dual boot UBUNTU 7.1, XP installation.
All works fine and I manage to install many software alternatives to the software I'm used to work on under windows but faced many problems installing **RealPlayer**.
Like some other programs I had to install **RealPlayer** in the terminal bit as many I use these commands without really understanding yet what they exactly do.

**THE PROBLEM**
   REM [installing real player]
kristof@KB:~$ sudo RealPlayer*bin
[sudo] password for kristof:
sudo: RealPlayer10GOLD.bin: **command not found**

I have done some of the things that were recommended in discussion forums but non of them where successful.
**WHAT I HAVE DONE**
rebooting UBUNTU in recovery mode and at the prompt reinstall SUDO with follow command.

kristof@KB:~$ aptitude install sudo

The fist time something went wrong and had to used <Ctrl><Alt><Del> to continue but rebooting in recovery mode and using the above command again all went well apart that when using sudo in terminal the problem persist.

Here is  some info that might be of use to diagnose the problem.
**ADDITIONAL INFO**
kristof@KB:~$ dir
Desktop    dwhelper  file:          Music     Public                Templates
Documents  Examples  Illustrations  Pictures  RealPlayer10GOLD.bin  Videos

kristof@KB:~$ id
uid=1000(kristof) gid=1000(kristof) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),1000(kristof)

kristof@KB:~$ ls $path
Desktop    dwhelper  file:          Music     Public                Templates
Documents  Examples  Illustrations  Pictures  RealPlayer10GOLD.bin  Videos

kristof@KB:~$ which sudo
/usr/bin/sudo

kristof@KB:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Thanks for anybody that is willing to help me inm my steep learning curve
Any help is much appreciated
Kristof

---

### Post by wireddad on 2008-02-24
Have you seen this:  [http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
I think this will explain further.

---

### Post by asmoore82 on 2008-02-24
(Realplayer, EWW!!)

The script is probably not executable, which is to say that the permissions are incorrect.
you could either make the script executable, or run a BASH shell and give it the name of the script to run.
```
chmod +x RealPlayer*.bin
sudo RealPlayer*.bin
```
--OR(better, IMO)--
```
sudo bash RealPlayer*.bin
```

---

### Post by sisco311 on 2008-02-24
try:```
sudo ./RealPlayer*.bin
```you need to enter the full path to your command.
.(period) = current directory

---

### Post by Duck2006 on 2008-02-24
This may help

[http://www.ubuntux.org/how-to-install-the-realplayer-multimedia-player](http://www.ubuntux.org/how-to-install-the-realplayer-multimedia-player)

---

### Post by KriSoft on 2008-02-24
> **sisco311 said:**
> try:```
sudo ./RealPlayer*.bin
```you need to enter the full path to your command.
.(period) = current directory

Thanks for this;

I Used 
kristof@KB:~$ chmod +x RealPlayer*.bin
kristof@KB:~$ sudo ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I found it odd that that the full path made a difference but not sure what to do with the answer.  What next?

Kind regards
Kristof

---

### Post by sumguy231 on 2008-02-24
You just need to install the libstdc++5 package through Synaptic or Aptitude:
```
sudo aptitude install libstdc++5
```

---

### Post by KriSoft on 2008-02-24
> **Duck2006 said:**
> This may help

[http://www.ubuntux.org/how-to-install-the-realplayer-multimedia-player](http://www.ubuntux.org/how-to-install-the-realplayer-multimedia-player)


Found a useful command **sudo apt-get install realplayer**
but was unable to install a repository that contained real player.

So learned a alot but did not get RealPlayer working yet

---

### Post by bodhi.zazen on 2008-02-24
Try enabling your repositories : [Enable Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by KriSoft on 2008-02-24
> **sumguy231 said:**
> You just need to install the libstdc++5 package through Synaptic or Aptitude:
```
sudo aptitude install libstdc++5
```

It worked, have to go to the hospital because my wife just went to early into labour.

Wish us luck
All the best
K.

---

### Post by sumguy231 on 2008-02-24
> **KriSoft said:**
> It worked, have to go to the hospital because my wife just went to early into labour.

Wish us luck
All the best
K.

Good luck! :)

---

### Post by KriSoft on 2008-02-27
> **sumguy231 said:**
> Good luck! :)

Thanks,
We have a beautiful daughter "Elona"

All the best

---

### Post by KriSoft on 2008-02-27
> **bodhi.zazen said:**
> Try enabling your repositories : [Enable Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu)

I tried editing the file directly or by using the Package Manager but was not successful in this case.  It's a useful link for future.

Thanks
K.

---

### Post by wireddad on 2008-02-27
Congratulations!

---

