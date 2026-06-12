---
title: "how do i make sound better quality"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by pavel_kbc on 2006-11-30
hello pplz. i got on board sound card (intel 945gnt) and i using codec "GStreamer extra plugins" can you plesae tell how do i make sound better quality as well. 

](*,) sound quality good on windows :(

---

### Post by deadgobby on 2006-11-30
> **pavel_kbc said:**
> hello pplz. i got on board sound card (intel 945gnt) and i using codec "GStreamer extra plugins" can you plesae tell how do i make sound better quality as well. 

](*,) sound quality good on windows :(
 Check the volume levels. If it is static or distorted. You have  the sound way too high. Install ALSA mixer or install it. Play with the sound levels till they are at par to your liking. Or you have some bad head phones or speakers.
Gobby

---

### Post by hotbrainz on 2006-11-30
Can i safely presume that you are a new Ubuntu to user. If so, you will have install a number of audio codecs and other essential software. I suggest you use "Automatix". It is a graphical interface and will be easy for you to follow. the link is:

[http://getautomatix.com/wiki/index.php?title=Installation]("http://getautomatix.com/wiki/index.php?title=Installation")

Hope this helps
Cheers

---

### Post by deadgobby on 2006-11-30
You may want to wait for installing Automatix. The server is down for a bit for updates. So try about an hour.
Gobby

---

### Post by pavel_kbc on 2006-11-30
ok lamme try the Automatix. i am not so newbie :S i know about Automatix.but i didnt try it .so i installed GStreamer

---

### Post by pavel_kbc on 2006-11-30
root@r00t-server:/home/r00t# sudo apt-get install automatix2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  automatix2
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 190kB of archives.
After unpacking 0B of additional disk space will be used.
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main automatix2 1.1-1.11-6.10edgy_i386 [190kB]
Fetched 190kB in 4m9s (762B/s)                                                 
Selecting previously deselected package automatix2.
(Reading database ... 100895 files and directories currently installed.)
Unpacking automatix2 (from .../automatix2_1.1-1.11-6.10edgy%5fi386_i386.deb) ...
Setting up automatix2 (1.1-1.11-6.10edgy_i386) ...
root@r00t-server:/home/r00t# automatix2
GTK Accessibility Module initialized
GTK Accessibility Module initialized
Starting
root@r00t-server:/home/r00t# automatix2
GTK Accessibility Module initialized
GTK Accessibility Module initialized
Starting
root@r00t-server:/home/r00t# automatix2
GTK Accessibility Module initialized
GTK Accessibility Module initialized
Starting
--23:27:42--  [http://www.getautomatix.com/keys/quinn2.key](http://www.getautomatix.com/keys/quinn2.key)
           => `quinn2.key'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.193.29
Connecting to www.getautomatix.com|82.165.193.29|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,690 (1.7K) [text/plain]

100%[====================================>] 1,690         --.--K/s             

23:27:44 (123.98 MB/s) - `quinn2.key' saved [1690/1690]

gpg: can't open `quinn2.key': No such file or directory
gpg: Total number processed: 0
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
--23:27:44--  [http://www.getautomatix.com/keys/jriddell.key](http://www.getautomatix.com/keys/jriddell.key)
           => `jriddell.key'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.193.29
Connecting to www.getautomatix.com|82.165.193.29|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 33,686 (33K) [text/plain]

100%[====================================>] 33,686         1.81K/s    ETA 00:00

23:28:13 (1.25 KB/s) - `jriddell.key' saved [33686/33686]

gpg: can't open `jriddell.key': No such file or directory
gpg: Total number processed: 0
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
Traceback (most recent call last):
  File "/usr/bin/automatix.py", line 65, in ?
    start = startUp()
  File "/home/arnav/resin2/debtree/source/usr/lib/automatix2/startup.py", line 26, in __init__
  File "/home/arnav/resin2/debtree/source/usr/lib/automatix2/startup.py", line 114, in checkEnviroment
  File "/home/arnav/resin2/debtree/source/usr/lib/automatix2/resin_config.py", line 101, in update_apt
  File "/home/arnav/resin2/debtree/source/usr/lib/automatix2/resin_controllers.py", line 56, in __init__

  File "/home/arnav/resin2/debtree/source/usr/lib/automatix2/terminal.py", line 117, in connect_pipe
  File "/home/arnav/resin2/debtree/source/usr/lib/automatix2/extra_functions.py", line 126, in update_ui
KeyboardInterrupt
root@r00t-server:/home/r00t# automatix2


please help me

---

### Post by pavel_kbc on 2006-11-30
in #ubuntu . they dont like the automatix2. they said its bracks the system

---

