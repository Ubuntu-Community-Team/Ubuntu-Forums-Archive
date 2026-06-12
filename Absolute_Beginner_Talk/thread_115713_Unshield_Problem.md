---
title: "Unshield Problem"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by IanM39 on 2006-01-11
Hi,

I am trying to load drivers in ndiswrapper for my Netgear wg111v2 wireless USB adaptor.  I have tried loading the .inf and ,sys files from the netgear configuration utikity CD, but ndiswrapper just returns an "invalid Driver" message.

I then tried downloading the drivers from the Netgear site but there were no .inf or .sys files.  Then I heard that Unshield can extract these files from the data1.cab file I downloaded from netgear.

I've got the tar.gz packat I vge onto my linux machine, but have no idea how to compile and load the program so that I can use it.

Can anybody give me an idiots guide to installing and using Unshield so that I can try to get internet access on my linux machine.  I love everything else about linux, i just wish I could get on to the net.

Many thanks.

---

### Post by pacificdrums on 2006-03-23
Yes I am having the same problem but I do know how to get unshield installed.

First to get the .deb package [Go here]("http://packages.debian.org/stable/utils/unshield"). Then put it on the desktop of ubuntu and open a terminal. In the terminal you need to change directory to your desktop
```
cd /home/your name here/Desktop/
```
Now that your at the desktop type in
```
sudo dpkg -i unshield_0.4-3_i386.deb
```
Now Unshield should be installed but that program did give me trouble. It needed one other file I did not have. Ubuntu should see that though and get it from the internet. So if you have another computer that's running Ubuntu and is connected to the internet or you can connect one with Ethernet instead try that. Then Ubuntu should just get the file for you. You will need to click on the little update icon in the upper right hand corner. But all that is only if Unshield dose not install correctly for you and some one here might now how to do that without connecting to the internet.
Now to extract your file you need to change directory again to wherever that file is. or you can just put the data#.cab files on your desktop. Now type in
```
unshield x data1.cab
``` or data2.cab.

That is what I did and unshield still did not get my file out but its worth a shot. Hope that answers your question. :-D

---

### Post by pacificdrums on 2006-03-23
O and if it gives you errors on the install just try to extract anyway. I just found out you may not need to be connected to the internet to fix the dependencies. So just try to extract anyway and wait a second and the little update icon should come up. Just click that and install what it says you need.

---

### Post by akiro.yamamoto on 2006-03-23
There is a program in the repos. that can extract all the contents from a .cab file....
It's called cabextract... See pic...
It's a command line util, but easy to use....
```

man cabextract

```
For more info ;)
Something like:
```
 cabextract my_cab/ cab-file.cab
```
Where my_cab/ is a directory you want to extract the cab contents to.
And cab-file.cab is YOUR cab file.... ;)
Hope this info helps....

---

### Post by pacificdrums on 2006-03-23
OK I have tried that program and it dose not extract all cab files. It tells you to use unshield because they are part of a windows install shield or something like that.

---

### Post by pacificdrums on 2006-03-23
lol my bad, I could not extract the files because the program could not make the directory. I changed the permissions and it worked fine.:-D

---

