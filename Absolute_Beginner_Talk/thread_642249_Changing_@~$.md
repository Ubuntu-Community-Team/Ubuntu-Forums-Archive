---
title: "Changing *@*:~$"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by SonicChao on 2007-12-16
How do I change my command line prompt:

________@_______:~$  to something else?

---

### Post by aidanr on 2007-12-16
Open /home/username/.bashrc
and  change the line
PS1='.............'
to whatever you want

[http://www.linuxselfhelp.com/howtos/Bash-Prompt/Bash-Prompt-HOWTO-2.html](http://www.linuxselfhelp.com/howtos/Bash-Prompt/Bash-Prompt-HOWTO-2.html)

---

### Post by nikoPSK on 2007-12-16
It is the user name followed by the system name. In my case it is niko@home. The words before the @ sign you can change if you are a different user, or root. example right here:

```
niko@home:~$ sudo su
[sudo] password for niko:
root@home:/home/niko# exit
exit
niko@home:~$ 
```

There are two ways to change your computer name. Say I wanted mine to be niko@work if I had ubuntu at work (I wish....) I'd (and you too) would do this:

System -> Administration -> Network
Network settings
General Tab -> Host Settings -> Hostname: Specify the computer name
Then finish with all open applications (save them etc...)  

If you want to do it the other way you can do this:
```
gksudo gedit /etc/hostname
```
Mine shows up "home" but I could change it to "work"

Hope that helped!
Niko

---

