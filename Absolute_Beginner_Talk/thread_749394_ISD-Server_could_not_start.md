---
title: "ISD-Server could not start"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by gbold on 2008-04-08
I have installed Ubuntu Hardy Heron and then the Edubuntu add-on cd on an old PIII-1.1GHz Compaq and I am now getting the error:

ISD-Server could not start because port 5800 is not available.

I have googled this and am finding nothing.  Can you all help me turn off whatever is causing this error?  I am giving this computer to my neighbors kids and I am trying to make it as error-free as possible (for an 8-year old).  Other than this, everything runs great, including the Airlink wireless card I have in it.  The kids are quite excited as there is a lot of kid related software they can use installed...
Greg

---

### Post by OffAxis on 2008-04-08
what does 

```
netstat -pant
```

give you?

---

### Post by gbold on 2008-04-08
I'm currently at work (shhh!) but I'll try it at home in about 5 hours... Thanks-
Greg

---

### Post by gbold on 2008-04-08
Here's the output:

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:5800          0.0.0.0:*               LISTEN      5424/ica        
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN      5466/ica        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      4898/cupsd      
tcp        0      0 192.168.1.20:47295      91.189.94.186:80        TIME_WAIT   -               
tcp        1      1 192.168.1.20:54204      91.189.90.132:80        LAST_ACK    -               
tcp        0      0 192.168.1.20:47307      91.189.94.186:80        TIME_WAIT   -               
tcp        0      0 192.168.1.20:47298      91.189.94.186:80        TIME_WAIT   -               


Anything else I can supply?
Greg

---

### Post by OffAxis on 2008-04-09
right here
> 
tcp 0 0 127.0.0.1:**5800** 0.0.0.0:* LISTEN 5424/ica
tcp 0 0 0.0.0.0:5900 0.0.0.0:* LISTEN 5466/ica 

that's what's using your 5800 port; **ica**, and it's attached to the internal ip.
I'm not entirely certain what program that is; usually vnc uses ports 5800 & 5900.
Hopefully someone who recognizes it will jump in...

If that doesn't happen, you could try running a search in your system to see if there's some documentation and where the executable is.

```

cd /
sudo find -name ica
```

you could also try a 

```
sudo ps -eLf
```

and get a list of running processes, hopefully with a path attached that gives you some indicator of what it is.

---

### Post by gbold on 2008-04-10
Thanks again for your reply...  It looks like it might be tied to Italc which may be a part of Edubuntu...  The kids are really enjoying the box and seem to like hanging on the Linux side of it (vice windows).  I told them i'll be back over to install the final version at the end of April (Hardy heron).  Thanks for all of your help!
Greg

---

### Post by haroldship on 2008-04-28
Did you ever find a solution to this? I have the same problem in Edubuntu Hardy Heron, AMD64.

---

### Post by jringoot on 2008-04-28
Hi There,

I don't know what the ISD-server is or does, when I look it up in google I only find things about webcam servers (Image Streaming Deamon?)
I would like to know what the ISD-server is, it appears undocumented in Ubuntu.

But I do know what ica is: the citrix metaframe client (see [http://www.citrix.com/](http://www.citrix.com/)) 

locate setupwfc on your system, this script can install/uninstall the ica client.

But probably you use this to connect to a citrix server to work on your remote windows desktop.


Joost

---

### Post by haroldship on 2008-04-29
> **jringoot said:**
> 
But I do know what ica is: the citrix metaframe client (see [http://www.citrix.com/](http://www.citrix.com/)) 

locate setupwfc on your system, this script can install/uninstall the ica client.


I don't have setupwfc on my system. I didn't deliberately install ica. It's part of Edubuntu. I can't remove italc either, without removing all of Edubuntu.

> **jringoot said:**
> 
But probably you use this to connect to a citrix server to work on your remote windows desktop.
Joost

I don't actually use it. I would like to remove it since it just gives me annoying popups.

---

### Post by djwohls on 2008-05-03
OK, here is how I got the error messages to go away.  I have made this change and have been running successfully without any issues or error messages.

Note: I am not really sure what other issues this may cause, so YMMV.

I launched a sudo session of Nautilus and went to the /usr/bin directory.  There I renamed "ica" to "icaxx".  This prevents any ica processes from being started.

This is on 8.04 Hardy Edubuntu.

If anyone knows what other issues this may cause please advise.  I was tired of seeing all of the errors on boot.  I couldn't find any other solution to the issue.  I thought I was close with this ([http://italc.sourceforge.net/wiki/index.php?title=ITALC_in_a_ThinClient_environment#Start_ICA_on_correct_port_at_logon](http://italc.sourceforge.net/wiki/index.php?title=ITALC_in_a_ThinClient_environment#Start_ICA_on_correct_port_at_logon)) but ran into a dead end.

-Dan

---

### Post by terets on 2008-05-05
Does anyone have a solid fix for this?  I don't want to rename files when that can have an adverse effect on how everything functions.  I just installed ubuntu/kubuntu/edubuntu and I keep getting this error 4 or 5 times everytime I log into KDE.  I have the same output as gbold for netstat -pant.  Here is the output I get from the other commands:

```

# sudo find -name ica
./usr/bin/ica

# sudo ps -eLf | grep ica
user  1007  6353  1007  0    1 11:20 pts/0    00:00:00 grep ica
user  6284  6159  6284  0    3 10:39 ?        00:00:00 ica -session 101ba147116149000120991761500000074230013_1209935990_647889
user  6284  6159  6292  0    3 10:39 ?        00:00:00 ica -session 101ba147116149000120991761500000074230013_1209935990_647889
user  6284  6159  6293  0    3 10:39 ?        00:00:00 ica -session 101ba147116149000120991761500000074230013_1209935990_647889
user  6286  6159  6286  0    3 10:39 ?        00:00:02 ica -session 101ba147116149000120992801700000061750014_1209935990_647195
user  6286  6159  6289  0    3 10:39 ?        00:00:00 ica -session 101ba147116149000120992801700000061750014_1209935990_647195
user  6286  6159  6290  0    3 10:39 ?        00:00:00 ica -session 101ba147116149000120992801700000061750014_1209935990_647195
user  6291  6286  6291  0    1 10:39 ?        00:00:01 /usr/bin/ica -rx11vs -nosel -nosetclipboard -rfbport 5900 -rx11vs -isdport 5800 -role other
user  6294  6284  6294  0    1 10:39 ?        00:00:00 [ica] <defunct>
user  6356  6159  6356  0    3 10:39 ?        00:00:00 ica -session 101ba147116149000120993010600000061820018_1209935990_647702
user  6356  6159  6364  0    3 10:39 ?        00:00:00 ica -session 101ba147116149000120993010600000061820018_1209935990_647702
user  6356  6159  6365  0    3 10:39 ?        00:00:00 ica -session 101ba147116149000120993010600000061820018_1209935990_647702
user  6366  6356  6366  0    1 10:39 ?        00:00:00 [ica] <defunct>
user  6480  6159  6480  0    1 10:39 ?        00:00:00 /bin/bash /usr/bin/ica-launcher
user  6481  6480  6481  0    3 10:39 ?        00:00:01 ica -noshm
user  6481  6480  6486  0    3 10:39 ?        00:00:00 ica -noshm
user  6481  6480  6487  0    3 10:39 ?        00:00:00 ica -noshm
user  6488  6481  6488  0    1 10:39 ?        00:00:00 [ica] <defunct>

```

I am researching this problem in hopes of finding a solution, but not getting much further than gbold.  Any help would be good.

---

### Post by haroldship on 2008-05-06
Ok - I've managed to get rid of the problem, but I don't really like the solution.

**You have to do this for each and every user on the computer.**

From the Gnome panel:

System --> Preferences --> Sessions

Startup Programs tab: Unselect iTalc client.

Current Sessions tab: Remove any and all ica or ica-launcher processes.

---

### Post by alkisg on 2008-05-15
Guys, ica is part of italc.sourceforge.net (as you already mentioned - see man ica for details). I have it (along with the same error sometimes) on Ubuntu without having installed any edu* staff.

But that's because I need to use iTalc, if you don't use it, why don't you just uninstall it?

sudo apt-get remove libitalc italc-client italc-master

---

### Post by polker on 2008-06-12
sudo apt-get remove --purge italc-client should be the savest way - even if i would love to have installed that programm working (it did in the past on debian/lenny and m$ xp)

I will try to install the latest version 1.09 - the one from the repositories is only 1.07

volker

---

