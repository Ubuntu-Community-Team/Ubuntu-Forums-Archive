---
title: "BT Voyager not being found on Wireless"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by Feldoon on 2006-05-28
Quick info:-
Yes, I'm new to Linux, but I wanna learn.
Using Kubuntu Dapper (6.06) as one of two OSs on my laptop.
Router for broadband is a BT Voyager 2091. It's wireless.

My problem is that whilst using Kubuntu, I can't "see" my wireless router. I can "see" the other connections, but not my own. When I first start the wireless software (name escapes me, sorry. Default Kubuntu one though), it comes up with a message that there may be restrictions and that to possibly solve it would be to use 'sudo'.

I know that sudo is used in command lines for ubuntu, when the gnome GUI didn't want to work for me.

So, I am presuming that I should be able to do something to get access to my router through command line. However, being a linux newbie, I have no idea how to do it.

Could anybody give me further instructions? Possibly even a different method?

---

### Post by popkid on 2006-05-28
Heya, when you say you can see other connections, do you mean other wireless networks in range? in other words do you have wireless working on your machine but you can't connect to your router.

Do you have your wireless essid hidden on your router?

If you type:

iwlist scan

at a command prompt, what does it return?

pK

---

### Post by Feldoon on 2006-05-28
I can see other connections within range just as on Windows. Except for my one.

And I'm not sure. It's my parents' connection, I just 'jack it. 

And that command got the following result
```
ath0      Scan completed :
          Cell 01 - Address: 00:30:F1:FF:6E:D8
                    ESSID:"belkin54g"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=17/94  Signal level=-78 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:0F:B5:B0:67:48
                    ESSID:"NETGEAR"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=5/94  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:11:50:35:C1:D5
                    ESSID:"belkin54g"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=7/94  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:11:F5:8A:52:3F
                    ESSID:"wicksfamily"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/94  Signal level=-72 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
```
Neither of those four are mine.

Another thing that may be worthy of note is that my one and only user (as far as I am aware) has no root access. And I can't give myself root access, because I've not got the permissions. *facepalm*

---

### Post by popkid on 2006-05-28
Crikey... you've enough wirless networks around haven't you!

In ubuntu, the default is for there to be no root user, to execute a command "as root", you type sudo before the command, it will then ask you for your password, (not the root password, just the one you log in with) and execute it.

not sure why you wouldn't be able to see the right network in this case since it sees the other ones... you've got me stumped, sorry! It is definitely switched on at the moment? (I know its a dumb question but I'm struggling to think of other reasons you wouldn't be able to find it)

pK

---

### Post by Feldoon on 2006-05-28
Well, my laptop dual boots and this is windows. So yah, kinda does work.

And I have no idea how to execute programs other than clicking them, let alone using the sudo command. (Well, I know how to use the sudo command, s'not that difficult.). Certain times when it asks for the root password though, I give mine and it doesn't accept it.

And I looked at my user and the secondary groups it is in, and "root" isn't one of them, yet "root" exsists as a user group. =\

---

### Post by popkid on 2006-05-28
[QUOTE=Feldoon]Well, my laptop dual boots and this is windows. So yah, kinda does work.

And I have no idea how to execute programs other than clicking them, let alone using the sudo command. (Well, I know how to use the sudo command, s'not that difficult.). Certain times when it asks for the root password though, I give mine and it doesn't accept it.

And I looked at my user and the secondary groups it is in, and "root" isn't one of them, yet "root" exsists as a user group. =\[/QUOTE]

Ok.... how many wireless networks can you see in windows? more than 4? are you certain that none of the 4 listed in ubuntu are the right one?

on the root issue, check out the following:

[https://wiki.ubuntu.com/RootSudo?action=show&redirect=SudoRoot]("https://wiki.ubuntu.com/RootSudo?action=show&redirect=SudoRoot") 

it explains it better than I can!

pK

---

### Post by Feldoon on 2006-05-28
With the wireless networks, I can see them in windows, however Kubuntu tends to pick them up better. =/

And I'll look at that tomorrow. I'm tired and irritable now. Thanks for your help though!

Anybody else?

---

### Post by popkid on 2006-05-28
[QUOTE=Feldoon]With the wireless networks, I can see them in windows, however Kubuntu tends to pick them up better. =/

And I'll look at that tomorrow. I'm tired and irritable now. Thanks for your help though!

Anybody else?[/QUOTE]

Ok, sorry couldn't be more help,

pK

---

