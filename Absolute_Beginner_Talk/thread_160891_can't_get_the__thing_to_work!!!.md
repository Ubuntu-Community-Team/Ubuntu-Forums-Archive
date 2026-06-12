---
title: "can't get the ******* thing to work!!!"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-04-15
This is the situation:
I have my ubuntu box connected to a wireless router via ethernet cable, and a windows notebook connected wirelessly to the router.
I tried lutrafobic's method from this thread: [http://ubuntuforums.org/showthread.php?t=91066]("http://ubuntuforums.org/showthread.php?t=91066"), but it didn't work.
I would like to share my * directory with my windows notebook.
how can i do this?!!!!!! ](*,)

---

### Post by John.Michael.Kane on 2006-04-15
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/)
[http://hr.uoregon.edu/davidrl/samba.html](http://hr.uoregon.edu/davidrl/samba.html)

---

### Post by user1397 on 2006-04-15
[quote=SD-Plissken][http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/")
[http://hr.uoregon.edu/davidrl/samba.html]("http://hr.uoregon.edu/davidrl/samba.html")[/quote]
Thanks SD-Plissken!
you've been really handy lately :D

---

### Post by John.Michael.Kane on 2006-04-15
Your welcome. I hope it helps.

---

### Post by user1397 on 2006-04-15
I know this sounds impulsive, but can somebody just tell me exactly what to do to set this up correctly? (no offense to you SD-Plissken) no links please

---

### Post by souki on 2006-04-15
which method did you use ?
"System -> Administration -> Shared Folders" ? or /etc/samba/smb.conf ?
do you have an error message ?
can you post your /etc/samba/smb.conf ?
can you look into the /var/log/samba/ folder and see if there is some error message ?

---

### Post by user1397 on 2006-04-15
[quote=souki]which method did you use ?
"System -> Administration -> Shared Folders" ? or /etc/samba/smb.conf ?
do you have an error message ?
can you post your /etc/samba/smb.conf ?
can you look into the /var/log/samba/ folder and see if there is some error message ?[/quote] I used the System -> Administration -> Shared Folders method. In my /var/log/samba folder, I found these two things:
1) "Unable to open printcap file /etc/printcap for read!"
2) "startsmbfilepwent_internal: file /etc/samba/smbpasswd did not exist. File successfully created."
I don't know if those mean anything but...

---

### Post by souki on 2006-04-15
the security model defaults to USER
so you have to create some accounts if you want your windows client to see your share
this is done with two steps:
1- create your linux account
2- create your samba accout

I don't know if there is a gui for that, the commands from a superuser terminal are :
```
useradd thewinuser
smbpasswd -a thewinuser
```

---

### Post by user1397 on 2006-04-17
[quote=souki]the security model defaults to USER
so you have to create some accounts if you want your windows client to see your share
this is done with two steps:
1- create your linux account
2- create your samba accout

I don't know if there is a gui for that, the commands from a superuser terminal are :
```
useradd thewinuser
smbpasswd -a thewinuser
```[/quote]
i'm sorry about my beginner-ness but i have absolutely no idea what you are talking about...

---

### Post by nalmeth on 2006-04-17
I never had this much trouble setting up samba.
Anyway, he means to open a terminal:
APPLICATIONS --> ACCESSORIES --> TERMINAL
and enter the given code in the terminal.
All I had to do was a 
sudo apt-get install samba
People are glad to help you here, but you should really try to help yourself as much as possible. Usually the howtos are step by step, and if you have a problem with a step, then it is a good idea to post for help.

---

### Post by user1397 on 2006-04-17
[quote=nalmeth]I never had this much trouble setting up samba.
Anyway, he means to open a terminal:
APPLICATIONS --> ACCESSORIES --> TERMINAL
and enter the given code in the terminal.
All I had to do was a 
sudo apt-get install samba
People are glad to help you here, but you should really try to help yourself as much as possible. Usually the howtos are step by step, and if you have a problem with a step, then it is a good idea to post for help.[/quote]
Will get back to you on this.

---

### Post by user1397 on 2006-04-17
[quote=nalmeth]I never had this much trouble setting up samba.
Anyway, he means to open a terminal:
APPLICATIONS --> ACCESSORIES --> TERMINAL
and enter the given code in the terminal.
All I had to do was a 
sudo apt-get install samba
People are glad to help you here, but you should really try to help yourself as much as possible. Usually the howtos are step by step, and if you have a problem with a step, then it is a good idea to post for help.[/quote]
Ahemmm...I'm not that much of a noob not to know where the terminal is located, a-thank you :cool:, but do you mean paste those exact commands or replace "thewinuser" with something?

---

### Post by nalmeth on 2006-04-17
I'm sorry if I was talking like a kindergarten teacher or something :???:
You'd be suprised how many times I have to tell someone where the terminal is. After all it is the Absolute Beginner's Forum.
Just follow the previous posters advice, copy and paste the lines (one command at a time). 
[I]Did you know? (Queue cheesy NBC music)
You can copy by highlighting text, and paste by pushing scroll button or left and right mouse buttons at the same time?
[/I]Good luck with your samba configuring, hopefully it doesn't take too much more trouble.
Sorry again for any apparent condescenion
EDIT:
The previous poster mentioned it had to be a superuser terminal?
If you want to follow his advice, before entering those commands, enter this
sudo -i
After giving your password, you will have admin priviledges for 15 minutes I think.
Or you can just put sudo in front of any command that requires higher priviledges.
EDIT #2:
Do you have a firewall setup on Ubuntu, this may cause problems. Reading over again, you didn't really say just what was wrong. From windows, just hit enter when prompted for username/password, if this is the prob.
When I setup my samba, all I did was install samba, and right-click on my Media folder, and tell it to share. It may be in properties or something like that, I'm unfortunatly on a windows PC right now.
I NEVER had to add this winuser thing.
I will be back on later in the day, and if you still have problems, I can show you my smb.conf.

---

### Post by user1397 on 2006-04-17
[quote=nalmeth]I'm sorry if I was talking like a kindergarten teacher or something :???:
You'd be suprised how many times I have to tell someone where the terminal is. After all it is the Absolute Beginner's Forum.
Just follow the previous posters advice, copy and paste the lines (one command at a time). 
[I]Did you know? (Queue cheesy NBC music)
You can copy by highlighting text, and paste by pushing scroll button or left and right mouse buttons at the same time?
[/I]Good luck with your samba configuring, hopefully it doesn't take too much more trouble.
Sorry again for any apparent condescenion
EDIT:
The previous poster mentioned it had to be a superuser terminal?
If you want to follow his advice, before entering those commands, enter this
sudo -i
After giving your password, you will have admin priviledges for 15 minutes I think.
Or you can just put sudo in front of any command that requires higher priviledges.
EDIT #2:
Do you have a firewall setup on Ubuntu, this may cause problems. Reading over again, you didn't really say just what was wrong. From windows, just hit enter when prompted for username/password, if this is the prob.
When I setup my samba, all I did was install samba, and right-click on my Media folder, and tell it to share. It may be in properties or something like that, I'm unfortunatly on a windows PC right now.
I NEVER had to add this winuser thing.
I will be back on later in the day, and if you still have problems, I can show you my smb.conf.[/quote]
Umm I pasted the commands and still my problem persists:
When in windows, in the network places, i click show workgroup computers, and only the windows computer is there, not the ubuntu computer.
I am using the firestarter firewall because i heard if you have one , samba is safe. if i have a router, is that the same as my firewall?

---

### Post by Randomskk on 2006-04-17
Your firestarter firewall may be interfering - check it is setup to allow Samba.
In linux, in a terminal, type "ifconfig" and look for the line with your IP address - this will look something like 192.168.0.5 - and then from windows, go start, run, //192.168.0.5 (or whatever your IP was), press enter and a window should open with the shared folders, or at least a box will open asking for a username and password.

---

### Post by user1397 on 2006-04-17
[quote=Randomskk]Your firestarter firewall may be interfering - check it is setup to allow Samba.
In linux, in a terminal, type "ifconfig" and look for the line with your IP address - this will look something like 192.168.0.5 - and then from windows, go start, run, //192.168.0.5 (or whatever your IP was), press enter and a window should open with the shared folders, or at least a box will open asking for a username and password.[/quote]
Thanks for the replies everybody.
After I typed my ip address into the run and pressed enter, i just got a "please make sure you typed it in correctly " type message, so I rechecked and rechecked, and everything is the way its supposed to be, but nothing happens?! ](*,)

---

### Post by Randomskk on 2006-04-17
Check samba is actually running on your linux machine, and check again that the firewall is setup - try turning it off and see what happens.

---

### Post by user1397 on 2006-04-17
[quote=Randomskk]Check samba is actually running on your linux machine, and check again that the firewall is setup - try turning it off and see what happens.[/quote]
In system monitor, I did not see any samba process running.  how can i make it run?

---

### Post by Randomskk on 2006-04-17
Try this:
```
sudo /etc/init.d/samba start
```

---

### Post by user1397 on 2006-04-17
[quote=Randomskk]Try this:
```
sudo /etc/init.d/samba start
```[/quote]
Ah! Now the windows box recognizes my computer, but when i try to click on it, it's telling me i do not have enough permissions to access it. i'm sure this is configurable in samba but i don't know exactly how to do it!

---

### Post by Randomskk on 2006-04-17
Indeed, I'm fairly sure this is configurable in your samba smb.conf, and you may want to try reconfiguring it a few times. I remember getting mine to work properly was a bit annoying, you may have to login as your linux user on the windows system to see anything.

I'm afraid I can't help much with the config file, though.

---

### Post by user1397 on 2006-04-17
[quote=Randomskk]Indeed, I'm fairly sure this is configurable in your samba smb.conf, and you may want to try reconfiguring it a few times. I remember getting mine to work properly was a bit annoying, you may have to login as your linux user on the windows system to see anything.

I'm afraid I can't help much with the config file, though.[/quote]
Okay, well thanks for all the replies and help

---

