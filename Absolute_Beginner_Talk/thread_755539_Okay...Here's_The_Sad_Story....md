---
title: "Okay...Here's The Sad Story..."
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by Chaco on 2008-04-14
Built a new system....Windoz Vista 64 bit would not install.  Called MS..they said something was wrong with the disk so send it back to the vendor..which I did.  In the meantime, I installed Ubuntu and got to crunching numbers for SETI (which is the purpose of the system).  Vendor sends back the disk and says there's nothing wrong with it but it will not begin installation from a reboot (or any other way I know of).  So I thought I'd try it from within Ubuntu....guess what?  I cannot remember my username or password (it's been sitting here running quietly and very slowly for over a month).  So I'm stuck. I don't know how to recover my username or password so I can at least get back into Ubuntu and it sets there disapprovingly and patiently waiting for me to enter my username and password.  I know, I know I shoulda written them down but I didn't .  I'd like to format the disk and start all over again but I don't know how to do that with the system in the state it's in...waiting for me to enter a username and password I no longer have.  Any suggestions (other than jumping off a bridge or using the monitor for a flower pot)?  Thanks for your kind understanding..I'm sure someone else has been here before...stomping around in the dirt, whistling and hoping it will all turn out for the better.

---

### Post by estaticd on 2008-04-14
Good stuff man.  Happens to everyone eventually.  Sorry to hear about this.

[http://ubuntuforums.org/showthread.php?t=273531](http://ubuntuforums.org/showthread.php?t=273531)

Should fix you up.  :)

---

### Post by Rhubarb on 2008-04-14
Or this way:
[https://answers.launchpad.net/ubuntu/+question/11873](https://answers.launchpad.net/ubuntu/+question/11873)
(Which would be a lot easier).

If you know your username, in recovery mode type in:
```
passwd username
```

---

### Post by spiderbatdad on 2008-04-14
Put in the live cd.
Boot into recovery
In the terminal enter: your_username passwd -d
That will delete the password.
Then enter your_username passwd
You will be asked to create a password.

Hope that's right. Been a while since I had to do that.

---

### Post by Chaco on 2008-04-14
Nope..don't know my user name, don't know my password, don't know diddly....I tried the recovery mode method but all it would allow me to do is put in another password unknown to me to do maintenance or to type control D to continue which, of course, takes me right back to the sign on screen....hmmmm  lost...oh so lost....!

---

### Post by Chaco on 2008-04-14
Don't have the live cd in addition to not having the username, password or diddly.  Downloaded Ubuntu from the net.

---

### Post by spiderbatdad on 2008-04-15
From the command prompt in recovery mode run ```
cat /etc/passwd
```

you will get an output like this:```
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:100:101::/nonexistent:/bin/false
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
messagebus:x:103:109::/var/run/dbus:/bin/false
hplip:x:104:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:105:112:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:106:113:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
polkituser:x:107:115:PolicyKit,,,:/var/run/PolicyKit:/bin/false
haldaemon:x:108:116:Hardware abstraction layer,,,:/home/haldaemon:/bin/false
gdm:x:109:118:Gnome Display Manager:/var/lib/gdm:/bin/false
pulse:x:110:119:PulseAudio daemon,,,:/var/run/pulse:/bin/false
**linux:x:1000:1000:private,,,:/home/linux:/bin/bash**
libuuid:x:111:125::/var/lib/libuuid:/bin/sh
sshd:x:112:65534::/var/run/sshd:/usr/sbin/nologin
Debian-exim:x:113:126::/var/spool/exim4:/bin/false
linux@linux-laptop:~$ 

```

Scroll all the way down till you see "somename:x:1000:1000:somename,,,/home/somename.....

In my case it starts with linux. My username is linux.

---

### Post by tagra123 on 2008-04-15
Reboot the computer

Press ESC at the grub prompt and select recovery

Press e for edit.

Goto the kernel line and then press e

Go to the very end of the line, add rw init=/bin/bash

Press enter and the b to boot into bash

You will be in a root shell -- BE CAREFUL

Type in passwd YourUserName. 

Enter your new password

Type reboot and press enter.

Your password has been reset.

---

### Post by Chaco on 2008-04-15
In recovery mode I get Give root password for maintenance (or type Control-D to continue):  When I try to type there are no letters appearing...just nothing visible happening there at all...what to do....what to do....Oh, and thanks everyone for the quick replies.  It is very much appreciated.

---

### Post by Chaco on 2008-04-15
Okay....This is Emelia Airhardt somewhere over the Pacific...lost...navigator is drunk...clouds on the horizon...low on fuel...it's time to fire up the Enola Gay and nuke this system....anyway to do that?.....reformat or a small, cleverly placed grenade perhaps, a gentle tweak with a 440v line to the motherboard?  Going down....sea surface getting closer....Okay....that's a little dramatic but really....can't I just wipe the slate clean and start again, renewed, reborn and running again?

---

### Post by tagra123 on 2008-04-15
Try post 8 first

---

### Post by spiderbatdad on 2008-04-15
> **tagra123 said:**
> Try post 8 first

Did you read the post where he says he doesn't know his user name?

Unfortunately it appears this account has enabled a root password, as well as a user password. I don't think you can recover without a CD.

---

### Post by tagra123 on 2008-04-15
> **spiderbatdad said:**
> Did you read the post where he says he doesn't know his user name?

Unfortunately it appears this account has enabled a root password, as well as a user password. I don't think you can recover without a CD.


Yes I did read it.

You do not need a pasword to use this method -- I've used it before -- no password necessary.


The line passwd oldusername or newusername

asks for a new password. 

You will not be prompted for a password.

The line should look something like this in grub

kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdc1 rw init=/bin/bash



Here's some other ways to reset root if the method in post 8 is giving you difficulty.

[http://wiki.clug.org.za/wiki/How_do_I_reset_my_root_password%3F](http://wiki.clug.org.za/wiki/How_do_I_reset_my_root_password%3F)

---

