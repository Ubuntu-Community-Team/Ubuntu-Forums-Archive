---
title: "The Ubuntu 'White Screen of Death.'"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-12-05
I have this frequent issue where my screen will go white (kind of) and the system requires a power off re-boot, as NOTHING responds. I was getting this upon entering or leaving a full screen 'netpanzer' session, but now it is beginning to happen at other times. I just had it happen at the last boot-up. 

Not sure what I should do, but the version I am using IS 6.06 LTS. I'm really banking on the 'LTS' part!
:D

---

### Post by nickburns on 2006-12-05
Can you and what do you get if it happens and you do a alt+ctrl+F1, if you get a termainal, login and type:

ps -ef 

of

top

and see what thread may be taking up all the resources.

---

### Post by Papa-san on 2006-12-05
I'll check it next time it happens...

Type those at once? Or one at a time...

---

### Post by Papa-san on 2006-12-05
Alt + Ctrl + F1 got me nowhere. I left it alone for five minutes, but it didn't go to terminal... (Didn't go to anything)

---

### Post by nickburns on 2006-12-05
ps -ef 

will show you all the threads/applications that are running in no particular order.  It numbers the application and shows the path from where they are running and the amount of resources they use.  This is one option.  Or if you type

top

It posts the program that is using the most resources on the top of the list.

Either will help us know if you just have an application running away, taking all the resources.

You aught to go to a terminal (Applications >> Accessories >> Terminal)  and run the top anytime and see what it does.  BTW to get out of top us CTRL+C

good luck and let us know what you find.

---

### Post by jpkotta on 2006-12-06
> **nickburns said:**
> ps -ef 

will show you all the threads/applications that are running in no particular order.  It numbers the application and shows the path from where they are running and the amount of resources they use.  This is one option.  Or if you type

top

It posts the program that is using the most resources on the top of the list.

Either will help us know if you just have an application running away, taking all the resources.

You aught to go to a terminal (Applications >> Accessories >> Terminal)  and run the top anytime and see what it does.  BTW to get out of top us CTRL+C

good luck and let us know what you find.

I'd try to ssh into it when it freezes, if you can.  Many times I've had a hard X server lockup, but I can still login remotely and kill X.

---

### Post by Papa-san on 2006-12-06
> **jpkotta said:**
> I'd try to ssh into it when it freezes, if you can.  Many times I've had a hard X server lockup, but I can still login remotely and kill X.

OK... I'd like to try this, as the other has failed to get me to a login.  I have tried to do it several times, and my system just does not respond. It doesn't seem to respond to anything... How do I?

EDIT: I had it crash and then typed in the ctrl+alt+ f1, nothing happened. I figured I'd give it some time, so I had breakfast. I came back, and no change. Well, not exactly true... I have tried to reboot three times, and it just goes to that lock up state just as my desktop should appear...

---

### Post by Papa-san on 2006-12-06
I had to let it sit for a while to cool down, I suppose. I am using it again now. This is really a huge concern, and seems to be getting worse...

I would like to get this resolved before I cook my computer, as I don't have the money to replace it...

---

### Post by deadgobby on 2006-12-06
I wounder if your monitor may be going bad. If you have a CRT type monitor, let it cool down for about an hour. If you have any thing on top of your monitor. Take it off of it. It may be getting to hot and causing it to fail. All so check your monitor connection. If you have a vid card. Like for sample a Nvid card with a cooling fan. Check to see if the fan is working. If it not not kicking on. The card my be on its way out. This is just a K.I.S.S. mythod here ( Keep It Simple Stupid )
Gobby

---

### Post by Papa-san on 2006-12-06
Naw... It's a Dell Lattitude laptop. LCD screen...

---

### Post by Kieranties on 2006-12-06
might wanna just use "q" to get out of top.  As it is the quit option

---

### Post by jpkotta on 2006-12-06
To ssh into the machine, you need another machine on the same network (it can be any OS).  Install openssh-server, and start it with ```
/etc/init.d/ssh start
```  On your remote machine, install openssh-client or PUTTY (Windows).  Then on remote host do ```
ssh jpkotta@192.168.0.5
``` Of course you would use your username and the ip address of the machine you're trying to log into.

More info on the wiki and google.

---

### Post by deadgobby on 2006-12-06
AH HAA Here is a link that would fix that problem. Next time be a good person and give the specs on your system.
[http://www.math.dartmouth.edu/~sarunas/D620F6.html](http://www.math.dartmouth.edu/~sarunas/D620F6.html)
See X server

---

### Post by Papa-san on 2006-12-06
I only WISH it was that system!!! LOL


mines about four years old.. 1 gig P3m processor 256k ram. Video card is a  Radeon Mobility M6 LY.

---

### Post by Papa-san on 2006-12-06
Trying to open ssh on my ubuntu box, I get:```
john@ubuntu:~$ /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server... Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key

```And:```
john@ubuntu:~$ sudo /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server...                               [fail]

```

---

### Post by Papa-san on 2006-12-06
Finally got to use this thing on the fourth re-boot...

I really hope I don't have to re-install. I am getting very, VERY tired of needing to do that with this OS... It takes about four hours of messing with stuff to get my wireless working after that. The funny thing there is that the same process doesn't work the same way twice.

Any real resolution would be nice. I really would like to have a nice, stable, usable computer.
:-#

---

### Post by jpkotta on 2006-12-06
> **Papa-san said:**
> Trying to open ssh on my ubuntu box, I get:```
john@ubuntu:~$ /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server... Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key

```And:```
john@ubuntu:~$ sudo /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server...                               [fail]

```

Try ```
sudo ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key
```

Also, ```
sudo /usr/sbin/sshd -t 
```

It would be very good if we could ssh into the machine after the crash, it will be much easier to figure out what is wrong.

---

### Post by Papa-san on 2006-12-07
OK... Managed to get the key generated. However, I still get the same errors as above when trying to start it on the unix box.

When I put in the IP while in Putty on the windows box, It opens with a non-blinking green cursor, and doesn't accept any keystrokes.

I must be doing something wrong. 

The first time I ran ```
/usr/sbin/sshd -t
```
it seemed to work, but the next time I tried, it gave me this:```
john@ubuntu:~$ sudo /usr/sbin/sshd -t
Could not load host key: /etc/ssh/ssh_host_dsa_key

```

---

### Post by jpkotta on 2006-12-07
> **Papa-san said:**
> OK... Managed to get the key generated. However, I still get the same errors as above when trying to start it on the unix box.

When I put in the IP while in Putty on the windows box, It opens with a non-blinking green cursor, and doesn't accept any keystrokes.

I must be doing something wrong. 

The first time I ran ```
/usr/sbin/sshd -t
```
it seemed to work, but the next time I tried, it gave me this:```
john@ubuntu:~$ sudo /usr/sbin/sshd -t
Could not load host key: /etc/ssh/ssh_host_dsa_key

```

That's really weird.  You just generated the key, it said it was OK, and now it's not.  Is the time stamp on the file newer than it should be?  Did something change it?  AFAIK, those key files should never change (except when you do it deliberately).  Try a ```
sudo apt-get --purge remove openssh-server
``` and reinstall.  I've never even had to generate the keys by hand, so I don't know why this isn't working.

You could also try installing a telnet server, that might be easier to do, and we can still log in and look at the machine (or if we can't, then we probably can't with ssh either).

```
sudo aptitude install telnetd
```

I just tried this, and it required nothing else.  I could telnet to my machine immediately (it starts the daemon on demand).

---

### Post by Papa-san on 2006-12-07
I have telnetd installed, and I have a live session of ubuntu running on the XP box (as I cannot figure out how to configure the ssh stuff on that comp.) I am going to let it finish updating. What is the recommended method of trying to:

1- log in from that comp to see if I even have the ability to connect from it?

2- If the above works, what do I need to do to read information when I make this one crash?

OK... I can ping my ubuntu box from the XP/(ubuntu) location. I am not able to aptitude install telnetd, however. I'm not sure what to do... Ive said it before, and I'll say it again: 

Papa-san's not the brightest crayon in the box! :rolleyes:

---

### Post by jpkotta on 2006-12-07
You don't need telnetd on the remote machine, just "telnet" (the client).  Telnet should also be available on a Windows machine, just start the command prompt and run "telnet".  

Logging in: 
Run telnet
Inside telnet: open 192.168.0.5 (or whatever your IP is)
You should get a login prompt, where you type your username and passwd.

---

### Post by Papa-san on 2006-12-07
This is so stinking frustrating!!!

I can ping the machines from each other, but cannot get a telnet connection. Ubuntu can't find a route to the XP box, and the XP box can't find anything at port 23 on my ubuntu box....

Grrrr.
 Is there a way to edit my 'open ports'? Maybe opening 23 on the ubuntu box?
Still I am not sure this will do it either...

---

### Post by jpkotta on 2006-12-07
An open port means that a) nothing is blocking the port and b) something is listening on that port.  If you have no firewall, it should just work; mine started up telnetd automatically when I tried to log in (the "internet daemon" inetd listens on port 23 and starts telnetd).  I have tried this from an XP machine.

Is anything else on your machine out of whack?  Is all this trouble another manifestation (like the lock ups) of a deeper problem?

Maybe the best route is reinstall.  It would be nice to know what's wrong though.

---

### Post by Papa-san on 2006-12-08
I don't know... I have tried it. All the research I have done says it should work just as you say it does. 

I don't know if there is a deeper problem. I know that for some reason samba didn't install correctly. Something called keno wouldn't install at all either. It (keno) finally did, but I had to run my update manager several times for it to do so. 

I am pretty convinced that this OS is so bodgered together that many things just don't mesh. God knows all those brilliant folks who develop this stuff do the best they can. I would never be able to develop something as simple as, like, 'Pong' or something. 

I hope yet another re-install might make the difference, but I doubt it will, as it hasn't before. 

Anyways, I appreciate all your help, and if you have a brainstorm, please feel free to offer any suggestions! :D

---

### Post by Papa-san on 2006-12-09
One other thing...

If I have uninstalled samba, why would my firestarter say that there has been a hit from samba from a different IP on my network than any set by my router?

---

### Post by dmizer on 2006-12-09
well, if you have firstarter turned on, that's what's blocking your telnet and ssh attempts.  you'll have to open those ports.

i might suggest a memory test.  when grub loads (and start's it's countdown from 3) hit the esc key to enter into the grub menu, and do the memtest86+

let that thing run for several hours to cycle through the complete test at least 3 times (maybe run over night?) and see if it catches errors.  you might just have a bad memory card.

next thing i'd suggest looking at is sound configuration.

---

### Post by Papa-san on 2006-12-09
> **dmizer said:**
> well, if you have firstarter turned on, that's what's blocking your telnet and ssh attempts.  you'll have to open those ports.

I have attached a screenshot that shows what my firestarter 'policy' is. I assumed it was correct... Our network is called 'home', and the assigned IP's are as shown. If this is configured wrong, let me know. If I need to do something different, I'll need to know what and prolly how... :rolleyes: 

I am willing to pursue any course at this point, as this is the first time I have had my wireless able to connect automatically to whichever AP I happen to be near... (Home, School, library, McDonalds, etc...) My drives all work and mount without issues. My mice work without issues... Etc., Etc....

I have my resolution turned down about halfway, and that has reduced the number of lockups, but not eliminated them. 

I will do the memtest this afternoon, and I'll post the results!

Thanks!

---

### Post by jpkotta on 2006-12-09
If you have a NAT router between you and the internet, just turn the firewall off, you don't really need it.  If ssh and telnet still don't work, then I don't know.  You can re-enable the firewall (because it is good to have, just not absolutely necessary) later after we have figured out why the thing is crashing.

---

### Post by Duck2006 on 2006-12-09
Then you may need a cooling pad for your system

---

### Post by Papa-san on 2006-12-14
I had to reboot five times to get my desktop. It had been off for over a day, so it's not a heat issue, I don't think...

I have tried all I can to telnet. I don't understand it. I thought firestarter was only a GUI for my IPtables... Does it actually 'firewall'? I am going to try uninstalling it and see if that helps.

---

### Post by rlozano on 2006-12-14
i think your CPU is getting high temp and its fan is not working 100% as it should be to cool down your system. it happened to me already in one of my laptops (toshiba). i have to get the help of an extra cooling to make it work continously.

---

### Post by LookTJ on 2006-12-14
You know ssh's port is 22, not 23

try port 22 then ssh into it.

---

### Post by Papa-san on 2006-12-14
> **Taylor said:**
> You know ssh's port is 22, not 23

try port 22 then ssh into it.

I thought so, but don't know how to change the ports...

---

### Post by jpkotta on 2006-12-16
No need to uninstall Firestarter.  Just disable it.  It is just a frontend for iptables, and iptables is your firewall.  If you disable Firestarter, it stops iptables from functioning, making everything much easier to work with.  You won't have to worry about "changing ports".  You can reenable Firestarter later.

---

### Post by Papa-san on 2006-12-27
One of the times I logged on to this site, I actually saw that I had a private message waiting for me. When I went there, I saw that it had been received almost a month ago. The writer had sent me this:```
My girlfriend has a Dell Inspiron 4100 with the M6LY card which also happens to be the first laptop I installed Ubuntu on. It worked out of the box with a few tweaks (Breezy then Dapper). What I would probably check is your xorg.conf and perhaps reconfiguring it:

Code:

sudo dpkg-reconfigure xserver-xorg

and setting the following options:

- Kernel framebuffer device NO (in your xorg.conf this option should appear as "false")
- 16 bit (instead of the default 24-bit selection)

Restart X and see if you have any improvement. PPRacer plays at acceptable rates for the card (and age of the laptop).

HTH
``` in /etc/X11/xorg.conf I didn't see anything like 'kernel framebuffer' so nothing changed there, but upon changing the 24 bits to 16 bits (all instances) my comp no longer locks up. I still get the clutter on the buttons, but this is tolerable... Thanks HTH!

---

