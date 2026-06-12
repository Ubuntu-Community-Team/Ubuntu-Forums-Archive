---
title: "Cant get Thunderbird to Upgrade"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by mastergunner on 2007-11-25
I have been trying to get Thunderbird to upgrade to the latest 2.0.0.9 but it wont. I have manually downloaded the new one but I am lost after that. Can anyone help me out???

---

### Post by dpar on 2007-11-25
you will only get security upgrades with the linux version. The security upgrades usually take a while after they come out before you will get them too.

---

### Post by dpar on 2007-11-25
If you absolutely have to have the latest and greatest right now, try this

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by mastergunner on 2007-11-25
tried that and it doesnt work. I installed the script but it doesnt run at all. I try to run it in terminal and this is what I get:

brad@brad:~$ ubuntuzilla.py -a install -p thunderbird
bash: ubuntuzilla.py: command not found

What gives??? It shouldnt be this hard.

---

### Post by kellemes on 2007-11-25
> **mastergunner said:**
> tried that and it doesnt work. I installed the script but it doesnt run at all. I try to run it in terminal and this is what I get:

brad@brad:~$ ubuntuzilla.py -a install -p thunderbird
bash: ubuntuzilla.py: command not found

What gives??? It shouldnt be this hard.

try "python ubuntuzilla.py -a install -p thunderbird"

---

### Post by philinux on 2007-11-25
You need the sudo prefix

---

### Post by mastergunner on 2007-11-25
I have tried both this is what happens:

sudo ubuntuzilla.py -a install -p thunderbird
[sudo] password for brad:
sudo: ubuntuzilla.py: command not found
brad@brad:~$ python ubuntuzilla.py -a install -p thunderbird
python: can't open file 'ubuntuzilla.py': [Errno 2] No such file or directory
brad@brad:~$ sudo python ubuntuzilla.py -a install -p thunderbird
python: can't open file 'ubuntuzilla.py': [Errno 2] No such file or directory


So what is going on???

---

### Post by dpar on 2007-11-25
Look in /usr/local/bin and see if ubuntuzilla.py is in there. If not, I'd try to reinstall. The script works fine for me.

---

### Post by nanotube on 2007-11-26
> **mastergunner said:**
> tried that and it doesnt work. I installed the script but it doesnt run at all. I try to run it in terminal and this is what I get:

brad@brad:~$ ubuntuzilla.py -a install -p thunderbird
bash: ubuntuzilla.py: command not found

What gives??? It shouldnt be this hard.

did you actually install the ubuntuzilla deb file? it looks like maybe you just downloaded it, but forgot to install it? :)

---

### Post by mastergunner on 2007-11-26
No I actual installed the deb file. I also looked in my /usr/local/bin and there is nothing in there. I have tried 3 times to install so where is this thing going?

---

### Post by nanotube on 2007-11-26
> **mastergunner said:**
> No I actual installed the deb file. I also looked in my /usr/local/bin and there is nothing in there. I have tried 3 times to install so where is this thing going?

hm, please run the following command and post the complete output:
```
dpkg -L ubuntuzilla
```

this command will list all the files installed with the ubuntuzilla package (if the package is installed - otherwise it will say "package not installed")

---

### Post by mastergunner on 2007-11-26
This is what it says:
brad@brad:~$ dpkg -L ubuntuzilla
/.
/etc
/etc/cron.daily
/etc/cron.daily/ubuntuzillaupdatecron
/usr
/usr/local
/usr/local/bin
/usr/local/bin/ubuntuzilla.py
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/ubuntuzilla.1.gz
/usr/share/man/man1/ubuntuzilla.py.1.gz

What now??? Thanks for the help.

---

### Post by nanotube on 2007-11-27
> **mastergunner said:**
> 
What now??? Thanks for the help.

ok, nice, so it's installed. then my guess is, you don't have /usr/local/bin in your default path. easy enough to solve.

try using full path, and run command:
```
python /usr/local/bin/ubuntuzilla.py -a install -p thunderbird
```

(note: sudo is not needed when running ubuntuzilla. it will ask you for sudo password just for the parts that need it)

---

### Post by mastergunner on 2007-11-27
Got it I appreciate all the help. I LOVE THIS FORUM and appreciate the help from all  the LINUX GURU's.

---

### Post by nanotube on 2007-11-28
> **mastergunner said:**
> Got it I appreciate all the help. I LOVE THIS FORUM and appreciate the help from all  the LINUX GURU's.

glad it worked out for you! :)

---

