---
title: "Applications won’t start"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by ekka on 2007-01-24
Hi all

My problem is somewhat weird; I am unable to understand as what could be the problem. 

When I start my system I could only use (start any application like Firefox, Terminal etc.) it for the first couple of minutes then suddenly without any apparent reason or any visual indication of such no application would start. If for example I click the firefox the task bar shows ‘Starting Firefox’ for a couple of seconds and then nothing would come up. I couldn’t even open the Terminal to start any application and alt+f2 wouldn’t start it either.
I am using Edgy on an Acer Laptop with 1GB RAM, Intel 945GM graphic card and using 915resolution to get the 1280X800 resolution.

Thanks

---

### Post by Pobega on 2007-01-24
Wow, that's akward. I get this sometimes too, but it's not until 48h of uptime. Well, is anything eating at your system resources? You might want to make sure  that nothing is using up your resources, because that would be the first thing I would do if I were in your shoes.

---

### Post by apjone on 2007-01-24
> **ekka said:**
> Hi all

My problem is somewhat weird; I am unable to understand as what could be the problem. 

When I start my system I could only use (start any application like Firefox, Terminal etc.) it for the first couple of minutes then suddenly without any apparent reason or any visual indication of such no application would start. If for example I click the firefox the task bar shows ‘Starting Firefox’ for a couple of seconds and then nothing would come up. I couldn’t even open the Terminal to start any application and alt+f2 wouldn’t start it either.
I am using Edgy on an Acer Laptop with 1GB RAM, Intel 945GM graphic card and using 915resolution to get the 1280X800 resolution.

Thanks

when you go in open a terminal first and leave it open. use the system until the applications stop opening. Now in the terminal type the name of the application and press return. This way you should get some out put that will atleast give you an idea of what is wrong

---

### Post by ekka on 2007-01-24
> **Pobega said:**
> Wow, that's akward. I get this sometimes too, but it's not until 48h of uptime. Well, is anything eating at your system resources? You might want to make sure  that nothing is using up your resources, because that would be the first thing I would do if I were in your shoes.

I am not sure of it. But the system is not ‘freezing’ its just that no applications would start. And also when I click the shutdown icon, the ‘shutdown’ and ‘restart’ options are missing. I have to log out first and then restart. Can I suspect some problems with X?

---

### Post by ekka on 2007-01-24
> **apjone said:**
> when you go in open a terminal first and leave it open. use the system until the applications stop opening. Now in the terminal type the name of the application and press return. This way you should get some out put that will atleast give you an idea of what is wrong

Well I am able to use the ‘alt+f2’ to start a application, but nothing would come up!

---

### Post by Pobega on 2007-01-24
> **ekka said:**
> Well I am able to use the &#8216;alt+f2&#8217; to start a application, but nothing would come up!
A terminal gives output for problems; For example, if I tried running a KDE app through Alt+F2 it just wouldn't work. But if I tried doing it through the terminal the terminal would tell me **exactly** what failed (No Qt libraries installed). So if you try to run it through the terminal, the terminal would (most likely) tell us what the problem is.

---

### Post by ekka on 2007-01-24
Thanks Pobega

I am not sure if used the terminal to start any applications. Will give it a try.

Thanks for the Help.

---

### Post by ekka on 2007-01-24
> **apjone said:**
> when you go in open a terminal first and leave it open. use the system until the applications stop opening. Now in the terminal type the name of the application and press return. This way you should get some out put that will atleast give you an idea of what is wrong

Hi apjone

As you said I kept the terminal open to start the applications, the error is not same for all the applications. Below are the details.

```
$firefox
(firefox-bin:6559): Gtk-Warning **: cannot open display
```

```
$ktouch
Ktouch: cannot connect to X server :0.0
```

```
$gaim
(gaim:6699): Gdk-CRITICAL **: gdk_display_get_name: assertion ‘GDK_IS_DISPLAY (display)’ failed
Gaim 2.0.0 beta 3.1
** (gaim:6699): WARNING **: cannot open display: unset
```

Any idea what is wrong with the system?

Thanks

---

### Post by apjone on 2007-01-25
> **ekka said:**
> Hi apjone

As you said I kept the terminal open to start the applications, the error is not same for all the applications. Below are the details.

```
$firefox
(firefox-bin:6559): Gtk-Warning **: cannot open display
```

```
$ktouch
Ktouch: cannot connect to X server :0.0
```

```
$gaim
(gaim:6699): Gdk-CRITICAL **: gdk_display_get_name: assertion &#8216;GDK_IS_DISPLAY (display)&#8217; failed
Gaim 2.0.0 beta 3.1
** (gaim:6699): WARNING **: cannot open display: unset
```

Any idea what is wrong with the system?

Thanks

in a terminal type

```

xhost +
/usr/bin/firefox

```

and see what you get. It looks like for some reason that your application can not connect to Xserver. xhost + allows any one ( anyone includes remote people who can access your box) to launch applications to the graphical desktop. Its a strange one. You might want to create a new user and try it normally as them.

---

### Post by ekka on 2007-01-29
I am still clueless, is there any way to reconfigure the x? Do I need to reinstall Ubuntu?:confused:

---

### Post by jvc26 on 2007-01-29
> **ekka said:**
> I am not sure of it. But the system is not ‘freezing’ its just that no applications would start. And also when I click the shutdown icon, the ‘shutdown’ and ‘restart’ options are missing. I have to log out first and then restart. Can I suspect some problems with X?

When I lost my start and restart options I reinstalled the OS. I still am none the wiser why they vanished - if anyone can give us a clue that would be cool as I like to understand what goes wrong with things. If you have a separate /home partition from your / partition reinstalling wont be that problematic and may well solve that issue - has ubuntu been running well up to this point or is it a recent install which has broken?

Il

---

### Post by apjone on 2007-01-30
> **Illuvator said:**
> When I lost my start and restart options I reinstalled the OS. I still am none the wiser why they vanished - if anyone can give us a clue that would be cool as I like to understand what goes wrong with things. If you have a separate /home partition from your / partition reinstalling wont be that problematic and may well solve that issue - has ubuntu been running well up to this point or is it a recent install which has broken?

Il

it could be that your are not in groups that give permission to use these functions. At the end of the day 90% of linux problems occur due to incorrect permissions. Check system > Admin.... > Users & Groups or in a terminal 
```

cat /etc/group | grep $USER

```

to make sure you are in the correct groups

---

### Post by ekka on 2007-01-30
> **apjone said:**
> it could be that your are not in groups that give permission to use these functions. At the end of the day 90% of linux problems occur due to incorrect permissions. Check system > Admin.... > Users & Groups or in a terminal 
```

cat /etc/group | grep $USER

```

to make sure you are in the correct groups

I have to go back to my system to check that. But if I don’t have the right user permission, how come I can start an application in the initial couple of minutes when the system boots and why not after that?

---

### Post by wgw on 2007-03-30
That is an interesting remark; what groups should I normally be a member of? All? Right now, it looks something like:

lpadmin:x:109:b
haldaemon:x:110:
scanner:x:111:cupsys,hplip,b
slocate:x:112:b
gdm:x:113
bill:x:1000:b
admin:x:114:
fuse:x:115:b

and others. But my id (b) should be on which of the long list of groups?

---

### Post by ekka on 2007-04-01
Hey wgw, do you have a similar problem with your system? My thing is still broken, may be only reinstall will solve the problem :confused:

---

### Post by wgw on 2007-04-01
In my case, I  only have a problem with one application: wifi-radar. I have a work around which is: xhost +local:username (fill in the appropriate username). Then it comes up. 

 I think it is a permissions problem, perhaps specific to wifi-radar. I discovered some information about the problem by executing it from the terminal and reading the error messages. It is in part a problem with xserver authorisation. 

I also had a problem with network manager, but that turned out to be something differerent.

One thing in my long years of linux (i.e. about 2 weeks seriously), is that often a reinstall is the quickest solution. I wish I had installed my data files on a separte partition, so that a reinstall would not affect the data. I may try to repartition my system for that purpose. 

So, I don't have a good way to diagnose the problem, nor how to fix it. I'm too new at this. It isn't simple fixing a package --at least, I found it a bit of a torture here [http://www.ubuntuforums.org/showthread.php?t=395613](http://www.ubuntuforums.org/showthread.php?t=395613). 

It would seem that in many cases it is necessary to rebuild the installation, and sometimes quicker to do a reinstall. 

good luck (I know how frustrating it can be!)

---

### Post by Josh_Taylor on 2007-06-08
I'm noticing the same issue on my Ubuntu machine; seems like from a cold boot applications won't start in gnome (shows "Starting Firefox" etc. in the taskbar, but then disappears). A ctrl-alt-bs will remedy the issue until I find the need to cold boot again, but I'm at a loss as to possible causes. Anyone find a solution yet?

---

### Post by ekka on 2007-06-10
> **Josh_Taylor said:**
> I'm noticing the same issue on my Ubuntu machine; seems like from a cold boot applications won't start in gnome (shows "Starting Firefox" etc. in the taskbar, but then disappears). A ctrl-alt-bs will remedy the issue until I find the need to cold boot again, but I'm at a loss as to possible causes. Anyone find a solution yet?

Nope, I didn’t find any solution. I just reinstalled it.

---

