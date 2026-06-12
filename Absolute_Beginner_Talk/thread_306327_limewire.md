---
title: "limewire"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by Cardmaster91 on 2006-11-24
can u run limewire on ubuntu edgy?
if so, how?

---

### Post by jpkotta on 2006-11-24
Use Frostwire.  Get Java 1.5 (or 5.0 or whatever they call it now) (I like Sun Java), and get the Frostwire .deb from [http://www.frostwire.com](http://www.frostwire.com).  Install the deb with ```
sudo dpkg -i FrostWire*.deb
```

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by taurus on 2006-11-24
Install it and run it!!!

---

### Post by Cardmaster91 on 2006-11-24
is this a good sign then?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "frostwire"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by ron999 on 2006-11-24
**is this a good sign then?**

No, it doesn't look good.

There's stuff about Limewire in this thread, specially post #5
[http://www.ubuntuforums.org/showthread.php?t=297142]("http://www.ubuntuforums.org/showthread.php?t=297142")
8)

---

### Post by Cardmaster91 on 2006-11-24
ok, whoopdie doo, i have the rpm file. how do u use it?

---

### Post by taurus on 2006-11-24
```
sudo aptitude install alien
alien <filename>.rpm
sudo dpkg -i <filename>.deb
limewire
```

---

### Post by Papa-san on 2006-11-24
Search is your best friend here...

Try this link:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Hang tough!

EDIT: Bookmark this one!

---

### Post by ron999 on 2006-11-24
Taurus beat me to it :p 

This is my take:-

OK Cardmaster, do this:-

1) Install alien (Use Synaptic)
2) Install Sun Java 1.5 JRE (Easiest way is to use Automatix2)
3) Make sure that the Limewire RPM file is on your desktop
4) Convert the RPM file to a DEB file by typing at the terminal:-
sudo alien -k /home/ron/Desktop/LimeWireLinux.rpm
**(Use your own username, not mine!)**
5) The DEB file will appear in your home folder, double click it to install Limewire - it will probably put a shortcut in your Applications>Internet menu
:cool:

EDIT: Yes, bookmark Papa-san's link

---

### Post by Cardmaster91 on 2006-11-25
i havent tried the rpm ile yet, but i do have frostwire. the only problem is when i open it, it doesnt ever connect, it says starting connection

---

### Post by taurus on 2006-11-25
Is your computer connected to a router?  If it is, then you need to go into your router and open whatever port(s) that frostwire is using...

---

### Post by Cardmaster91 on 2006-11-25
wat port i frostwire is using? i was able to connect w/ limewire on windows. and i have 6112 open.

---

### Post by taurus on 2006-11-25
I don't know what port frostwire is using.  You have to look for it.  Maybe frostwire is not using the same port as your limewire in Windows!  Try to change the port for frostwire to 6112 or open a new port for frostwire.

---

### Post by Cardmaster91 on 2006-11-25
uhhm, how?

---

### Post by taurus on 2006-11-25
> **Cardmaster91 said:**
> uhhm, how?
How to look to see what port frostwire is using or how to open a port for frostwire in your router???

---

### Post by Cardmaster91 on 2006-11-25
both

---

### Post by Spano on 2006-11-25
> it doesnt ever connect, it says starting connection
Current versions of Limewire and Frostwire have this problem.
Now that you have Frostwire installed try this tweak:
[http://www.ubuntuforums.org/showthread.php?t=295253](http://www.ubuntuforums.org/showthread.php?t=295253)
An alternative is to try gnunet-gtk, availible in synaptic, it should work for you "out of the box".

---

### Post by Cardmaster91 on 2006-11-25
ok, i can connect now. but it wont go but 5 minutes w/o freezing

---

### Post by Cardmaster91 on 2006-11-25
ummm, i would like an answer please. i cant rlly do anything on frostwire. it starts, connects, then takes up 100%of my cpu, and is so slow it seems frozen. if i switch to the frostwire window, it takes about 10 minutes to load. and another 10 to click on anything. i wuld rlly like to start dling.

---

### Post by jpkotta on 2006-11-26
Start Frostwire from a terminal and give us the messages it spits out:
```
frostwire >& ~/frostlog.txt
```
Attach the file frostlog.txt (it will be in your home directory) to a post.

Remember, there may be solutions here too:
[http://www.frostwire.com/forum/](http://www.frostwire.com/forum/)

Specifially, [http://www.frostwire.com/forum/viewtopic.php?t=679&highlight=linux+cpu](http://www.frostwire.com/forum/viewtopic.php?t=679&highlight=linux+cpu)

---

### Post by pavel_kbc on 2006-11-26
Thanks pplz :D

---

### Post by seismicmike on 2006-11-26
This may sound like a really stupid question, but I can't get java to work...

I downloaded limewire and installed it and it said I need to upgrade to jre 1.5.x... so I went to java.com and downloaded jre 1.5.x.rpm.... and I installed it, and it says it runs fine, but when I try to run limewire again, it still says that it can't find java. Do I need to write a script in the limewire folder to tell it where java is? If so, how do I do that. Yeah, I'm lazy. Can anyone help?

---

### Post by taurus on 2006-11-26
What's the output of this command from a terminal?

```
java -version
```

---

### Post by xpod on 2006-11-26
Not sure if your still having trouble with Frostwire constantly "starting connection" but a few folks had the same issue recently...

You`ll find the answer in post 44 of this thread

[http://ubuntuforums.org/showthread.php?t=292863&page=5](http://ubuntuforums.org/showthread.php?t=292863&page=5)
Good luck

---

### Post by seismicmike on 2006-11-26
```
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

so, yeah apparently it didn't take. What do I need to do?

---

### Post by ThrobbingBrain66 on 2006-11-26
i just did a quick scan of this thread, so i may have missed it if someone already offered this advice, but to actually use sun java after you install you have to set it as default with this command:

```
sudo update-java-alternatives -s java-1.5.0-sun
```

---

### Post by taurus on 2006-11-26
Or

```
sudo update-alternatives --config java
```

---

### Post by jpkotta on 2006-11-26
If you had read [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) you would know you had to set the default Java.

Use the wiki!

---

### Post by Cardmaster91 on 2006-11-26
> **jpkotta said:**
> Start Frostwire from a terminal and give us the messages it spits out:
```
frostwire >& ~/frostlog.txt
```
Attach the file frostlog.txt (it will be in your home directory) to a post.

Remember, there may be solutions here too:
[http://www.frostwire.com/forum/](http://www.frostwire.com/forum/)

Specifially, [http://www.frostwire.com/forum/viewtopic.php?t=679&highlight=linux+cpu](http://www.frostwire.com/forum/viewtopic.php?t=679&highlight=linux+cpu)

it gave out no message, it startedfrostwire (still frezzes and takes up 100% cpu)


ur other post:
If you had read [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) you would know you had to set the default Java.

Use the wiki!




i tried that link, i got lost after like the third paragraph, lol. im newb,.

---

### Post by Cardmaster91 on 2006-11-26
wow, i just used this thread, and it seems to work excellent. i have a "turbo-charged connecton" so i think its pretty good. and it doesnt freeze up. i guess its just a beta tho.

[http://ubuntuforums.org/showthread.php?t=305337]("http://ubuntuforums.org/showthread.php?t=305337")

---

### Post by Cardmaster91 on 2006-11-26
scratch that...


its been about 30 minutes, and its starting to slow down, ive tried restarting and everything, it slows down and starts to take up 100% cpu


this keeps appearing in terminal 

java.lang.OutOfMemoryError: Java heap space

---

### Post by jpkotta on 2006-11-26
First off, if you are using a beta, try the current release version.  That will probably not have any of these issues.  For reference, please post the version of Frostwire that's not working and if you do get another version to work, post that too.

Maybe there is a problem with the "human" theme?  Is human the default?  Try using a different theme.  Also, we may have found a bug in Frostwire, at least it doesn't really look like a configuration issue.  It wouldn't be a bad idea to go to their forums and ask about it.

BTW, the Java link was meant for the guy who didn't have the correct Java default.

---

### Post by Cardmaster91 on 2006-11-26
both versions have not worked, up until my post when i said i got i got turbocharged connection, i was using the automatix version (i have no idea wat version hat was) now im using the beta release 4.13.1
but has the same issue, and i have tried different themse.

---

### Post by jpkotta on 2006-11-27
Go ahead and install the .deb from frostwire.com.  It should be 4.10.  See [https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire) for help on installing it.  If the instructions are confusing, then post back; we want to get them clear and easy.

---

### Post by misfitpierce on 2006-11-27
yeah I run limewire got the RPM off site I believe and alien'd it and then installed the deb file. Very easy and works flawlessly.

---

### Post by seismicmike on 2006-11-30
> **ThrobbingBrain66 said:**
> i just did a quick scan of this thread, so i may have missed it if someone already offered this advice, but to actually use sun java after you install you have to set it as default with this command:

```
sudo update-java-alternatives -s java-1.5.0-sun
```

```
:~/Desktop$ sudo update-java-alternatives -s java-1.5.0-sun
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-1.5.0-sun

```

```
:/usr/lib/jvm$ ls
java-1.4.2-gcj-4.1-1.4.2.0  java-gcj

```

can you help me fix this?

---

### Post by jpkotta on 2006-11-30
Do you have Sun Java installed?  Find out with ```
update-java-alternatives -l
```This will list all the JVMs you have.  If Sun Java isn't there, then install it.

[https://help.ubuntu.com/community/Java#head-f4267cc37a197ccf46397cc58ff0944838741956](https://help.ubuntu.com/community/Java#head-f4267cc37a197ccf46397cc58ff0944838741956)

---

### Post by Cardmaster91 on 2006-12-06
ok, i edventually just decided to reinstall ubuntu, then automatix. i installed everything i needed through automatix first. it all seems to work fine now. the only program i have a problem with is google earth.
[IMG]http://i130.photobucket.com/albums/p270/cardmaster91/googearth.png[/IMG]

---

### Post by jpkotta on 2006-12-06
Just a guess: ```
rm -rf ~/.googleearth
```  This will clear all user settings for googleearth, and might clear out whatever is wrong, maybe.

Note: be careful with the command rm with the -rf options.

---

### Post by Cardmaster91 on 2006-12-07
didnt work

---

### Post by pissedoffdude on 2006-12-07
try gtk-gnutella, its available in the repos

---

### Post by jpkotta on 2006-12-09
Then I would just try to reinstall GoogleEarth from Google itself, not through Automatix or whatever.  Tip: when you install GoogleEarth, don't run it afterwards, just quit immediately after install.  This will prevent it creating a bunch of root-owned files in $HOME.

---

