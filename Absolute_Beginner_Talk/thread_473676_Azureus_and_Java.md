---
title: "Azureus and Java"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by inspite on 2007-06-14
Hi,
I'm a recent convert to Ubuntu, and so far I have no complaints at all! 
However, in the last few days I've been having problems running Azureus. I have sun java installed (version 1.5.0_11). 
When I open azureus I get the error (azureus loads, the window shows, then dissapears)
```
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  Internal Error (53484152454432554E54494D450E43505001A3), pid=12101, tid=3084908224
#

```
However, if I switch back to free java with 
```
sudo update-alternatives --config java
```
open azurues, close azureus, then switch back to sun-java, everything works for a while. 
The error log file which is generated is really long, and a little too criptic for me!
I was wondering if anyone else has had this problem, and what they did to fix it. 
Thanks!
-Farid

---

### Post by dasbooter on 2007-06-16
Sorry don't have an answer but I thought I would chime in and say I also have the same error. I can run azureus as root with sudo however but this seems wrong security wise.I am using Suns java. Probably we are facing a permissions problem. Frostwire seems to be able to access java fine and running it does not require sudoing. I have just come over from suse and I am hoping some ubunt veteran will help us out.

---

### Post by gigaferz on 2007-06-16
have you tried unistalling it,and get the newest java and then reinstall it again(azureus)?

there are a lot of threads with the same issue,many of them solved by doing one of the above or all of them...

---

### Post by Keisad on 2007-06-16
I'm having the same problem as well.

I've tried re installing azureus, deleting and then re installing and it doesnt seem to work. I have the newest version of java but I still get this problem :
```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E435050020F), pid=6041, tid=3084798864

```

Still working at it though...

---

### Post by dakochan on 2007-06-17
Hi all,

I also have the same problem....
Still trying to find out why.


Best Regards,
Dakochan

---

### Post by dasbooter on 2007-06-17
I downloaded and replaced the java2.jar file with the latest one from sourceforge I didnt totally reinstall the whole thing only replaced that file and it seems to work alright with the exception that it does not automatically install plugins. I had to add the safe peer plugin manually and it also complained when I told it to restart something about azupdater not being installed... still it is working well for the purposes that I require.

---

### Post by dakochan on 2007-06-22
Hi,

I've solved the problem. It's in this forum as well. Please check:
[http://ubuntuforums.org/search.php?searchid=22522465](http://ubuntuforums.org/search.php?searchid=22522465)

---

### Post by Ansible on 2007-07-29
Above link is dead...

---

### Post by sailor2001 on 2007-07-29
if I'm not mistaken, jave jre needs to be installed through synaptics

---

### Post by WarholsGhost on 2007-07-29
there has been a big problem with azureus and java, but it doesn't seem to effect any other java based programs so what i did to solve it is just change to Deluge.

if you google deluge you can download the install packet, it is not available in the add/remove programs thing yet.

---

### Post by Ansible on 2007-07-29
Deluge looks cool.  It took a while to get all the packages installed, but now that its running I like it so far.  I was really looking for something like this on ubuntu anyway - I've started using utorrent on the windows side because its more lightweight than azureus; deluge looks kind of utorrent-ish.

---

### Post by mahasmb on 2007-08-25
> **inspite said:**
> Hi,
I'm a recent convert to Ubuntu, and so far I have no complaints at all! 
However, in the last few days I've been having problems running Azureus. I have sun java installed (version 1.5.0_11). 
When I open azureus I get the error (azureus loads, the window shows, then dissapears)
```
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  Internal Error (53484152454432554E54494D450E43505001A3), pid=12101, tid=3084908224
#

```
However, if I switch back to free java with 
```
sudo update-alternatives --config java
```
open azurues, close azureus, then switch back to sun-java, everything works for a while. 
The error log file which is generated is really long, and a little too criptic for me!
I was wondering if anyone else has had this problem, and what they did to fix it. 
Thanks!
-Farid


Thanks! This seems to work for me. How do I upgrade to the latest version though? I'm using 2.5.0.0. It doesn't upgrade automatically. And I can't install version 2.5.0.4 ( or the latest one) and have it actually show up under applications.

---

### Post by DanPT on 2007-08-25
I had a lot of problem but the only way I got it to work is first uninstall everything

Then install Java JRE 6 (1.6.0_02) with this method
[http://ubuntuforums.org/showthread.php?t=332674](http://ubuntuforums.org/showthread.php?t=332674)

Just use JRE package instead of the SDK if you don't need the SDK.
I didn't do the eclipse part.

Then install Azureus with this method

[http://ubuntuforums.org/showthread.php?t=144546](http://ubuntuforums.org/showthread.php?t=144546)

Now I have the lastest verison of Java and Azureus. Both seem to work prefectly

Neither combination of automatix ubuntu package of java or Azureus wanted to work together. But if you installed them manually with the HOWTO above it work perfectly

---

