---
title: "cannot access networking"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by IusedTObeSOMEONEelse on 2006-09-12
I am so new! I was messing around in networking and I do not know what I did but I cannot access Networking under systems. something is wrong with ethernet card and I cannot get online. I am on my windows machine now. I tried /etc/resolv.conf and I got message  denied access. can some one please guide me?

---

### Post by Najand on 2006-09-12
How did you try:
>  /etc/resolv.conf and you got message denied access?

---

### Post by IusedTObeSOMEONEelse on 2006-09-12
i used the terminal and not sudo. I just put in live cd and I am on the internet using live cd so I no it is a  program problem.

---

### Post by Najand on 2006-09-12
OK, let us see what is the problem. Cna you execute two commands:
```

$ netstat
$ ifcinfig

```
and copy paste the outputs here?

---

### Post by IusedTObeSOMEONEelse on 2006-09-12
ok, but please give me a couple of minutes as I have to pop live cd out and I'll be back on my windows machine and i'll have to type it all out. I do know that i was missing an address on the second command as I tried that command earlier. thanks , i'll be back in a moment!!

---

### Post by Najand on 2006-09-12
Sure... Take your time...

---

### Post by cjh on 2006-09-12
hi Najand,

on the subject of networking i have a small question. 
after an exhausting time getting the modem driver working, whenever i connect using the network settings app it stops the connection when i click "ok" and it closes.
net connection will not connect using KPPP and my connection comes up as loopback interface (lo). under the networking tool the two devices presented are "loopback interface (lo)" and "ethernet".  i did not have this problem with my first install of ubuntu 6.06 but i do know after i have re-installed the OS due to a mess I made when partitioning. 
funnily now with my new install i can also access my windows filesystem straight from the desktop which i couldnt do at all in the first install.

I do not understand. could you shed some light on the network difficulties?

v92 conexant internal modem. 

cjh

---

### Post by IusedTObeSOMEONEelse on 2006-09-12
ok w/ifcinfg it says command not found now with the other one can you tell me what wre looking for as it was a very long list. all said connected accept the first two lines and I am using two differant computers

---

### Post by YeahBuntu on 2006-09-12
Hi mustang .. sorry to pipe into your already troubled system.. do you have a thumb drive?  You could output the results of those commands to a file then copy that file to your thumbdrive take it to your windows compooper open it up copy and paste... walla .. :-\"

---

### Post by Najand on 2006-09-12
OK... It seems your system could not recognise your network card... How are you connected to the internet? Modem? ISDN? DSL? LAN?

---

### Post by Najand on 2006-09-12
> **cjh said:**
> hi Najand,

on the subject of networking i have a small question. 
after an exhausting time getting the modem driver working, whenever i connect using the network settings app it stops the connection when i click "ok" and it closes.
net connection will not connect using KPPP and my connection comes up as loopback interface (lo). under the networking tool the two devices presented are "loopback interface (lo)" and "ethernet".  i did not have this problem with my first install of ubuntu 6.06 but i do know after i have re-installed the OS due to a mess I made when partitioning. 
funnily now with my new install i can also access my windows filesystem straight from the desktop which i couldnt do at all in the first install.

I do not understand. could you shed some light on the network difficulties?

v92 conexant internal modem. 

cjh

Working on it... Can you wait for a short time, please?

---

### Post by IusedTObeSOMEONEelse on 2006-09-12
DSL but I cannot access networking inthe systems menue as well.

---

### Post by Najand on 2006-09-12
Then assuming you're using PPPoE, use this command:
```

sudo pppoeconf

```

---

### Post by cjh on 2006-09-12
sorry i shouldnt have used this post for my own question. i have started a thread here in regards to it if you are interested in helping:

[http://www.ubuntuforums.org/showthread.php?p=1489633#post1489633](http://www.ubuntuforums.org/showthread.php?p=1489633#post1489633)

thanks, cjh.

---

### Post by IusedTObeSOMEONEelse on 2006-09-12
ok I got-sudo: unable to lookup ubuntu via gethostbyname()

---

### Post by Najand on 2006-09-12
Hmm, so I think I know what is your problem now... 
Do you have root acount or you haven't made it yet?
1. If you have it, do 
```

su

```
If you don't have it use recovery mode;
2. Then set your hostname as something you like, for example MYHOST and run:
```

hostname MYHOST
gedit /etc/hostname /etc/hosts

```
in /etc/hostname write down your hostname if i is not the same as your hostname: i.e. MYHOST
in /etc/hosts check if you have the same hostname on the first line... If not, write it there...
3. Save both files... 
4. restart your computer now.

---

### Post by IusedTObeSOMEONEelse on 2006-09-12
First, I appreciate your help, now forgive my ignorance  but I'm not sure about root and how and where do I do recovery mode?

---

### Post by Najand on 2006-09-12
Recovery mode:
1 Boot-up computer
   2 If GRUB menu is hidden, press 'Esc' to enter the GRUB menu
   3 Select 
     Ubuntu, kernel 2.6.15-26-386 (recovery mode)
   4 Press 'Enter' to boot

---

### Post by IusedTObeSOMEONEelse on 2006-09-12
Iwas totaly lost in grub! Should I just go ahead and re-install? I would rather not but after I hit recovery mode selection I was lost. I'sorry for being  a little on the "not so bright" side abou tthis system, what next, I'll try to keep up](*,)

---

### Post by Najand on 2006-09-12
Hmm, no,,, there is no need to reinstall the whole thing...
Let us see...
If you have the Live CD... Let us use it...
Follow every step carefully...

1 Put the media in your cd-rom and boot your computer using it...
2 After a successful boot click on > Application -> Accessories -> Terminal to open a terminal
3 run ```
sudo su
```
4 run ```
cd /media
```
5 run ```
mkdir ubuntu
```
6 run ```
fdisk -l
``` to see which /dev/*** has the system "LINUX"
7 run ```
mount -t ext3 /dev/*** /media/ubuntu
(change /dev/*** with what you found in "fdisk -l" as LINUX)
```
8 if successful, run ```
gedit /media/ubuntu/etc/hostname
```
9 Write your hostname there and Save the file
10 run ```
gedit /media/ubuntu/etc/hosts
``` and check if you have the hostname at the first line of the file. If it was not avaiable, write it there.
11 Save
12 run ```
shutdown -r now
```

---

