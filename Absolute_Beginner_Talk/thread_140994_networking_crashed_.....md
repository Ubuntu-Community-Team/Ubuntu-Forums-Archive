---
title: "networking crashed ...."
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by badiruz on 2006-03-07
hi everyone ... 

I tried to establish the wireless connection with 3com wireless modem here in my friends flat ... however I could not make it and without knowing I did "something" wrong and now I can not access my networking to fix the any problems with internet connections :( ... (I had no problems with wireless before in other places)

now when I start ubuntu on my laptop (IBM T41) a window is opening while starting with the following note:

--------------
!!!! Could not look up internet address for .
This will prevent GNOME from operating correctly-
It may be possible to correct the problem by adding to the file /etc/hosts.
--------------

I am a totally beginner :-|  and really do not know what to add on this file ... 

I very appreciate any help ... :) 

thanks ... 

b.:)

---

### Post by bato on 2006-03-07
Ehi, don't worry
I think your /etc/hosts file is corrupted. It happened me too.
Ok. Enter in gnome.

Start a terminal (Application->Accessories->Terminal)

then edit

```
less /etc/hosts
```

It would be something like

```
127.0.0.1 localhost.localdomain localhost ErodeLX

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

In the first line ErodeLX is my host name (my pc name).

So if it isn't you can look if there is a hosts~ file (it's a temp file).

again ```
less hosts~
```

if it's correct you have to move hosts~ in hosts.

```
sudo gedit /etc/hosts &
sudo gedit /etc/hosts~
```

then copy all by hosts~ and past into hosts

sudo command maybe dosen't work. In this case reboot and go in safe mode then:

```
cp /etc/hosts /etc/hosts.backup
rm /etc/hosts
cp /etc/hosts~ /etc/hosts
```

if hosts~ dosen't exist then you have to edit /etc/hosts and write the code above.

```
nano /etc/hosts
```

write 

```
127.0.0.1 localhost.localdomain localhost ErodeLX

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

with your pc name instead of ErodeLX.
CTRL+o, CTRL+x

reboot and see if it works

---

### Post by badiruz on 2006-03-07
thank you very much for you help ... however it did not work ... is it possible that I may delete the host name ????? ... if yes I had to be nominated for the Ubuntu crack down oscars (if there is such a thing) ... the first line was as you wrote, than I changed it to something else with an advice of a friend who also uses ubuntu ... did not work ... and I entered the first line again as previous ... I checked the hosts names as you suggested but the command did not work ... I am typed "su" in the terminal and get in writting my password ... and followed your instructions using mc ... 

what else can I do to give my host its name back or whatever ... 

thanks ... for your concern ... 

...b.:)

---

### Post by Iowan on 2006-03-07
Not absolutely certain, but **su** probably isn't gonna work without **do** behind it. Without my Ubuntu box for reference, I'm guessing... but does the hostname appear in the **interfaces** file?

---

### Post by bato on 2006-03-08
To see your hostname you have to digit in a terminal

```
hostname
```

if it's different from that in your /etc/hosts modify your /etc/hosts

---

### Post by Iowan on 2006-03-08
From [http://www.howtoforge.com/samba_setup_ubuntu_5.10_p3]("http://www.howtoforge.com/samba_setup_ubuntu_5.10_p3")> Setting The Hostname

echo server1.example.com > /etc/hostname 
/bin/hostname -F /etc/hostname
I haven't tried it - dunno if it works...

---

### Post by badiruz on 2006-03-08
thanks Bato and Iowan .... 
I tried all these ... the setting hostname did not work or I could not made it ... I also went to the link you wrote Iowan to follow some instructions ... anyway I tried with the command hostname to see if it is there ... the name ... but only a blank line appeared ... so it means that my computer has no hostname anymore for networking purposes ... does this mean that I have to download whole or some parts of ubuntu again ... ????

any more suggestions (better than the re-downloading -set up- of ubuntu) ... ????

...b.:)

---

### Post by bato on 2006-03-08
try to set /etc/hostname by yourself.

nano /etc/hostname

then type the name that you want for your pc, CTRL+O, CTRL+X

bohh... I don't know if it works :-k

---

### Post by badiruz on 2006-03-13
hi :)

well to be honest  I did not touch my laptop working with ubuntu for a couple of days ... cause I had to work through the internet and I still have the problem ... the networking is still not working ... eventhough I have a hostname ... heh ... 

now here there is no guy who can see my laptop and see what the problem is ... and I am not capable yet to figure out the problem through the forums ... but I try to understand ubuntu through the messages already written here ... 

so guys ... thanks a lot for your help ... however I am still a freshman who may not able to tell the problem properly and hence solve the problem through the forums ... 

:(

well .. life is going on ...

---

### Post by badiruz on 2006-03-13
YOU WON'T BELIEVE THIS .... !!!!!!!!!

while I was writing the last message here .... my laptop was just re-starting ubuntu ... and now I have again access to the networking ... wooow .... 

I also followed the 

[http://ubuntuforums.org/showthread.php?t=141816&referrerid=75839](http://ubuntuforums.org/showthread.php?t=141816&referrerid=75839)

and tried it ... ... 

thanks ... .... I will keep always an I on these forums ... not to feel myself such desperate again, when facing a problem ... heh ... 

...b.:)

---

