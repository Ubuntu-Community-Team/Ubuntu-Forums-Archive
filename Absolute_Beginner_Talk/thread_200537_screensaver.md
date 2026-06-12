---
title: "screensaver"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by Newbie_needs_help on 2006-06-19
I have ubuntu 6.06 and I wanted to get the older screensaver atlantis so I tried uninstalling the gnome-screensaver package because I heard if you uninstalled it and left xscreensaver you would have the older screensavers. Well now when I go to system- preferences theres nothing I can click on for screensavers and now my screensavers dont work at all. Please help me get my screensavers back. Thanks

---

### Post by gnack on 2006-06-19
I have Atlantis as an option under System -> Preferences -> Screensaver with a default Breezy (5.10) install.

---

### Post by givré on 2006-06-20
did you install xscreansaver, this is not install by default

---

### Post by Newbie_needs_help on 2006-06-20
I dont know ill check. No I havnt but when i try to install it it says its obsolete so it wont let me install it same with gnome-screensaver ](*,) im running into a wall.

---

### Post by Drakkor on 2006-06-20
Don't want ot hi-jack the thread, but it seemed stupid to start another one for a screensavers problem. Mine don't work anymore, Have had Dapper on here for about a week now,and they used to work,but now, I just get a black screen ! 
I go to System>Preference>Screensaver, and try to pick another one,instead
of Random like it was,and only 2 or 3 of them work, the rest are all black !!
Any help ?? :confused:   TIA

---

### Post by Drakkor on 2006-06-20
OK, update, seems I had dowloaded the xscreensaver also, so I went into Synaptic and removed both the xscreensaver,and the gnome-screensaver,then
reinstalled the gnome saver, and now it works,but I have only 3 screensavers.
Cosmos, the flying gnome feet,and a pictures folder ! :confused:

---

### Post by givré on 2006-06-20
Install xscreensaver-data and xscreensaver-gl

---

### Post by Drakkor on 2006-06-20
I already looked at the wiki, and couldn't find out anything about screensavers.](*,)
Are gnome-screensavers, and xscreensaver compatible ?  Thanks

---

### Post by Newbie_needs_help on 2006-06-20
Hi im back and I've decided to copy the message I get when i try to install the screensaver packages(theres only one they are all the same message):

gnome-screensaver:

Package gnome-screensaver has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

Anyone know what I should do?

---

### Post by givré on 2006-06-20
ok, what is your source.list ```
gedit /etc/apt/sources.list
```

---

### Post by Newbie_needs_help on 2006-06-20
When I do that the text editor comes up blank same with the terminal/command line thing.

---

### Post by givré on 2006-06-20
It seams that you broke your source.list, but anyway, we can resolve that:
Open a terminal and copy
```
wget -c http://www.psychocats.net/ubuntu/sources.list
sudo chown root:root sources.list
sudo cp sources.list /etc/apt/sources.list
```
That's sould be ok.

---

### Post by Newbie_needs_help on 2006-06-20
ok this is what happened.

sam@Cub:~$ wget -c [http://www.psychocats.net/ubuntu/sources.list](http://www.psychocats.net/ubuntu/sources.list)
--13:48:03--  [http://www.psychocats.net/ubuntu/sources.list](http://www.psychocats.net/ubuntu/sources.list)
           => `sources.list'
Resolving [www.psychocats.net](www.psychocats.net)... 64.14.68.87
Connecting to www.psychocats.net|64.14.68.87|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,459 (1.4K) [text/plain]

100%[====================================>] 1,459         --.--K/s

13:48:03 (24.41 MB/s) - `sources.list' saved [1459/1459]

sam@Cub:~$ sudo chown root:root sources.list

now when I opened the sources list it was still empty.

---

### Post by Drakkor on 2006-06-20
OK, givré , I have downloaded and installed the xscreensaver files, and can preview and select them, but no-go on the desktop..... :confused:

---

### Post by givré on 2006-06-20
[QUOTE=Newbie_needs_help]ok this is what happened.

sam@Cub:~$ wget -c [http://www.psychocats.net/ubuntu/sources.list](http://www.psychocats.net/ubuntu/sources.list)
--13:48:03--  [http://www.psychocats.net/ubuntu/sources.list](http://www.psychocats.net/ubuntu/sources.list)
           => `sources.list'
Resolving [www.psychocats.net](www.psychocats.net)... 64.14.68.87
Connecting to www.psychocats.net|64.14.68.87|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,459 (1.4K) [text/plain]

100%[====================================>] 1,459         --.--K/s

13:48:03 (24.41 MB/s) - `sources.list' saved [1459/1459]

sam@Cub:~$ sudo chown root:root sources.list

now when I opened the sources list it was still empty.[/QUOTE]
did you do```
sudo chown root:root sources.list
sudo cp sources.list /etc/apt/sources.list
```
to test it do gedit /etc/apt/sources.list after

---

### Post by Newbie_needs_help on 2006-06-20
nows there stuff there

---

### Post by givré on 2006-06-20
[QUOTE=Drakkor]OK, givré , I have downloaded and installed the xscreensaver files, and can preview and select them, but no-go on the desktop..... :confused:[/QUOTE]
You need to launch the daemon
```
 gnome-screensaver
```

---

### Post by Newbie_needs_help on 2006-06-20
now its asking for me to do some updates should I?

---

### Post by givré on 2006-06-20
Of course you should

---

### Post by Newbie_needs_help on 2006-06-20
ok well its almost done. There was 81 packages to load

---

### Post by givré on 2006-06-20
wha, it was a long you didn't update your system :cool: 
Just to be sure that you will not have issue, what is the kernel you are using, the 386? if it is be sure that you have linux-386 install:
```
sudo apt-get install linux-386
```

---

### Post by Newbie_needs_help on 2006-06-20
Thanks alot:cool:. I hope it works now. How long have u had ubuntu?

---

### Post by Newbie_needs_help on 2006-06-20
I have to go. Bye  hope i get some good books at the library.

---

### Post by Drakkor on 2006-06-20
YAY !!  :D  It's working now !!  Thanks, givré  :p

---

