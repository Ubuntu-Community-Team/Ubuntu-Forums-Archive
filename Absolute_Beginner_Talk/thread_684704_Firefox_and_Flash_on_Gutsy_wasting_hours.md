---
title: "Firefox and Flash on Gutsy wasting hours"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Knot_Sharpe on 2008-02-01
Hi all,

I'm a noob, but not incompetent.  Done lots of reading and have tried many of the more recent fixes without success, the latest download refused to install, saying I had a newer version ... which I can't find to delete.

Does anyone have the latest suggestions for the Adobe/flash/Gutsy mess?  I would hope a fix for something as basic as watching Utube videos would be pretty critical a fix?

Thanks for any ideas, 
Gary

---

### Post by erfahren on 2008-02-01
are you using 32-bit or 64-bit Ubuntu?

---

### Post by philinux on 2008-02-01
[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

One of these should fix you up.

---

### Post by Knot_Sharpe on 2008-02-01
32 bit as far as i know...did the simple instal from cd

---

### Post by philinux on 2008-02-01
[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

One of these should fix you up, if it's 32 bit.

[edit] top link site down .

---

### Post by jan quark on 2008-02-01
try my guide it works

[http://janquark.fatfreehost.com/tutorial3.html](http://janquark.fatfreehost.com/tutorial3.html)

---

### Post by Knot_Sharpe on 2008-02-01
> **philinux said:**
> [http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

One of these should fix you up.

Thank, I tried both of those to no avail.

---

### Post by taurus on 2008-02-01
Open a terminal and download it by hand.

Applications -> Accessories -> Terminal
```
cd ~/Desktop
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
```
When it's done, unpack it and install it.

```

tar xvzf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux
sudo ./flashplayer-installer
**[COLOR="Blue"]-or-[/COLOR]**
sudo cp libflashplayer.so /usr/lib/firefox/plugins
```

Fire up firefox again and see if flash plugin is on the list.

```
about:plugins
```

---

### Post by Knot_Sharpe on 2008-02-01
> **jan quark said:**
> try my guide it works

[http://janquark.fatfreehost.com/tutorial3.html](http://janquark.fatfreehost.com/tutorial3.html)

Thanks, I'll try it now and get back to you soon .....

---

### Post by jan quark on 2008-02-01
cool taurus it is almost the same guide as I have written but I dont have the las copy step is it necessary 
i didn't have to do this
just asking

---

### Post by spydon on 2008-02-01
> **taurus said:**
> Open a terminal and download it by hand.

Applications -> Accessories -> Terminal
```
cd ~/Desktop
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
```
When it's done, unpack it and install it.

```

tar xvzf install_flash_player_9_linux.tar.gz
cd cd install_flash_player_9_linux
sudo ./flashplayer-installer
**[COLOR="Blue"]-or-[/COLOR]**
sudo cp libflashplayer.so /usr/lib/firefox/plugins
```

Fire up firefox again and see if flash plugin is on the list.

```
about:plugins
```

```
cd cd install_flash_player_9_linux
```

It is one cd to much, it should be:

```
cd install_flash_player_9_linux
```

---

### Post by Knot_Sharpe on 2008-02-01
> **jan quark said:**
> try my guide it works

[http://janquark.fatfreehost.com/tutorial3.html](http://janquark.fatfreehost.com/tutorial3.html)

Hi, I have 2 files on the desktop and this came out of terminal command:

gary@gary-ibm:~$ ~/Desktop/install_flash_player_9_linux$
bash: /home/gary/Desktop/install_flash_player_9_linux$: No such file or directory
gary@gary-ibm:~$ 

Ideas?

---

### Post by Knot_Sharpe on 2008-02-01
> **jan quark said:**
> try my guide it works

[http://janquark.fatfreehost.com/tutorial3.html](http://janquark.fatfreehost.com/tutorial3.html)

Still around??

Hi, I have 2 files on the desktop and this came out of terminal command:

gary@gary-ibm:~$ ~/Desktop/install_flash_player_9_linux$
bash: /home/gary/Desktop/install_flash_player_9_linux$: No such file or directory
gary@gary-ibm:~$

Ideas?

---

### Post by jan quark on 2008-02-01
type this when you are in the folder into the terminal

```
./configure flashplayer-installer
```

---

### Post by jan quark on 2008-02-01
but you must navigate in the terminal to the folder

it must look like this

```
jan@jan-laptop:~/Desktop/install_flash_player_9_linux$ ./configure flashplayer-installer
```

---

### Post by erfahren on 2008-02-01
@Knot_Sharpe - just do this

if you haven't extracted that Flashplayer .tar.gz archive just right-click on it and select "extract here" and then open the folder that has been extracted.

then open the file browser with root priviledges -  press Alt+F2 and type in
```

gksudo nautilus

```

just copy that libflashplayer.so file and as root, browse to /usr/lib/firefox/plugins and paste it in there

(that's all the installer does basically)

---

### Post by Knot_Sharpe on 2008-02-01
> **jan quark said:**
> but you must navigate in the terminal to the folder

it must look like this

```
jan@jan-laptop:~/Desktop/install_flash_player_9_linux$ ./configure flashplayer-installer
```

This is what I tried .... am I not navigating to the folder with this command? ...

gary@gary-ibm:~$ ~/Desktop/install_flash_player_9_linux$ ./configure flashplayer-installer
bash: /home/gary/Desktop/install_flash_player_9_linux$: No such file or directory
gary@gary-ibm:~$ cd /home/gary/Desktop/install_flash_player_9_linux$
bash: cd: /home/gary/Desktop/install_flash_player_9_linux$: No such file or directory
gary@gary-ibm:~$

Sorry, I don't understand ...

---

### Post by iansane on 2008-02-01
Just wanted to get in on this so I can understand why so many people have a problem at all with flash in firefox.

I opened firefox, went to adobe, they automatically only give option to download linux type (tar.gz, yum, and rpm) . Download and extract tar.gz to the desktop, cd to the directory and type "./flashplayer-installer" in terminal. Hit enter to continue and that's it.

Why is this such a problem? Is it because of 64 bit vs. 32? I don't even know how to tell what this package is. It doesn't say whether it's 64 or 32. I have 64 bit processor but use 32 bit for everything cause I see so many problems people have getting things to work.

Could anyone explain to me what exactly is the problem?

Thanks

---

### Post by erfahren on 2008-02-01
@jan quark - why is there a "./configure" in that command?

(it's only *one* file that's being installed - for 32-bit Ubuntu it's not that complicated)

---

### Post by Knot_Sharpe on 2008-02-01
> **iansane said:**
> Just wanted to get in on this so I can understand why so many people have a problem at all with flash in firefox.

I opened firefox, went to adobe, they automatically only give option to download linux type (tar.gz, yum, and rpm) . Download and extract tar.gz to the desktop, cd to the directory and type "./flashplayer-installer" in terminal. Hit enter to continue and that's it.

Why is this such a problem? Is it because of 64 bit vs. 32? I don't even know how to tell what this package is. It doesn't say whether it's 64 or 32. I have 64 bit processor but use 32 bit for everything cause I see so many problems people have getting things to work.

Could anyone explain to me what exactly is the problem?

Thanks

Thanks for the reply ./... I guess you'll all have to humour me.... I can't seem to understand how to cd to the right directory ...

---

### Post by ICUR2Ys on 2008-02-01
A bug was introduced in flash 9 around the holidays if I remember correctly.  I was having the same problem.  I followed a link and found a work around.  Sorry I can't remember where.  flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb is the name of what I downloaded and installed.  This worked for me.  Maybe you can search and find it.  Good Luck.

---

### Post by Knot_Sharpe on 2008-02-01
Thank you to everyone.
I'm not familiar with the Terminal and couldn't figure out how to navigate the directory structure, don't know why.

I used the file browser window which showed a path (I think) that was  /gary/Desktop/install_flash_player .... there was a tab that I clicked and a button that offered to install ... I clicked and utube seems to work ,,,, not very intuitive .

I do appreciate all the suggestions ... who can suggest a good tutorial on basic linux or ubuntu usage and command for newbs??

Thanks again,
Gary

---

### Post by jan quark on 2008-02-01
sory guys good catch

it must be```
 ./flashplayer-installer
```

---

### Post by jan quark on 2008-02-01
and you navigate using the cd command
and the ls command

see my tutorial

with ls you look what directories are in the folder you are currently
and with cd you change the directory to that folder

and once again I apologize for the mistake

it must be ```
./flashplayer-installer
```

---

### Post by iansane on 2008-02-01
Like I said I don't really understand it, but here's what I did.

1.download the tar.gz from adobe to my desktop
2. right click and extract here
3. right click and rename to "flash" to make it simple
4. Open terminal and type "cd Desktop/flash"  or "cd /home/myname/Desktop/flash" for the full path
5. then type "./flachplayer-installer"
It asks you to close all browser windows and hit enter to continue, then says "success" . I think it asked me to remove a certain file from my home directory after it completed. Actually it said get an administrator to rmove it but I just went there and deleted it. 

I now know that there was some kind of bug,Thanks to ICUR2Ys  but I had no problem with it. I'm useing Gutsy and firefox 2.0.0.11 if that makes any difference. Maybe they fixed the bug. I don't know

---

### Post by wolfen69 on 2008-02-01
double click flashplayer installer and choose open with terminal. the rest is easy.

---

### Post by erfahren on 2008-02-01
> **Knot_Sharpe said:**
> Thank you to everyone.
I'm not familiar with the Terminal and couldn't figure out how to navigate the directory structure, don't know why.

I used the file browser window which showed a path (I think) that was  /gary/Desktop/install_flash_player .... there was a tab that I clicked and a button that offered to install ... I clicked and utube seems to work ,,,, not very intuitive .

I do appreciate all the suggestions ... who can suggest a good tutorial on basic linux or ubuntu usage and command for newbs??

Thanks again,
Gary
you were in the correct directory - but when you entered in that "./configure flashplayer-installer" command bash looked for a file (or directory) named "configure" and couldn't find it. The command was erroneous.

When you open a terminal session it opens in your /home/<username> directory by default. If you entered "pwd" (print working directory) it would reflect that.

The "Desktop" directory is a subdirectory of your /home/<username> (also can be written as "~/Desktop" - the "~/" is a shortcut for your /home/<username>)

with that in mind consider [**taurus's** directions](http://ubuntuforums.org/showpost.php?p=4249499&postcount=8). You first cd into your ~/Desktop directory and download the archive. Then untar it. Then enter into the new folder (or directory) that results from uncompressing the archive. - then type in the "./flashplayer-installer" command which launches the script in that folder.

...but again - all that script does is put the "libflashplayer.so" file in your /usr/lib/firefox/plugins directory - **taurus** put that way too with the:
```

[color="blue"]-or-[/color]
sudo cp libflashplayer.so /usr/lib/firefox/plugins

```

Anyway - for more info on the terminal -
[Terminal for Beginners](http://ubuntuforums.org/showthread.php?t=73885)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[Know Your Terminal Commands, Terminal references](http://ubuntuforums.org/showthread.php?t=171507)

-- sorry for the confusion - I tried to have you just put the file where it needed to go- just using the GUI, but couldn't answer fast enough (apparently).

---

### Post by Knot_Sharpe on 2008-02-01
@ erfahren

Thank you for the extended explanation ... I do see where I was going wrong.  Works well, now.
Thanks too for the links and explaining the directory structure so concisely.  I did use terminal commands, but that was 30 years ago and I've been Windows-lazy ever since.

I loaded Ubuntu so I could start regaining some real knowledge of whats going on under the hood. I didn't realise I would be this far behind, but ... onward we go!

Kindest Regards,
Gary

---

