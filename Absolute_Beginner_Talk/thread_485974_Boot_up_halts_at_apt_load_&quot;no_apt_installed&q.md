---
title: "Boot up halts at apt load: &quot;no apt installed&quot;?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by tordan on 2007-06-27
So I upgraded to Feisty fawn and now when I reboot the computer it starts to load Ubuntu and then it defaults to the linux prompt after stating that apt is not installed. If I hit alt-ctrl-del it loads to Ubuntu but many of the setting are messed up. I have tried installing apt from both the prompt and synaptic package manager and it doesn't seem to stick. Every time I reboot it says it has not been installed and when I go back into synaptic it is still uninstalled.

Help. Please...

---

### Post by Seisen on 2007-06-27
Boot into recovery mode and put this in.

```
sudo apt-get -f install
sudo dpkg -reconfigure -a 
```

---

### Post by tordan on 2007-06-28
Here are the responses to the commands:
```
tordan@tordan-desktop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfile-scan-perl libwxgtk2.4-1 libsdl-gfx1.2-4 ttf-dustin cdda2wav libtagc0
  kdemultimedia-kio-plugins libsqlite0 libsgutils1 libgnutls12
  linux-headers-2.6.17-11-generic libkcddb1 libwavpack0 libmono-cairo2.0-cil
  ruby1.8 libphat0 ruby libsdl-ttf2.0-0 python-sip4 libsigc++-1.2-5c2
  libsamplerate0 libgtk2-gladexml-perl libtunepimp3 libifp4 libfluidsynth1
  libipoddevice0 liblo0 linux-headers-2.6.17-11 libruby1.8 ladcca2
  libid3-3.8.3c2a libnjb5
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

and...

```
tordan@tordan-desktop:~$ sudo dpkg -reconfigure -a
dpkg: conflicting actions -e (--control) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

```

From what I can tell, something didn't work, but I don't know what.

---

### Post by tordan on 2007-06-28
oops. I didn't catch the "boot into recovery mode" part. I'll try that again.

---

### Post by tordan on 2007-06-28
could not boot into recovery mode.
had to do ctrl-alt-del from prompt to get back into Ubuntu.
Help...What is next?

---

### Post by Seisen on 2007-06-28
How did you upgrade to feisty anyway?

---

### Post by tordan on 2007-06-28
I used the update manager.

---

### Post by Seisen on 2007-06-28
When it finished it didn't give you any errors at the end?

---

### Post by tordan on 2007-06-28
Not that I saw. My roomate rebooted when it was done and didn't say anything about any error messages either. However, I can't guarantee that.

---

### Post by darkrose on 2007-06-28
> **Seisen said:**
> Boot into recovery mode and put this in.
```

sudo dpkg -reconfigure -a 
```
shouldn't that be:
sudo dpkg-reconfigure -a

no space between dpkg and -reconfigure.

---

### Post by tordan on 2007-06-28
should I try it?

---

### Post by darkrose on 2007-06-28
yeah, it shouldfix things as intended, and won't return the previous error.

---

### Post by Seisen on 2007-06-28
> **darkrose said:**
> shouldn't that be:
sudo dpkg-reconfigure -a

no space between dpkg and -reconfigure.

I think you might be correct

---

### Post by tordan on 2007-06-29
I am in the process of going through the process. There are a lot of choices and a lot of processing going on. I'll post the result of our efforts when I finish.

---

### Post by tordan on 2007-06-29
Ok. It appears to have finished. Should I reboot now?

---

### Post by tordan on 2007-06-29
rebooted. same error and result. ctrl-alt-bksp to somehow get to login screen. Any other ideas?

---

### Post by tordan on 2007-06-29
anybody got any guesses or should I just give up and do a complete reinstall of Feisty?

---

### Post by xdarkxanarchyx on 2007-08-20
Have you tried booting from a livedisc and doing an fsck on all of your partitions?
And I'm also not sure about this but have you tried moving your home folder and starting fresh with that?
```
 mv /home/*yourusername* /home/*yourusername-normal*
```

---

