---
title: "Terminal Issue (Blank White Screen)"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by Artimusp on 2007-07-20
Ok, so I am brand new to using Ubuntu so far I like what i see but, today i was messing around just to get a better feel of how it all works. I was following a link on how to get flash working went to terminal to past the instal/link eh? when i opened terminal all that came up was a blank white screen. I'm sure it's probably something real easy to fix but like i said I'm literally retarded as far as any of this stuff goes, trying to learn but can't seem to get this fixed. Any help would be greatly appreciated. Thanks

---

### Post by asmoore82 on 2007-07-20
there was no text in the upper left corner of the Terminal??

---

### Post by Artimusp on 2007-07-20
none, not even a cursor.

---

### Post by asmoore82 on 2007-07-20
drop down to the real terminal: press [ctrl]+[alt]+[F1]

login with your username and passwd and post the output of
```
~$ mount
```

... press [alt]+[F7] to return to gui

---

### Post by alienexplorers on 2007-07-20
Try running ALT-F2 and run Root Terminal

---

### Post by Artimusp on 2007-07-20
ok so i did CTRL+ALT+ F1

/dev/hda2 on / type ext3 (rw,errors=remount-ro
proc on /proc typr proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs(rw,noexec,nosuid,nodev,mode=0755
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777
procbususb on/proc/bus/usb tybe usbfs (rw)
undev on /dev type tmpfs (rm,mode=0755)
devshm on /dev/shm type tm pfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620
irm on /lib/modules/ 2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc(rw)

thats what is said to the best of my abilities as i do not know how to copy/paste from within that screen
also Alt+f7 exited out but not back to the GUI it was only a black screen. I had to do a hard restart to get it going again.

what does run in terminal mean? I hit alt+f2 and choose that but nothing.

Thanks for your time and help, I appreciate it.

---

### Post by Artimusp on 2007-07-21
hmm. So i disabled desktop effects and disabled the unregistered driver for my nvidia card "7900 gs"
I did this because it was a suggestion i found on another forum. "Loading bullet in gun" So now when i start it up after i log in the thing entire desktop is white. "placing gun to temple" ARGGG. what the hell have i done? How do I just reinstall over the same partition. I figure it would probably just be easier to start fresh from this point. I wasn't that far into it to loose anything of value. I have it set up dual boot with vista/Ubuntu. vista takes up the largest part of my hard drive but i set aside 20gigs for Ubuntu. when i start my computer though it will automatically boot into ubunto if i do not choose vista from the list. is there a safe way to reinstall without accidentally deleting vista as that would be a nightmare because it has business stuff family photos and the like.
I really want to learn this stuff but it is proving to be rather frustrating.

---

### Post by meierfra on 2007-07-21
I don't think you need to reinstall (although  that is no more  difficult than  the original installation)
Let's try to get the gui back. Boot into safe mode ( press esc  during boot up to get to the grub boot menu). 
In the terminal type:

 ```
  dpkg-reconfigure xserver-xorg 
```

follow the instruction and choose the default setting, unless you have a good reason not to.

Reboot via 

```
reboot 
```

and hopefully you get something better than a white screen.

---

### Post by Artimusp on 2007-07-21
Ok, followed your advice. answered all the questions and everything is running smooth. Thanks for all of your help! The open source community has been very helpful and understanding of my lack of experience with the whole thing. gonna try not to mess with too much for the time being till i can do some more reading on the whole thing. I've been a windows user since as long as i can remember so this is all Greek to me but I'm getting it slowly but surely. Again thanks alot guys!      Cheers!                             Artimus

---

### Post by Beavis&amp;Butthead on 2008-07-17
Hey, Are you running skype?
This seems like a retarded question but there might be something beheind it.
Skype uses popup messages but its written either for Debian (where ubuntu is based on).
Or Ubuntu 7.04+ (so ubuntu 7.04 and up).
This might cause this GUI problem.
Can you make a screenshot when this error occurs?
Maybe with a camera or just a normal printscreen if thats possible?
Does your terminal look like this: [http://www.2shared.com/file/3610904/f9851081/errortar.html](http://www.2shared.com/file/3610904/f9851081/errortar.html) ?
Then we might have the same problem.
I posted a Topic about it also, [http://ubuntuforums.org/showthread.php?t=862559](http://ubuntuforums.org/showthread.php?t=862559) .
So does it look like we have the same problem?


I'd like to add:
My latest findings are that skype was off when this bug happend again.
And over here, it happens randomly and not just to a terminal.
Now, Do you use pidgin or do you have an nvidia graphics card.
Maybe Nvidia's drivers are causing this trouble!

---

