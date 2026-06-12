---
title: "How to login as root?"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by Mr.X on 2006-02-15
Ok, this may be the stupidest ever question, but how do i login as root? I'm trying to setup ICS (internet connection sharing) with linux as the main, and it says i need to be logged in as root for a few commands.

Thanks,
X

---

### Post by heimo on 2006-02-15
Use sudo
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Mr.X on 2006-02-15
Thanks for fast reply, the guide said I cant use sudo. :confused: 

Here is a link:
[http://ubuntuforums.org/showthread.php?t=91370&highlight=internet+connection+sharing](http://ubuntuforums.org/showthread.php?t=91370&highlight=internet+connection+sharing)

---

### Post by anirban.sam on 2006-02-15
sudo passwd root will let you su to root, but you can do everything with sudo

---

### Post by heimo on 2006-02-15
[quote=Mr.X]Thanks for fast reply, the guide said I cant use sudo. :confused: 

Here is a link:
[http://ubuntuforums.org/showthread.php?t=91370&highlight=internet+connection+sharing]("http://ubuntuforums.org/showthread.php?t=91370&highlight=internet+connection+sharing")[/quote]

Well, it could be done using sudo, but at least one step should be changed a bit. Instead you can run *sudo -i *at the beginning and then use the instructions as is.

---

### Post by Mr.X on 2006-02-15
Ok, thanks guys ill give it a try!
:p

---

### Post by Mr.X on 2006-02-15
OK, it wouldnt work in Terminal1 (Or whatever its called - CTRL+ALT+F1), so i went Applications>System>Terminal, I did the sudo passwd root , said new UNIX password, so i put my default one, and the sudo -i [command, such as ifconfig ethX ip) wont work, says permission denied.. I know i can change my IP in the networking etc..

Lol, this is kinda being a pain I know.
P.S: I can "see" my windows computers in the main networking screen.

---

### Post by heimo on 2006-02-15
As you already set the root password, you should now be able to run
```
su
``` and enter the password you gave using sudo passwd. (anirbans' and my instructions were alternatives, not complementary)

---

### Post by Mr.X on 2006-02-15
[QUOTE=heimo]As you already set the root password, you should now be able to run
```
su
``` and enter the password you gave using sudo passwd. (anirbans' and my instructions were alternatives, not complementary)[/QUOTE]
Ok, thanks for all your help, heimo! :) 

I did the su, the my password i set, but the when i type in the commands it just goes to a new line without saying anything, and doesnt change my IP etc.

I'll keep trying though, thanks a bunch!

edit: here is a picture, the main terminal1 does the same thing.. so here is just a little screenshot:
[http://img128.imageshack.us/img128/7830/terminal16gw.png](http://img128.imageshack.us/img128/7830/terminal16gw.png)

---

### Post by heimo on 2006-02-15
[quote=Mr.X] but the when i type in the commands it just goes to a new line without saying anything, and doesnt change my IP etc.[/quote]

Old unix philosophy, no news is good news. If there's no erros, it worked. If you have any problems with some specific step, just ask away.

---

### Post by Mr.X on 2006-02-15
[QUOTE=heimo]Old unix philosophy, no news is good news. If there's no erros, it worked. If you have any problems with some specific step, just ask away.[/QUOTE]
Ok, ill type them all out then go to windows computers and try!
And thats a good saying :-D

---

### Post by Mr.X on 2006-02-15
7. Add the line "net.ipv4.ip_forward = 1" to /etc/sysctl.conf

# gedit /etc/sysctl.conf

i cant add in any lines, since its read only.. whats wrong ;)?

edit: nvm, i figured that step out.
going to reboot now :-D

---

### Post by GeirG on 2006-02-15
[QUOTE=anirban.sam]sudo passwd root will let you su to root, but you can do everything with sudo[/QUOTE]

"sudo su -" would be an alternative to setting a (potentially weaker) root password.

---

### Post by Mr.X on 2006-02-15
Ok, now the other computers (windows), "see" the site, but just gets stuck on site loading. :-k

---

### Post by heimo on 2006-02-15
[quote=Mr.X]Ok, now the other computers (windows), "see" the site, but just gets stuck on site loading. :-k[/quote] To be more specific, you mean that loading some website in browser doesn't work, or works half-way? No error messages? Can you ping outside world (from Windows), for example:
```
ping www.ubuntu.com
ping 82.211.81.166
```

Have you set the gateway for Windows (should be the ip address of the internet sharing Ubuntu box)?

---

### Post by Mr.X on 2006-02-15
[QUOTE=heimo]To be more specific, you mean that loading some website in browser doesn't work, or works half-way? No error messages? Can you ping outside world (from Windows), for example:
```
ping www.ubuntu.com
ping 82.211.81.166
```

Have you set the gateway for Windows (should be the ip address of the internet sharing Ubuntu box)?[/QUOTE]

Yes, the IP is set to the main ubuntu box, was that way when windows was on this machine.
It can ping [www.ubuntu.com](www.ubuntu.com) (with a valid ping rate as well), and it can "see" the other 2 computers that are on - ill configure the other 4 later.
Net still wont load up, it can see google.com just not load.

---

### Post by heimo on 2006-02-15
Could you send output (of relevant parts) of these commands:
```
route -n
sudo iptables -L

``` 

It could also help if you can check if the windows box can connect to any other kind of service - ftp, instant messaging - what-ever.

EDIT: You can hide ip addresses with xxx.xxx.xxx.xxx, yyy.yyy.yyy.yyy or similar, if needed.

---

### Post by Mr.X on 2006-02-15
[http://img291.imageshack.us/img291/6798/ub19ph.png](http://img291.imageshack.us/img291/6798/ub19ph.png)
there.

---

### Post by heimo on 2006-02-15
Did you configure firewall using firestarter? I believe there's an option to enable internet sharing somewhere in firestarters menus (or setup wizard). Not sure if that's actually needed after the instructions you followed, but there may be some firewall rule preventing access. That's my best guess.

I'd probably just stop the firewall for a moment, repeat the iptables command in the instructions and retry from windows. If that works, the problem is some of those rules which firestarter has configured (it's the same net filter / firewall that can be configured using iptables).

---

### Post by Mr.X on 2006-02-15
[QUOTE=heimo]Did you configure firewall using firestarter? I believe there's an option to enable internet sharing somewhere in firestarters menus (or setup wizard). Not sure if that's actually needed after the instructions you followed, but there may be some firewall rule preventing access. That's my best guess.

I'd probably just stop the firewall for a moment, repeat the iptables command in the instructions and retry from windows. If that works, the problem is some of those rules which firestarter has configured (it's the same net filter / firewall that can be configured using iptables).[/QUOTE]

Im kind of a newbie to linux, ive never ran firestarter before. Was reading a guide so ill try that :-k

---

