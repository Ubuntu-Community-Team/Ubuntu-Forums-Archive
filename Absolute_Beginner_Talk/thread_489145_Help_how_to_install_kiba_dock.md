---
title: "Help how to install kiba dock"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by fongs on 2007-07-01
Hi I would like to install kiba dock Latest version or, most stable version any help would be appreciated.

---

### Post by cwood06 on 2007-07-01
add this repo to your /etc/apt/source.list
```

# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs... 
deb http://download.tuxfamily.org/3v1deb feisty eyecandy 
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

add the gpg key

```
sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

then do a 
```

sudo apt-get update
```

then do a 
```

sudo apt-get install kiba-dock
```

---

### Post by fongs on 2007-07-01
thanks for help cwood06 But being as inexperienced as i am add the gpg key means nothing to me could you explain it to me.

---

### Post by Perfect Storm on 2007-07-01
It's a safty device that you aknowledge the specific source.

---

### Post by cwood06 on 2007-07-01
ok doky ill try to go a little better sorry,

```
 sudo gedit /etc/apt/source.list
```

use that to edit the text file add the repo and continue on

---

### Post by Campingman on 2007-07-02
> **cwood06 said:**
> ok doky ill try to go a little better sorry,

```
 sudo gedit /etc/apt/source.list
```

use that to edit the text file add the repo and continue on

That should be:
sudo gedit /etc/apt/sources.list
;)

---

### Post by fongs on 2007-07-02
Thanks for help got it working by
System / Administration / Synaptic package manager / Settings / Repositories / Third Party Software / Add
 Then copy and paste 
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy 

deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
 Indivdually 
Then ran and started from applications
Thanks again to all concerned hope this helps some others.

---

### Post by sambehera on 2007-07-02
hi i added the repository, but cannot find the kiba-dock package in it... please help :(

---

### Post by Seisen on 2007-07-02
Did you search in synaptic or use apt-get?

---

### Post by fongs on 2007-07-02
> **sambehera said:**
> hi i added the repository, but cannot find the kiba-dock package in it... please help :(

Make sure you add the whole lot then have a look for it in somewhere in applications.

```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
```

```
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

even the deb part then you'll be fine.

---

### Post by sambehera on 2007-07-16
sorry i have 64 bit amd... and have added the 64bit eyecandy repository... but still no kiba dock... i am running kubuntu feisty 64bit

---

### Post by john0589 on 2007-07-29
ok i installed and run the program..........then get this error:
Error: Unable to open dir /home/john/.kiba-dock/config_schemas
notifications: Error opening directory '/home/john/.kiba-dock/config_schemas': No such file or directory

what should i do?:confused:

---

### Post by sailor2001 on 2007-07-29
you have to add the tux key............best to do it through the terminal as previously posted

---

### Post by threeonethree on 2007-07-29
> **john0589 said:**
> ok i installed and run the program..........then get this error:
Error: Unable to open dir /home/john/.kiba-dock/config_schemas
notifications: Error opening directory '/home/john/.kiba-dock/config_schemas': No such file or directory

what should i do?:confused:

u installed it correctly .. it happened when i installed it too , there should be a solution on the forums , search for it

---

### Post by xpod on 2007-07-29
> That should be:
sudo gedit /etc/apt/sources.list


It should actually be
```
gksudo gedit /etc/apt/sources.list
```

The "gk" should always proceed the sudo command when running graphical app`s as far as i understand.
Aysiu explains it so much better than i ever could.....
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by boob11 on 2007-09-03
Thnx

---

