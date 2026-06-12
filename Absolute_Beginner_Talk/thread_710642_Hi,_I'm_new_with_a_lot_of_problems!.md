---
title: "Hi, I'm new with a lot of problems!"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by James Haigh on 2008-02-28
Hi.
I am new to Linux, Ubuntu, this forum and installing OSs.

After discovering linux I liked it and planned to switch in about a month. However, my HD broke and I lost EVERYTHING back to november! Ouch!!! But on the bright side, a good time to switch!

I am very good at Windows XP but I don't like it. I self learnt to program. I am a quick learner and I will probably be helping with development in a few weeks. I am using XP now because I have lots of problems with Ubuntu. I would apprieciate it if I could get Ubuntu running smoothly in a few days.

_Problems_

Graphics:
The first problem I noticed on the Live CD was low resolution. This makes Ubuntu very difficult to use. The installer buttons were off the bottom of the screen! I did sucessfuly install it tho. After install, as Ubuntu starts it has the right res but once loaded it is bad again. I now know that many people have this problem so solving this could help many. My system is up to date. The driver for XP is not good, it causes stop errors so is it a problem with my driver? It is VIA/S3G UniChrome Pro IGP.

Wireless:
Cable networking is fine. I had to install a propietry driver for my broadcom wireless. I can view networks in range but can't connect. I think it is something to do with security. In XP it's easy, click connect and type the code.

Those 2 problems are why I am still using XP for internet. I am restarting all the time between the 2 OSs which is time consuming. The next problems are less ugent.

Feedback:
I am very good at giving constuctive feedback. If this would be useful to the Ubuntu community or developers then who do I contact? I would be happy to give feedback on the installation process from a beginers perspective. I want to take part and help in return.

Development:
The big attraction to Linux for me was that programs could be modified (Which I now know is named 'Open Source'). How do I begin? Do I need to install development software? How do I learn the language? I have seen bits of code and commands on some threads. What are these? What language? What language is the source code for Linux programs? I can't wait to use Ubuntu to the full!!!

Ok. They are the main ones. Thank you kind people for helping, I hope to be up to speed with Ubuntu, and helping others asap!

James.
:)

---

### Post by overdrank on 2008-02-28
[QUOTE=James Haigh;4424599]Hi.

Graphics:
The first problem I noticed on the Live CD was low resolution. This makes Ubuntu very difficult to use. The installer buttons were off the bottom of the screen! I did sucessfuly install it tho. After install, as Ubuntu starts it has the right res but once loaded it is bad again. I now know that many people have this problem so solving this could help many. My system is up to date. The driver for XP is not good, it causes stop errors so is it a problem with my driver? It is VIA/S3G UniChrome Pro IGP.

Wireless:
Cable networking is fine. I had to install a propietry driver for my broadcom wireless. I can view networks in range but can't connect. I think it is something to do with security. In XP it's easy, click connect and type the code.

[QUOTE]

Hi and welcome, this link may help with the garaphics
[https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)
What is the model of the wireless card? You can use the command in the terminal located under applications, accessories  ```
lspci
``` this will allow you to search for that model and find the solution. As for the commands this link may help
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
Good luck!

---

### Post by Origin415 on 2008-02-28
If you want to download the ubuntu source code, you can enable the source packages in System -> Administration -> Software Sources

Most Ubuntu programs (incuding the kernel) are written in C, with the rest a smattering of C++, python, perl, etc. If you are new to programming, there are a bunch of guides to various languages here:
[http://ubuntuforums.org/showthread.php?t=606009](http://ubuntuforums.org/showthread.php?t=606009)

---

### Post by oedha on 2008-02-28
maybe you can check this :==> [http://ubuntuforums.org/showthread.php?t=698205](http://ubuntuforums.org/showthread.php?t=698205)

---

### Post by James Haigh on 2008-03-01
Thanks overdrank.

The 'Using The Terminal' link was very useful. I now have a moderate understanding and know about 20 - 30 commands. How many commands exist? Is there a list? I could use man, info and --help to find out more about commands if I knew their names.

My wireless has fixed on its own! Strange... possibly after installing 6 new updates. I tried lspci:

```
james@james-laptop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0c.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

```
This will help with graphics I think. I tried that link but I don't know which driver. The screen res is 1280x800 but I can only get 800x600. This is not a problem on XP. My Ubuntu experience is break-even with XP. Otherwise Linux and Ubuntu are way way better than XP and Vista and I am pleased to have made the switch! (Using Ubuntu now.)

Thanks Origin415.

The link is useful. After research and some previous knowledge I concluded this:

I think C is a very old language that is efficient and good at background services and processing data. I think it is used on other OSs like Windows. I like C but don't want to learn it yet.

I think Python is easy to learn and good at GUIs and graphics. I have some skills in Visual Basic .net (also good at GUIs) and I think Python is equivalent to it. I like Python and want to start learning it.

I am not certain about these but I get an impression. Can you confirm them?

I have self-taught a few languages and so I am happy to learn more. In Add/Remove, Python (v2.5) is checked but how do I open in? It is not in the App menu.

I think there is a mentoring system. How do I get involved?

I have read that it is not good to practice on my own and make a new project. I should join a project. How do I do this?

oedha,

The solution to that thread was to get a new graphics card. That is not something that I can do because I can't afford it after laptop repairs and new HD.

Thanks all.

James.

---

### Post by y-lee on 2008-03-01
> I think Python is easy to learn and good at GUIs and graphics. I have some skills in Visual Basic .net (also good at GUIs) and I think Python is equivalent to it. I like Python and want to start learning it.

Python runs in a terminal, open a terminal and type

```
 python
```

Ctrl-d exits it :)


```
man python
```
 

gives you more information on using it in the command line. q exits the man page. Most commands in linux have a man page

```
man command
```

For most commands gives you some information. As does 

```
info command
```

You may also be interested in reading

```
info
```


as well as

```
man man  
```


and 


```
man bash
```

as well as

 ```
man apropos
```


have fun :)

---

### Post by James Haigh on 2008-03-03
Thanks y-lee, I now have all I need to self-teach python and the terminal.

Graphics:

Res is 800x600 (Too small) and Desktop effects could not be enabled. Can someone look at output of lspci (Above) and tell me which driver I need? This page has too many; I don't know which 1 I need.

[http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220]("http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220")

Thanks.

James.

---

### Post by wheredidrealitygo on 2008-03-03
After googling, apparently your graphics problem is common.

These may help:

You can download 
```
xserver-xorg-video-unichrome
unichrome
```

(two separate packages) from the program "Synaptic package manager", or


```
sudo aptitude install xserver-xorg-video-unichrome unichrome
```

from the terminal.

That may help a bit, if it says it can't find those specified packages, you may have to enable some extra repositories ([http://www.ubuntuguide.org]("http://www.ubuntuguide.org")).

Good luck!!

---

### Post by James Haigh on 2008-03-03
wheredidrealitygo, I tried that and it didn't work, thanks for trying tho.

As I only have 1 problem left I have started a new thread. I will still post solutions and links on this thread just in case some other newb reads it.

New thread:

[http://ubuntuforums.org/showthread.php?p=4447810#post4447810](http://ubuntuforums.org/showthread.php?p=4447810#post4447810)

Thanks all.

James.

---

