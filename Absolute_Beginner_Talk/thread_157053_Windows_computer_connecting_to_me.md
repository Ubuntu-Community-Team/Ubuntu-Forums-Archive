---
title: "Windows computer connecting to me"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by shador on 2006-04-08
I have a problem with sharing files on my computer with windows user. In wondows you can just type in the ip address of the user you want to connect to and you reach him. When I tried to connect to my ubuntu computer this way i came to a login screen. My login and pass for ubuntu didnt work. So how can i fix this?

---

### Post by renzokuken on 2006-04-08
look into using something called "samba"

---

### Post by Abhi Kalyan on 2006-10-20
Check the thread given below, lot of activity happening here regarding your problem, probably this might help us all
Cheers!!!
"connecting linux to a windows network"

---

### Post by sYs^ on 2006-10-20
just type 

sudo gedit /etc/samba/smb.conf

and change 
```
;   security = user
```to
```
security = share
```I hope it'll help, I'm not sure about my memories :D

don't foget to restart samba: **sudo **[SIZE=-1]**/**[B]etc/init.d/smbd restart
[/B][/SIZE]

---

### Post by Abhi Kalyan on 2006-10-20
Hi trying to follow your instructions 
Am using drapper drake 6.06
but
"sudo /etc/init.d/smbd restart"
returns
"command not available.
tryiong to install everything having samba in its name through add/remove
Is this the right thing to do?

---

### Post by Abhi Kalyan on 2006-10-20
this
sudo gedit /etc/samba/smb.conf
did work (i.e.) the change was made.

---

### Post by Abhi Kalyan on 2006-10-20
DUDE THANK YOU!!!!!
am Sooooo Happy
Thank you
Am able to access the share from my windows system, Feel like givin a hug to you
THANK YOU
note: am so happy that am actualy jumping and screaming!!!

But still not able to access shares from windows system!!!

---

### Post by sYs^ on 2006-10-20
Not at all! :p

note: You mean access shares on Windows XP using Ubuntu?

---

### Post by Abhi Kalyan on 2006-10-24
The pleasure's mine sYs^ - thanks to you and people like You am hoping to convert 150 people from windows to Ububtu
It was the other way round- sYs^
1. I wanted to access files from a windows 2003 server
2. Now i can open files from ubuntu system
3. today could connect to windows server ( am able to only use ip address and not names-dont knwo why, Could you help Please?)

---

