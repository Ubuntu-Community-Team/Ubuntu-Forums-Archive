---
title: "[SOLVED] sudo x su"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by victorbrca on 2006-12-07
Hi all,


  I read the rootsudo documentation, but I'm still in doubt.

  Somewhere trying to install an application using sudo it denied access to some system file (/etc/...). I them (again somehow) was able to create a su (root) account.

  Is that normal, I mean, sudo not having access to some file, or did I do something wrong?


Vic

---

### Post by taurus on 2006-12-07
What did you run with sudo that you couldn't write to /etc?

---

### Post by victorbrca on 2006-12-07
I don't really remember. I was trying to install my 915resolution for the whole day, tried at least 10 different guides with different commands.

  Really new here. It may have something to do with me dpkging a file and then shutting down the X. By the time I was able to start the X again (which took a while) I had lost the website, and I had visited so many sites that I could not find the rest of the commands, so the files were still in use...

  I don't know. I just started with Linux on Tuesday.  :???: 


Vic

---

### Post by taurus on 2006-12-07
915resolution is available in the repos...  After you have installed it, you need to edit /etc/X11/xorg.conf and change whatever Driver you use for your graphic card to 915resolution...

```
sudo  cp  /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak <-- make a backup
gksudo gedit /etc/X11/xorg.conf
```
It should look something like

```
Driver           "915resolution"
```

---

### Post by victorbrca on 2006-12-07
That was the first one I tried, manually editing xorg.conf

My repos also were not all checked. Didn't find that till later.

Also tried accessing an FTP file trough cli and downloading an 915resolution to a folder and installing. Any command for 915resolution you can find posted on this forum you can bet I tried... :) One of them worked thou... The problem is that for some reason I had to use my root account, but only through cli.

I don't remember which command. They are still all very new to me!!


Vic.

---

### Post by taurus on 2006-12-07
Maybe something like

```
sudo nano -Bw /etc/X11/xorg.conf
```

---

### Post by victorbrca on 2006-12-07
I haven't used any nano command yet...

I remember that after I typed a command using sudo cli asked me "are you root?"


Vic

---

### Post by taurus on 2006-12-07
It's kind of hard to figure out what's wrong if you don't remember what you did!  That's why it's always a good idea to have a piece of paper to write down what you have done in case something goes wrong, then you know which command causes the problem...

---

### Post by victorbrca on 2006-12-08
:???:   I'll make sure I do that for now on!!! 

Thanks taurus...


Vic

---

### Post by victorbrca on 2006-12-08
Ok, this is on example of what I just got...

Apparently there items that were dpkged and not used... 


```
victor@victor-laptop:~$ sudo apt-get update && apt-get install etherwake
Password:
Get:1 http://ca.archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://ca.archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:3 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://ca.archive.ubuntu.com dapper Release
Hit http://ca.archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper Release
Get:4 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://ca.archive.ubuntu.com dapper/main Sources
Hit http://ca.archive.ubuntu.com dapper/restricted Sources
Hit http://ca.archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://ca.archive.ubuntu.com dapper-updates/main Packages
Hit http://ca.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://ca.archive.ubuntu.com dapper-updates/main Sources
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://ca.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Fetched 4B in 1s (3B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it
```


Can anyone give some light to this stupid noob???

Thanks!!


Vic

---

### Post by taurus on 2006-12-08
```
sudo apt-get update && sudo apt-get install etherwake
```

---

### Post by victorbrca on 2006-12-08
Still got same error msg. What happen if I dpkg a file and don't use it?

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Don't know if this helps...

```
victor@victor-laptop:~$ ps -ux
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
victor    4965  0.0  0.9  19720 10268 ?        Ss   11:48   0:01 x-session-manager
victor    5007  0.0  0.0   4336   688 ?        Ss   11:48   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-sessi
victor    5010  0.0  0.0   2712   648 ?        S    11:48   0:00 /usr/bin/dbus-launch --exit-with-session x-session-manage
victor    5011  0.0  0.0   2196   912 ?        Ss   11:48   0:00 dbus-daemon --fork --print-pid 8 --print-address 6 --sess
victor    5013  0.0  0.3   6400  3964 ?        S    11:48   0:01 /usr/lib/libgconf2-4/gconfd-2 5
victor    5016  0.0  0.0   2340   728 ?        S    11:48   0:00 /usr/bin/gnome-keyring-daemon
victor    5018  0.0  0.2   6300  3056 ?        Ss   11:48   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-
victor    5020  0.0  0.9  27640  9400 ?        Sl   11:48   0:01 /usr/lib/control-center/gnome-settings-daemon --oaf-activ
victor    5028  0.0  0.4   5804  4340 ?        Ss   11:48   0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 18
victor    5037  0.3  0.9  15552  9516 ?        Ss   11:48   0:14 metacity --sm-save-file 1165554698-4961-2321944733.ms
victor    5055  0.2  2.3  44812 24408 ?        Ssl  11:48   0:11 gnome-panel --sm-config-prefix /gnome-panel-smz1lg/ --sm-
victor    5062  0.0  2.6  82172 27736 ?        Ssl  11:48   0:03 nautilus --sm-config-prefix /nautilus-srObTn/ --sm-client
victor    5063  0.0  0.5  17260  5200 ?        Ss   11:48   0:00 gnome-volume-manager --sm-config-prefix /gnome-volume-man
victor    5081  0.0  1.0  19568 10544 ?        Ss   11:48   0:00 update-notifier --sm-config-prefix /update-notifier-brIqO
victor    5089  0.0  0.3   8644  3856 ?        Sl   11:48   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon --oaf-activate-ii
victor    5093  0.0  1.0  31880 10504 ?        Ss   11:48   0:00 nm-applet --sm-disable
victor    5102  0.0  0.6  18628  6392 ?        Ss   11:48   0:01 gnome-power-manager --sm-config-prefix /gnome-power-manag
victor    5106  0.0  0.8  48232  8520 ?        Sl   11:48   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAF
victor    5112  0.0  0.0   2288   800 ?        S    11:48   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
victor    5122  0.0  0.9  19408 10132 ?        S    11:48   0:00 /usr/lib/gnome-applets/battstat-applet-2 --oaf-activate-i
victor    5124  0.0  1.2  34852 12828 ?        S    11:48   0:01 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=O
victor    5126  0.0  1.2  34452 12984 ?        S    11:48   0:01 /usr/lib/gnome-netstatus/gnome-netstatus-applet --oaf-act
victor    5128  0.0  1.0  23240 10396 ?        S    11:48   0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFI
victor    5132  0.0  0.1   4180  1688 ?        S    11:48   0:00 /bin/sh /usr/bin/firefox
victor    5143  0.0  0.1   4224  1720 ?        S    11:48   0:00 /bin/sh /opt/firefox/run-mozilla.sh /opt/firefox/firefox-
victor    5148  7.4  9.1 212036 94232 ?        Sl   11:48   4:36 /opt/firefox/firefox-bin
victor    5161  0.0  0.0      0     0 ?        Z    11:48   0:00 [netstat] <defunct>
victor    5167  0.0  0.2  14760  2784 ?        Ss   11:48   0:01 gnome-screensaver
victor    5429  0.0  0.4  11660  5048 ?        S    12:01   0:00 gksu /usr/sbin/synaptic
victor    5515  0.0  0.9  29336  9756 ?        S    12:19   0:01 gksudo network-admin
victor    5673  0.3  1.5  54476 16080 ?        Sl   12:26   0:04 gnome-terminal
victor    5674  0.0  0.0   2284   680 ?        S    12:26   0:00 gnome-pty-helper
victor    5675  0.0  0.3   5564  3224 pts/0    Ss   12:26   0:00 bash
victor    5791  7.8  1.9  44520 20312 ?        S    12:49   0:01 gedit file:///media/usbdisk/Linux/Linux%20Commands.txt
victor    5792  0.0  0.0   2396  1024 pts/0    R+   12:50   0:00 ps -ux

```

---

### Post by taurus on 2006-12-08
How about the output of this command instead?

```
ps -A
```

---

### Post by dbott67 on 2006-12-08
Do you have Synaptic running?

**EDIT:**
It appears that you do have Synaptic running...
```
victor    5429  0.0  0.4  11660  5048 ?        S    12:01   0:00 [COLOR="Red"]**gksu /usr/sbin/synaptic**[/COLOR]

```

Close Synaptic & try again.

-Dave

---

### Post by victorbrca on 2006-12-08
Closing synaptic worked... 

Thanks a lot guys!!! :)


Vic.

---

### Post by victorbrca on 2006-12-08
Ok, sorry guys, but it hapenned again!! What am I doing wrong?

I'm trying to install gparted and I'm getting the same msg

```
victor@victor-laptop:~$ sudo apt-get update && apt-get install gparted
Get:1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Get:3 http://ca.archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://ca.archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://ca.archive.ubuntu.com dapper Release
Hit http://ca.archive.ubuntu.com dapper-updates Release
Hit http://ca.archive.ubuntu.com dapper/main Sources
Hit http://ca.archive.ubuntu.com dapper/restricted Sources
Hit http://ca.archive.ubuntu.com dapper/universe Sources
Hit http://ca.archive.ubuntu.com dapper-updates/main Packages
Hit http://ca.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://ca.archive.ubuntu.com dapper-updates/main Sources
Hit http://ca.archive.ubuntu.com dapper-updates/restricted Sources
Fetched 4B in 10s (0B/s)
Reading package lists... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```


It's the same file "/var/lib/dpkg/lock



Vic.

---

### Post by taurus on 2006-12-08
Look in "ps -A" to make sure synaptic is not running in the background!!!

Also, please run those two commands together like this!

```
sudo apt-get update && sudo apt-get install gparted
```

---

### Post by victorbrca on 2006-12-08
Holly f%*$.. This is exactly the same thing you told me last time.... ](*,) 

I'm really sorry Taurus... I guess I'm trying too hard and not paying enough attention.


Vic

---

### Post by taurus on 2006-12-08
So, does that work now?

```
sudo  apt-get  update  &&  sudo  apt-get  install  gparted
```

---

### Post by victorbrca on 2006-12-08
It did!!!!  :KS 

BTW, do you live here? You answered to my posts different times of the day !! :)


Thanks a lot,


Vic.

---

### Post by taurus on 2006-12-08
> **victorbrca said:**
> It did!!!!  :KS 

Good.  Don't forget the sudo in front of every command if you want to run it as root.  ;) 

> BTW, do you live here? You answered to my posts different times of the day !! :)

Thanks a lot,

Vic.
Nope, although I probably need a life!!!  ](*,)

---

