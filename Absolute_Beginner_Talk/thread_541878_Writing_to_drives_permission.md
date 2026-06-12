---
title: "Writing to drives permission"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Spacedementia87 on 2007-09-03
For some reason i can't write any files anywhere apart from my "user area" place.

It means i can't save files onto my other hdds where i store all my data and I can't move the .run file for my lastest gfx card drivers onto my root partition to be able to install it.

---

### Post by taurus on 2007-09-03
Use the sudo command if you need to write/move/copy something outside of your $HOME directory.

```
sudo cp filename destination
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Spacedementia87 on 2007-09-03
ahh ok cool, thought it might be that, but because i haven't managed to get my internet sorted on linux just wanted to check before rebooting and trying!

---

### Post by LongJuanFeng on 2007-09-04
umm. yeah, I have the SAME woes right now, and i tried the sudo command in terminal then I"m asked for a password, I entered the same password which I am the only user on this OS and it said I had the wrong password. Someone please help, I know ubuntu is really good, but I'm starting to doubt it and getting extremely frustrated reading all this faqs that aren't helping me to install flash player and aim for this OS. And I just had a few hours ago switched from windows xp. Some one please help. I am imploring you!!!!

---

### Post by hyper_ch on 2007-09-04
Where did you mount that other harddrive to?

---

### Post by ukripper on 2007-09-04
> **LongJuanFeng said:**
> umm. yeah, I have the SAME woes right now, and i tried the sudo command in terminal then I"m asked for a password, I entered the same password which I am the only user on this OS and it said I had the wrong password. Someone please help, I know ubuntu is really good, but I'm starting to doubt it and getting extremely frustrated reading all this faqs that aren't helping me to install flash player and aim for this OS. And I just had a few hours ago switched from windows xp. Some one please help. I am imploring you!!!!

Here is flash player howto link as below -
[http://www.howtoforge.com/native_linux_flash_player9_in_ubuntu](http://www.howtoforge.com/native_linux_flash_player9_in_ubuntu)

Alternatively,

 easy way to install flash player use automatix2 - [http://www.getautomatix.com/](http://www.getautomatix.com/)

You are putting wrong password. you need the root password which you have  setup initially during installing ubuntu.

---

### Post by LongJuanFeng on 2007-09-04
Thanks a MILLION!!!!

---

### Post by hyper_ch on 2007-09-04
automatix is not recommended to use.

---

### Post by ukripper on 2007-09-04
Let user decide if they want to use automatix or not I have given both options.

---

### Post by hyper_ch on 2007-09-04
I didn't say the shall not use it... only that it's not recommended ;) big difference ;)

And before making suggestions, you should rather also voice the concerns about those things... that will actually help users to make a decision.

---

### Post by LongJuanFeng on 2007-09-04
why is that? btw, I currently despise the 800x600 resolution. Is there anyway to make it higher? I tried going into screen resolution preferences and changing it but it doesn't get higher.

---

### Post by hyper_ch on 2007-09-04
You can have a read here:

[http://ubuntuforums.org/showthread.php?t=519872](http://ubuntuforums.org/showthread.php?t=519872)

that links to here:

[http://ubuntu-tutorials.com/2007/08/06/commentary-and-alternatives-to-automatix/](http://ubuntu-tutorials.com/2007/08/06/commentary-and-alternatives-to-automatix/)

which links to here:

[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

and as a short summary:
> 
Automatix exists to satisfy a genuine need, and further work should be
carried out to determine whether these user requirements can be
satisfied within the distribution as a whole. However, in its current
form Automatix is actively dangerous to systems - ranging from damage
to small items of user configuration, through removing user-installed
packages without adequate prompting or warning and up to the (small
but existing) potential to leave a system in an unbootable state.

The current design of Automatix precludes any reasonable way to fix
some of these problems. It is attempting to fulfil the role of a
high-level package manager without actually handling any sort of
dependency resolution itself.

A more reasonable method of integrating Automatix's functionality into
Ubuntu would be for the Automatix team to provide deb files to act as
installers for the software currently provided. These could then be
installed through the existing package manager interfaces. This would
solve many of the above problems while still providing the same level
of functionality.

In its current form Automatix is unsupportable, and a mechanism for
flagging bugs from machines with Automatix installed may provide a
valuable aid for determining whether issues are due to supported
distribution packages or third party software installers.


---

### Post by ukripper on 2007-09-04
> **hyper_ch said:**
> You can have a read here:

[http://ubuntuforums.org/showthread.php?t=519872](http://ubuntuforums.org/showthread.php?t=519872)

that links to here:

[http://ubuntu-tutorials.com/2007/08/06/commentary-and-alternatives-to-automatix/](http://ubuntu-tutorials.com/2007/08/06/commentary-and-alternatives-to-automatix/)

which links to here:

[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

and as a short summary:

If you install with automatix it is fine. Problem sometimes occur during removing packages which can be done through command line or synaptic.

---

### Post by LongJuanFeng on 2007-09-04
umm. I followed that "how to forge" guide exactly and the terminal is still giving me issues about...invalidity. I have the original file on my desktop btw. 


here's how I did; 


warpman00@00warpman00:~$ cd /home/warpman00/desktop
bash: cd: /home/warpman00/desktop: No such file or directory
warpman00@00warpman00:~$ cd/home/warpman00/Desktop
bash: cd/home/warpman00/Desktop: No such file or directory
warpman00@00warpman00:~$ /home/warpman00/Desktop
bash: /home/warpman00/Desktop: is a directory
warpman00@00warpman00:~$ tar xvfz install_flash_player_9_linux_tar.gz
tar: install_flash_player_9_linux_tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
warpman00@00warpman00:~$ tar install_flash_player_9_linux.tar.gz cd install_flash_player_9_linux/
tar: invalid option -- a
Try `tar --help' or `tar --usage' for more information.
warpman00@00warpman00:~$

---

### Post by taurus on 2007-09-04
```
cd      /home/warpman00/Desktop
tar xvfz install_flash_player_9_linux_tar.gz
cd install_flash_player_9_linux
```
Now, read the instruction in there to install those two files for flash.

---

