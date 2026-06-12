---
title: "Auto logon"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by pacogozalez on 2006-04-19
I did use ubuntu on my garage-PC for a while. This worked ok for reading emails and surfing the web. Negative was the long boot time, and to have to enter the password at each startup. After a month of inactivity, i did forget the password. 
I have installed windows again since it wont ask me for a password.

My kids do use a win2k PC for surfing. This PC is spyware-adware, etc infested since they will click every link they see.
Linux would be a better choice here, but 2 of the kids cant read, and wont be able to type any password. 

Now the questions:

How can i "auto-logon" ubuntu ?
It is a single user, NAT protected PC used for web-surfing. 

How can i speed-up boot? It's pure nonsense to wait 20 sec for the clock-sync on every start, isnt it?

How can i install ubuntu in parallel with win2k, using the windows boot-manager? (Grub works fine, have done that, but prefer win-bootmanager).

---

### Post by htinn on 2006-04-19
If you go to the System/Administration menu (in GNOME), there should be a Login Window Preference application. There you can set up a user to be automatically logged in.

Why do you prefer Windos bootmanager?

---

### Post by akudewan on 2006-04-19
Check out this link to speed up boot: [http://ubuntuforums.org/showthread.php?t=80423&highlight=howto+boot+speed](http://ubuntuforums.org/showthread.php?t=80423&highlight=howto+boot+speed)

I don't know if you can bypass the password, but maybe you can keep a username and password like "zzz" or something, which even someone who can't read can grasp.

---

### Post by dickohead on 2006-04-19
Speeding up the boot could be one of a million things, but mostly try upgrading the pc?

For the autologin, under the System -Administration - Login Screen Setup
You can specify a user that can be automatically logged in.

For the windows boot manager, you can't(afaik), because it's badly written, try Lilo or some other boot managers if you're daring.

And for the clock synching, just turn that service off using a boot loader editor: ie: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by pacogozalez on 2006-04-19
>there should be a Login Window Preference application. 

GREAT!  Thanks.

>Why do you prefer Windos bootmanager?

I do know how-to edit win-boot.ini, but not grub.

There is only a very limited amount of new things that fit into my short term memory.  I will try to avoid learning grub and give "general ubuntu" things the preference.

---

### Post by dickohead on 2006-04-19
sudo vi /boot/grub/menu.lst

---

### Post by htinn on 2006-04-19
Grub and menu.lst are easy.

Just do something like this:

```
default=0
timeout=9
splashimage=(hd0,2)/boot/grub/splash2.xpm.gz

# Ubuntu

title           Ubuntu (2.6.15-20-k7)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-20-k7 root=/dev/hdd1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-20-k7
savedefault
boot

# Fedora Core

title Fedora Core (2.6.16-1.2080)
        root (hd0,2)
        kernel /boot/vmlinuz-2.6.16-1.2080_FC5 ro root=LABEL=/1 rhgb quiet
        initrd /boot/initrd-2.6.16-1.2080_FC5.img

# separator

title -----------------------------
root

# Memory test

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot
```

Nothing to it. :)

---

