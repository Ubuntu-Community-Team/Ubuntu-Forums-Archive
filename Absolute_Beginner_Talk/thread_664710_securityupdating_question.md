---
title: "security/updating question"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by net-reg on 2008-01-11
hi all! 
kindly help --

  1) is it okay to install ubuntu and just start surfing rightaway 
          (windows virus/spyware wont cling to it? i am home user)

  2) is it necessary to install firewall for home user
            (ok i hv done it n checked the site 'shield's up' n it said passed; but the question
              remains)

  3) how do i see what programs are connecting to net 
            ( like 'zone alarm' in windows tells what prgm wants to connect to internet. 
              Isnt it that a malicious prgm in linux will want to connect to net too)

  4) how to install updates _unattended_
            ( my isp gives free bandwith only in night for four hours, so how not to sit in
               front of comp at those hours n tell ubuntu/kubuntu to update itself. i tried 
              'at' command but #sudo aptitude -yd safe-upgrade didnt work. it still posed a
              question n stopped)

  5) suggest games (FPS) :-) 
  thanks

---

### Post by dmitriyp13 on 2008-01-11
To answer a few of your questions:
1) It is perfectly ok to start surfing right out of the box (provided that everything is up to date).
2) It is not necessary to have a firewall or a virus scanner on a linux machine.  I have a webserver and an ssh server running without either and have been perfectly ok. This took a while to get over when I switched away from XP.
3) To see what programs are connecting to the internet, use the 'netstat' command in terminal.
4) I am not quite sure exactly how to achieve this, but it seems some kind of a combination between cron (scheduler) and apt.

I hope this helps.

---

### Post by Niniel on 2008-01-11
> **net-reg said:**
> 
  5) suggest games (FPS) :-) 
  thanks

Check out id games (Quake, Doom, etc.), they tend to create native Linux versions of their games.

Otherwise, a lot of the Valve games run under Wine (sort of a Windows emulator for Linux, not a virtual machine), too.

---

### Post by Pevichaey5 on 2008-01-11
ok

on ubuntu a firewall is installed by default called 'ip tables' you can if you want install an interface called 'firestarter' for it

as for games, i play alien arena (free and open source) from the synaptic package manager and supertux kart and now just waiting for the ut3 linux client and i'll be sorted lol

i haven't installed anti virus on my computer and i've been using Linux for just over 10 months now and i've never had a Linux virus and as for windows viruses, they can't do anything to your system even if you run them lol

i'm not sure about automatically updating, but if you've only just installed, there will be a few updates lol, just click to download and just leave it, it will do the rest except the reboot afterwards, only really needs the reboot because of a kernel patch

hope this helps

---

### Post by net-reg on 2008-01-12
> **dmitriyp13 said:**
> To answer a few of your questions:

4) I am not quite sure exactly how to achieve this, but it seems some kind of a combination between cron (scheduler) and apt.
.


yes i tried varios combinations of cron / at but it dosen't work.
googling found this-- [http://kevin.vanzonneveld.net/techblog/article/schedule_automatic_updates_on_ubuntu/](http://kevin.vanzonneveld.net/techblog/article/schedule_automatic_updates_on_ubuntu/)
will try it tonight. let's see how it turns out to be.

---

### Post by net-reg on 2008-01-12
> **thexero said:**
> ok


i'm not sure about automatically updating, but if you've only just installed, there will be a few updates lol, just click to download and just leave it, it will do the rest except the reboot afterwards, only really needs the reboot because of a kernel patch



thanks for helping.
i found this also--- [http://woozle.org/blogs/neale/2007-10-26T16:34:26Z?r=1](http://woozle.org/blogs/neale/2007-10-26T16:34:26Z?r=1)
but i cant make the head n tails of it currently. (ah,newbie)
so trying the other site  found.

---

### Post by shae on 2008-01-12
To make the computer update without any input you would want to use the following command:

```
sudo apt-get -q -y update && sudo apt-get -q -y upgrade
```

-q puts apt-get into quiet mode and -y tells apt-get to assume yes.  This could be dangerous though, use at your own risk.

---

### Post by net-reg on 2008-01-13
> **shae said:**
> To make the computer update without any input you would want to use the following command:

```
sudo apt-get -q -y update && sudo apt-get -q -y upgrade
```
.

but isnt aptitude to be preferred now?

thanks anyway for this, will try it too:)  [i lv running all sorts of commands, lets see how many before i break sth]

googling (what else) i tried this command with 'at' and was able to update ubuntu 7.10 without any input. -----
#at 3:00 tomorrow
#sudo unattended-update
(but first i edited /etc/sudoers --added this-- Defaults:usernamehere	timestamp_timeout=600
 this made sudo not ask for password for 600min
and by morning it was all ready! the system-update-tool showed that system is up-to-date!

n so the saying is verified once again -- try n try n u will succeed // Google and Ye Shall Find.

thank u all for ur inputs/time.

---

### Post by net-reg on 2008-03-05
found another easy way to update during off hours ---go to--->
  system----administration----software source---update----check for updates daily & download updates in background
  now all i have got to do is to ---- # at 2am tomorrow       
				                      # pon dsl-provider
				                 	# at 8am tomorrow
                     			                # poff
  next morning all updates have been downloaded and all i have to do is to click update button near clock.	

man it was so simple, sheeesh, took so much time to get there.

---

### Post by hyper_ch on 2008-03-05
don't install unattended.... download the packages unattended.. when you then install them you can still see if there are bugs/issues with it.

I haven't tested it but code should be:
```

apt-get update && apt-get upgrade -d

```

Now, how do you run that?

--> You use cron and a little shell script

(1) updatescript.sh
create the updatescript in the /root folder
```

sudo nano /root/updatescript.sh

```

paste this code
```

#!/bin/bash
apt-get update
apt-get -y -d upgrade

```

Save the file by pressing ctrl-x and hit enter

Now make it executable with this
```

sudo chmod 0700 /root/updatescript.sh

```

(2) Cron entry

I prefer to make a text file with my cron entries and load this then to cron

Create the file
```

sudo nano /root/cron.txt

```

Paste the cronjobs in it
```

0 0 * * * sh /root/updatescript.sh

```
That would run the cron every night at midnight. The first number is the minute in the hour, the second one the hour. To run a cron every morning at 3:52 you'd enter this:
52 3 * * *

press again ctrl-x and hit enter for saving the file

Now add the cron to the root cron by issuing this:
```

sudo crontab /root/cron.txt

```

Check if it was really added:
```

sudo crontab -l

```

---

