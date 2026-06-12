---
title: "What Have I Done!!??"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by _Phantom_ on 2008-02-11
ok soo i installed ubuntu 7.10 on my comp but this is not what i was wishing for lol
i was looking for a safe clone of windows and well i didnt get that sooo i need to learn things...
i have no idea how to do anything... i cant even extracted??? if thats the word.... a theme im just hopeless any good guides 
i tried using a couple i found but there written in linux language ! lol im a super N00B and am srry if this has been asked before....
just looking for some help.. 

_Phantom_


The need on the top of my list is Floola instulation ..... lol srry

---

### Post by LaRoza on 2008-02-11
If you don't want to use Linux, then don't. Since you didn't get what you wanted, I suggest sticky with Windows. [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

If you have decided to try Linux anyway, you will have to spend sometime learning new things. (It isn't any harder, just different, read the article I linked to)

For Floola: [http://www.floola.com/modules/wiwimod/index.php?page=download_linux](http://www.floola.com/modules/wiwimod/index.php?page=download_linux)

---

### Post by _Phantom_ on 2008-02-11
i deffinatly want to try linux and im willing to learn! i was just thunderstruck! 
i type 
sudo apt-get install libnotify-bin 
in the terminal
enter my password 
but then sez connecting to ca.archive.ubuntu.com then an ip adresss
and the % doesnt change at all...
hoep that made sence...
then it sez timed out....

_Phantom_

---

### Post by oedha on 2008-02-11
before installing......you have to point your software source.....
go to system - administration - software source
detail in /etc/apt/sources.list
then sudo apt-get update
then sudo-apt get install "programname"

---

### Post by tact on 2008-02-11
Hey there...  Welcome to the world of linux.  If you can hang in there and don't mind learning you might just find that what you have got, whilst its definitely NOT a clone of windows, is a lot safer and worth the effort learning.

Some tips:
- You might want to tackle things one step at a time and put mor especific/relevant topics like "How do I add a theme to standard ubuntu 7.10" and you will sure get good polite help here.

- One of the things that got me into trouble when I was new to linux was thinking i can google (or search these forums) to get all the answers i need.   Thing is - you get answers, too many of them! 

- Some of the answers may be wrong for you (relating to different versions of linux for example)   
- And many of the answers, while damn good answers, may not be what you are really looking for (and you don't know it because you don't really know what the right questionis to ask!).

- So I soon learned to preface every google query with the words "ubuntu" and or "gutsy" etc.  and I learned not to grab the first "how-to" and follow it expecting good results.  

(example... I just wanted to share folders with my wife's winXP laptop and I followed some long detailed how-to's and installed a HEAP of software (samba, winbind, etc etc) and configured it all and messed myself up terribly - only to find out later (with Feisty and Gutsy) it was all wasted effort - all I had to do was "right click" on the folder and select "sharing".)

Now to your question about unpacking and installing a new theme:
There are lots of different types of themes - GDM themes, Gnome Splash themes, usplash themes, etc etc.   They each have  their own installation process.  Very likely you don't have to unpack it at all as you just either drag'n'drop or "add" the compressed package as it is.   No need to unpack at all if it is packaged correctly.

To install a desktop theme (look for GTK2 themes for ubuntu 7.10) you simply click System>Preferences>Appearance and then click "install" and navigate to the *.tar.gz package (assuming it is in the correct format) and it will install.  No need to unpack anything.

So tell some more about the kind of theme you have downloaded...where you got it...etc.  Then can give more explicit direction.

(Ohh...  and to unpack pretty much any archive you download (remember for themes you likely dont need to unpack it - but for other things...) all you need to do is "right click" and "Extract Here".)

---

### Post by _Phantom_ on 2008-02-11
> **oedha said:**
> before installing......you have to point your software source.....
go to system - administration - software source
detail in /etc/apt/sources.list
then sudo apt-get update
then sudo-apt get install "programname"

im sorry what does this meen? ive been to software sources but after that im lost srry...

---------------------

> **tact said:**
> Hey there...  Welcome to the world of linux.  If you can hang in there and don't mind learning you might just find that what you have got, whilst its definitely NOT a clone of windows, is a lot safer and worth the effort learning.

Some tips:
- You might want to tackle things one step at a time and put mor especific/relevant topics like "How do I add a theme to standard ubuntu 7.10" and you will sure get good polite help here.

- One of the things that got me into trouble when I was new to linux was thinking i can google (or search these forums) to get all the answers i need.   Thing is - you get answers, too many of them! 

- Some of the answers may be wrong for you (relating to different versions of linux for example)   
- And many of the answers, while damn good answers, may not be what you are really looking for (and you don't know it because you don't really know what the right questionis to ask!).

- So I soon learned to preface every google query with the words "ubuntu" and or "gutsy" etc.  and I learned not to grab the first "how-to" and follow it expecting good results.  

(example... I just wanted to share folders with my wife's winXP laptop and I followed some long detailed how-to's and installed a HEAP of software (samba, winbind, etc etc) and configured it all and messed myself up terribly - only to find out later (with Feisty and Gutsy) it was all wasted effort - all I had to do was "right click" on the folder and select "sharing".)

Now to your question about unpacking and installing a new theme:
There are lots of different types of themes - GDM themes, Gnome Splash themes, usplash themes, etc etc.   They each have  their own installation process.  Very likely you don't have to unpack it at all as you just either drag'n'drop or "add" the compressed package as it is.   No need to unpack at all if it is packaged correctly.

To install a desktop theme (look for GTK2 themes for ubuntu 7.10) you simply click System>Preferences>Appearance and then click "install" and navigate to the *.tar.gz package (assuming it is in the correct format) and it will install.  No need to unpack anything.

So tell some more about the kind of theme you have downloaded...where you got it...etc.  Then can give more explicit direction.

(Ohh...  and to unpack pretty much any archive you download (remember for themes you likely dont need to unpack it - but for other things...) all you need to do is "right click" and "Extract Here".)

thank i appreciated it!

_phantom_

---

### Post by tact on 2008-02-11
> **_Phantom_ said:**
> i deffinatly want to try linux and im willing to learn! i was just thunderstruck! 
i type 
sudo apt-get install libnotify-bin 
in the terminal
enter my password 
but then sez connecting to ca.archive.ubuntu.com then an ip adresss
and the % doesnt change at all...
hoep that made sence...
then it sez timed out....

_Phantom_

That could be just a bad connection at the time.  Try again.  If you get a message telling you that the package is not available then maybe you need to turn on some additional repositories.  Try it again when you are sure your internet connection is good and let us know what the result is.

---

### Post by _Phantom_ on 2008-02-11
> **tact said:**
> That could be just a bad connection at the time.  Try again.  If you get a message telling you that the package is not available then maybe you need to turn on some additional repositories.  Try it again when you are sure your internet connection is good and let us know what the result is.

it seems my computer allways does this ....
and my connection is allways ´bad´

_Phantom_

---

### Post by jan quark on 2008-02-11
hi and welcome _Phantom_

you may feel thunderstrucked 
it is OK we are here to help you and answer every question

linux is not windows and many things are much more better solved than in windows
but differently and that is what makes you feel like being in a foreign country and everybody is speaking a strange language

but after some time you will be speaking it by yourself


here some question

is you internet connection working ; I don't know if you are running to another PC to post 
your questions? :)


to ckeck your internet status just open the terminal
it can be found here

system > accessories > terminal

open it

and type in 

```
iwconfig
```

press enter and post the output here by simply copy and paste


then we have to make sure your software sources are enabled

go to system > administration > software sources

are all sources checked ? if not check the boxes and click on reload


in the beginning try also to install via the add/remove application 

can be found here applications > add/remove

ask if you hit the wall

---

### Post by tact on 2008-02-11
> **_Phantom_ said:**
>  [QUOTE= oedha]
before installing......you have to point your software source.....
go to system - administration - software source
detail in /etc/apt/sources.list
then sudo apt-get update
then sudo-apt get install "programname"


im sorry what does this meen? ive been to software sources but after that im lost srry...

_phantom_[/QUOTE]

Don't worry about that for now.  I don't think you need to alter your sources list to install libnotify-bin.  Just give this another shot when you know your internet connection is good.

```
sudo apt-get install libnotify-bin 
```

---

### Post by tact on 2008-02-11
> **_Phantom_ said:**
> it seems my computer allways does this ....
and my connection is allways ´bad´

_Phantom_

Are you able to do anything online?  Email?  Surf the web?

How are you connecting to the internet?   Wifi?  Wired ethernet?

Please do as jan quark requested and in a terminal type 
```
iwconfig
```
(this gives a listing of all network interfaces and whether they have any wireless extensions - it will help us to understand what you are using).

and also ...
```
ifconfig
```
(this will list out the configuration of all your network interfaces and if any are active what its configuration is).

Paste the results back here...

(note:  you should be careful you understand what people are asking you to type in a terminal (specially if the command starts off with "sudo" because this gives "administrator" or "superuser" powers to the command)...   it is possible to do a lot of damage to your system and there have been some mean-spirited people advising newcomers to type things (execute commands) that cause problems).

---

### Post by _Phantom_ on 2008-02-11
ok thank you all so much for your help! 
> **tact said:**
> are you able to do anything online
Yes e-mail surf download
my interent is working but when ever i try to download anything via the terminal it times out.... i had this same problem of windows .. i am running a linksys router could that be the problem do i need to port forward? i tried that on windows and it also didnt work, it stoped me from playing games and downloading at my capable speed...
i should have quoted someone srry if taht causes confusion ..
> **tact said:**
> wifi?Wired ethernet?
I have wired eithernet
thx again!

oh i changed the thing with the software sources and tried the 
sudo apt-get install libnotify-bin
terminal code and it didnt work it sez
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

any help would be great!!!! thx guys !
> **tact said:**
> Paste the results back here...


here is for the iw config

ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


here is for the ifconfig

ubuntu:~$ : Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.
georgio@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D3:24:EA:FA  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fe24:eafa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:239788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:333553216 (318.1 MB)  TX bytes:16082316 (15.3 MB)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2065 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2065 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:164511 (160.6 KB)  TX bytes:164511 (160.6 KB)



_phantom_

---

### Post by tact on 2008-02-11
ok seems your networking is all good.  No it won't be a port forwarding problem.  Sometimes repositories are down or not contactable and so you get the message "unable to fetch some archives"

Did you follow the advice after the warning and run
```
sudo apt-get --fix-missing
```
and
```
sudo apt-get update
```

What is the result?

You could also try to change the country/server your system is set up to use for repository databases...
System>Admin>Software Sources
- make sure  the first 4 checkboxes are ticked
- Click on the button near "Download from:" and select a location near to you, or try a different location.

Once that is done you can go back to a terminal and do 
```
sudo apt-get update
```
if there is a problem try also
```
sudo apt-get --fix-missing
```

Then try again to 
```
sudo apt-get install libnotify-bin
```

---

