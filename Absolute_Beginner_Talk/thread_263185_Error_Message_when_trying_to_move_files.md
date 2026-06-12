---
title: "Error Message when trying to move files"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by HareBall on 2006-09-22
I have been trying to move flashplayer.xpt and libflashplayer.so to the firefox plug-ins folder. I keep getting an error message telling me, "You do not have permissions to write to this folder".
I am the administrator, and am logged on as such.
So how do I move these files?

---

### Post by bulldog on 2006-09-22
The only way to do that is as root.

sudo cp whateveryouwant /whereeveryouwant

---

### Post by HareBall on 2006-09-22
> **bulldog said:**
> The only way to do that is as root.

sudo cp whateveryouwant /whereeveryouwant

I'm not sure exactly how to do this. I can understand the last half of this at the /whereeveryouwant, but it is the first half I can't seem to get to work. Here is what I tried to do, with the messages I keep getting.

larry@larry-desktop:~$ sudo cp install_install_flash_player_7_linux /usr/lib/for efox/plugins
cp: cannot stat `install_install_flash_player_7_linux': No such file or director y
larry@larry-desktop:~$ sudo cp /desktop/install_install_flash_player_7_linux /us r/lib/forefox/plugins
cp: cannot stat `/desktop/install_install_flash_player_7_linux': No such file or  directory

I saved the download to my desktop. I am lost in finding the route to this file. I believe I got the second half right, just not the tree to the file to move.:confused: 


Please tell me exactly what to do. I have only been at this 1 1/2 days.
Thanx,
Larry

---

### Post by maaronB on 2006-09-22
The error in the example you give is that the file does not exist.

I notice that you use
  > sudo cp /desktop/install_install_flash_player_7_linux /us r/lib/forefox/plugins

On my computer the desktop is called Desktop (capitilized: it does matter in linux).

---

### Post by HareBall on 2006-09-22
> **maaronB said:**
> The error in the example you give is that the file does not exist.

I notice that you use
  

On my computer the desktop is called Desktop (capitilized: it does matter in linux).

Still not getting it:(  I am still getting told the file doesn't exist. I can go to it on my desktop. Can someone please tell me what the tree might be.
Thanx again,
Larry

---

### Post by maaronB on 2006-09-22
I don't know if you know it or not but you can use TAB to autocomplete statements.
So for instance you can hit TAB after you are in the desktop (Desktop?) directory you can type "inst" then hit TAB and it should autocomplete "install_install_flash_player_7_linux".


Also you should ignore everything I have said until this point because "install_install_flash_player_7_linux" is not the file you want to move anyway.  I don't know exactly what it is but my guess is that it is an executable that automatically sets everything else up for you.  
So find it in GNOME and then right click on it.
Then click on properties.
Then click on permissions.
Then make it executable for the owner.
(sometimes you can then double click on it and it will run in which case skip the next few steps)
Then go back to the command prompt and type
```
cd des(TAB key) (or Des(TAB key)
./insta(TAB key)
```

If my guess that it is an installer is correct that should set everything up for you.

You should also probably consider looking at Automatix.

---

### Post by HareBall on 2006-09-22
> **maaronB said:**
> I don't know if you know it or not but you can use TAB to autocomplete statements.
So for instance you can hit TAB after you are in the desktop (Desktop?) directory you can type "inst" then hit TAB and it should autocomplete "install_install_flash_player_7_linux".


Also you should ignore everything I have said until this point because "install_install_flash_player_7_linux" is not the file you want to move anyway.  I don't know exactly what it is but my guess is that it is an executable that automatically sets everything else up for you.  
So find it in GNOME and then right click on it.
Then click on properties.
Then click on permissions.
Then make it executable for the owner.
(sometimes you can then double click on it and it will run in which case skip the next few steps)
Then go back to the command prompt and type
```
cd des(TAB key) (or Des(TAB key)
./insta(TAB key)
```

If my guess that it is an installer is correct that should set everything up for you.

You should also probably consider looking at Automatix.


This is supposed to be the installer for the flash plugin for firefox. It doesn't work when I try to get it to automatically install. I have tried drag and drop to move the necessary files and I have tried to do it fromthe terminal. Nothing I have tried has worked. I have, as I said above, only been at this since yeterday. I mean Ubuntu by that. I got to used to doing it the Windows way for too long and now I have to learn how to do things all over again.
I ain't giving up though. I will whip this problem.
Larry[-o<

---

### Post by crokett on 2006-09-22
The file you want is in /home/<yourusername>/D(d?)esktop

---

### Post by maaronB on 2006-09-22
Have you looked at Automatix.

I just want to make sure you know about it.  I used it and it does make setting things up easier, but if you are interested in learning it might be better to do it yourself.

Also, since you are that new, you might not have realized something yet.
Finding and installing things on linux is a much different process that it is on Windows.  In fact it is easier in Linux.

On Windows you do internet searches, find the program you want, go to the homepage, download and install.  This is normally the Wrong way to do it in Linux. 
Because Linux is still on the fringe, and because it is fragmented into different distro's it is difficult for developers to make things that will work automatically.  To solve this problem distros and volunteers (including Ubuntu) make repositories that contain the programs you need.

Long story short.
Go to System menu
click on Administration
click on Synaptic Program Manager
cl: Settings then Repositories
check everything
See if Flash (and everything else you need or want) can be installed from synaptic.

---

### Post by HareBall on 2006-09-22
> **crokett said:**
> The file you want is in /home/<yourusername>/D(d?)esktop

I started by moving the files to the desktop and trying this in the terminal:

larry@larry-desktop:~$ sudo cp flashplayer.xpt /usr/lib/firefox/plugins /file system/usr/lib/firefox/plugins

Now I don't get the same message about file not found, but I get this:
cp: target `system/usr/lib/firefox/plugins' is not a directory

I know this is the simpole stuff, but I have to start somewhere:)

---

### Post by BlocknBleed on 2006-09-22
I'm in exactly the same boat as you. New user, same problem.
I just got mine moved after a realized that I never extracted the files to desktop to begin with. Then I did this and it seemed to work.

jesse@jesse-desktop:~$ sudo cp /home/jesse/Desktop/flashplayer.xpt /usr/lib/mozi lla-firefox/plugins
Password:
jesse@jesse-desktop:~$ sudo cp /home/jesse/Desktop/libflashplayer.so /usr/lib/mo zilla-firefox/plugins
jesse@jesse-desktop:~$

Hope it helps.

---

### Post by maaronB on 2006-09-22
> **HareBall said:**
> I started by moving the files to the desktop and trying this in the terminal:

larry@larry-desktop:~$ sudo cp flashplayer.xpt /usr/lib/firefox/plugins /file system/usr/lib/firefox/plugins

Now I don't get the same message about file not found, but I get this:
cp: target `system/usr/lib/firefox/plugins' is not a directory

I know this is the simpole stuff, but I have to start somewhere:)

larry@larry-desktop:~$ sudo cp flashplayer.xpt /usr/lib/firefox/plugins ***/file system/usr/lib/firefox/plugins***

What are you trying to do with that last part.  It seems unnecessay.

---

### Post by HareBall on 2006-09-22
> **maaronB said:**
> Have you looked at Automatix.

I just want to make sure you know about it.  I used it and it does make setting things up easier, but if you are interested in learning it might be better to do it yourself.

<SNIPPED>

Long story short.
Go to System menu
click on Administration
click on Synaptic Program Manager
cl: Settings then Repositories
check everything
See if Flash (and everything else you need or want) can be installed from synaptic.

I can't seem to locate anywhere to download Automatix. I have found all kinds of stuff about it, but no downloads.
Tried the "Synaptic Program Manager" also. Nothing there about Flas. This is an Adobe plugin. Some websites don't seem to want you to see much without it.
Having the same kind of trouble with Java.
Still ain't giving up, just about to stop for the night though.
Thanx for responding,
Larry

---

### Post by HareBall on 2006-09-22
> **maaronB said:**
> larry@larry-desktop:~$ sudo cp flashplayer.xpt /usr/lib/firefox/plugins ***/file system/usr/lib/firefox/plugins***

What are you trying to do with that last part.  It seems unnecessay.

Part of that got pasted twice somehow. I have tried just about every combination I could come up with. Nothing has worked yet.
Larry

---

### Post by maaronB on 2006-09-22
> **HareBall said:**
> I can't seem to locate anywhere to download Automatix. I have found all kinds of stuff about it, but no downloads.
Tried the "Synaptic Program Manager" also. Nothing there about Flas. This is an Adobe plugin. Some websites don't seem to want you to see much without it.
Having the same kind of trouble with Java.
Still ain't giving up, just about to stop for the night though.
Thanx for responding,
Larry

From here:
[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix]("http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix")

Open up terminal and paste the following lines one after the other (wait for each command to finish before you paste the next)
```
wget http://www.getautomatix.com/files/automatix-installer
chmod 755 ~/automatix-installer
./automatix-installer
```

Automatix is also an easy way to install Java.

---

### Post by HareBall on 2006-09-22
> **BlocknBleed said:**
> I'm in exactly the same boat as you. New user, same problem.
I just got mine moved after a realized that I never extracted the files to desktop to begin with. Then I did this and it seemed to work.

jesse@jesse-desktop:~$ sudo cp /home/jesse/Desktop/flashplayer.xpt /usr/lib/mozi lla-firefox/plugins
Password:
jesse@jesse-desktop:~$ sudo cp /home/jesse/Desktop/libflashplayer.so /usr/lib/mo zilla-firefox/plugins
jesse@jesse-desktop:~$

Hope it helps.

Great, this worked like a charm. Copy and paste is truly my friend. Now if I can get Java to work ;)

---

### Post by maaronB on 2006-09-22
You can start Automatix by going Applications , then System Tools, Automatix.
It should have Sun Java as one of the options to install.

---

### Post by HareBall on 2006-09-22
> **maaronB said:**
> From here:
[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix]("http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix")

Open up terminal and paste the following lines one after the other (wait for each command to finish before you paste the next)
```
wget http://www.getautomatix.com/files/automatix-installer
chmod 755 ~/automatix-installer
./automatix-installer
```

Automatix is also an easy way to install Java.

Thanx, it is loading stuff now. Can't wait to see what all I can do. I am slowly going to wean myself from windows;O)
Larry

---

