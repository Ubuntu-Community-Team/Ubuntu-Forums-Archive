---
title: "Limewire help"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by katarot on 2006-04-04
hey all i downloaded limewire from there site and i tryied to follow the instructions 
in the guide but its not working for me 

if someone can tell me an alternative 
or maybe just explain to me what to do here im really confused

---

### Post by Perfect Storm on 2006-04-04
Please link to the guide, also terminal input/output. Which version of ubuntu do you use?

---

### Post by Qrk on 2006-04-04
I prefer gtk-gnutella, which you can get from the repositories:
```

sudo apt-get install gtk-gnutella
```

Frostwire is an alternative, which is exactly the same as Limewire but it provides .deb packages. 

[http://www.frostwire.com/static/downloads.html](http://www.frostwire.com/static/downloads.html)

First you need Java installed. The Ubuntu wiki tells you how to do this:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Get the ubuntu .deb file, and save it to your desktop.

```
cd ~/Desktop
sudo dpkg -i FrostWire-4.10.9-1.i586.deb
```

I've heard that there is a problem with the Ubuntu build... after installing run this if it doesn't work.
```

sudo apt-get install sysutils
sudo dos2unix /usr/lib/frostwire/runFrost.sh
```

---

### Post by katarot on 2006-04-04
emm this is the guide im using 
[http://www.ubuntuguide.org/#limewire](http://www.ubuntuguide.org/#limewire)

katarot@ubuntu:~$ sudo unzip -u LimeWireLinux.rpm -d /opt/
unzip:  cannot find or open LimeWireLinux.rpm, LimeWireLinux.rpm.zip or LimeWireLinux.rpm.ZIP.
katarot@ubuntu:~$

---

### Post by Perfect Storm on 2006-04-04
Download the .rpm version it works well (using it myself)

First:
```
sudo apt-get install alien
```

then download the .rpm version of Limewire to your Desktop 

```

cd Desktop
sudo alien XXXXXXXX.rpm
sudo dpkg -i XXXXXXXXX.deb
```
where XXXX is the name of the package (remember that linux is case sensitive)

---

### Post by katarot on 2006-04-04
ok that work great but when i go to applications > internet and select it nothing happens 
i remember from windows it used to sit in the taskbar and i had to select it and go to open but its not in the toolbar 

i have to use ndiswrapper to work with my wificard could that be the problem

---

### Post by Perfect Storm on 2006-04-04
Did you install java? Limewire needs java.

---

### Post by ecto on 2006-04-04
Can you please elaborate further on what your problem is? You should have Java sun not Java Black for java...Also it is make sure you have java development kit to ensure that you have the java compiler. If the compiler still says it is missing place the binary in your path sudo ldconfig and rehash wouldnt hurt. But these are generalizations...As I said... Elaborate and ill help a bit more

---

### Post by katarot on 2006-04-04
i tried it in the terminal and got this 
katarot@ubuntu:~$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
katarot@ubuntu:~$

i will go and download these just now

---

### Post by Perfect Storm on 2006-04-04
You might check this: [http://ubuntuforums.org/showthread.php?t=76735&highlight=java](http://ubuntuforums.org/showthread.php?t=76735&highlight=java)

---

### Post by Rhys_Pieces on 2007-11-11
Okay for anyone still having a problem loading Limewire just clickthis link and tell it to run not save to disk.  [http://www9.limewire.com/download/LimeWireLinux.deb](http://www9.limewire.com/download/LimeWireLinux.deb)

---

### Post by DarinB on 2007-11-18
i have limewire running but not too fast.
any ideas
some stuff just zips other is very slow... i am a newbie to this limewire stuff on ubuntu
i win it was easy not so sure now
do i need to open ports like in bit torrent.
i am not sure since i can download some stuff really fast.
also how do i deal with the lack of selection??????
does bit torrent have a bigger selection i once tried emule with win
but it was days to get one movie???
sorry i just need advise on this stuff.

---

