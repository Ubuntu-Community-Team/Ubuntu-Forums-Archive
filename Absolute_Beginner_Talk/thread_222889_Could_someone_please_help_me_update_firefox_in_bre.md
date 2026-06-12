---
title: "Could someone please help me update firefox in breezy..??"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by jason.b.c on 2006-07-25
[I followed these instructions]("http://http://ubuntuforums.org/showthread.php?t=137243") but it won't update..!   Why.?

Could someone help me please.?

---

### Post by jason.b.c on 2006-07-25
I just tried it again , It still won't update.?

---

### Post by jason.b.c on 2006-07-25
*Bump*

---

### Post by avtolle on 2006-07-25
What didn't work? It would be helpful if you could post any error messages you received, so someone can look at them and help from there.

---

### Post by aysiu on 2006-07-25
Use [this script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5).

---

### Post by jason.b.c on 2006-07-25
> **aysiu said:**
> Use [this script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5).

> Ubuntu 5.10 comes with Firefox 1.0.7. Unfortunately, 1.0.7 is quite sluggish, lacks some features, and the newest extensions don't work with it anymore. There are no plans to backport 1.5. Looks like you just have to wait until the next release of Ubuntu comes out, doesn't it? Lucky for us, all is not lost! This page on the Ubuntu wiki spills the beans on how to get the new firefox going.

As an alternative to following the wiki instructions, you can use this script that will automatically download and install the new firefox for you. I created it in collaboration with Aysiu, who helped with testing, ideas, and motivation. It automatically detects the newest firefox release, allows you to make a choice of language for firefox, verifies the gpg signature, and installs the new firefox in /opt/firefox. Here are the steps to take to use this script:

    * Download the script to your desktop
    * Open a terminal (how?)
    * Enter these commands: 

cd Desktop
chmod +x installnewfirefox.sh
./installnewfirefox.sh

And, if no errors occur, your new firefox is ready for use!

One little trick: middle click on tab to close it does not work by default on firefox. To enable it, point firefox to "about:config" and set middleclick.contentloadURL to false. Voila, middle click to close works again. 

Yea i tried that one..

But it didn't work , I open the terminal and paste the command into it and press enter , The the terminal display's a bunch of stuff, ask's me a few question's wich i answer and then it starts doing what i thought was installing firefox.

Then the terminal closes and nothing happens..!   Firefox isn't updated.! , It's not open and running when i try this..Also i've tried it with firefox open as well . Nothing.!

I open firefox and go to **help** then **about** and it still say's v1.0.7  ...

So what am i doing wrong..???   I can't paste what the terminal say's because when i highlite and choose **Copy** and then try to paste it in here i don't have paste option to do so....

---

### Post by aysiu on 2006-07-25
It's difficult to help you without seeing the terminal output.

Are you closing the terminal before you try to paste?

---

### Post by jason.b.c on 2006-07-25
> **aysiu said:**
> It's difficult to help you without seeing the terminal output.

Are you closing the terminal before you try to paste?

Should I..???


That is if it wasn't closing before i can do anything...

The terminal closes and exits like the install completed but it hasn't , No update installed..

---

### Post by jason.b.c on 2006-07-25
Well it still won't install..

```
jason@Hp-Vectra-VL:~$ cd Desktop
jason@Hp-Vectra-VL:~/Desktop$ chmod +x installnewfirefox.sh
chmod: cannot access `installnewfirefox.sh': No such file or directory
jason@Hp-Vectra-VL:~/Desktop$ ./installnewfirefox.sh



```

Now what do i do..???

---

### Post by jason.b.c on 2006-07-25
Now when i double click on the script it opens the terminal and now not even it does anything , The terminal just sit's there with the cursor blinking...

---

### Post by aysiu on 2006-07-25
Is *installnewfirefox.sh* actually on your desktop?

What's the output of these commands? ```
cd ~/Desktop
ls -al
```

---

### Post by jason.b.c on 2006-07-25
> **aysiu said:**
> Is *installnewfirefox.sh* actually on your desktop?

What's the output of these commands? ```
cd ~/Desktop
ls -al
```

Yes . , So is the firefox package.

```
jason@Hp-Vectra-VL:~$ cd ~/Desktop
jason@Hp-Vectra-VL:~/Desktop$ Is -aI
bash: Is: command not found
jason@Hp-Vectra-VL:~/Desktop$ ls -al
total 8316
drwxr-xr-x   2 jason jason    4096 2006-07-25 20:59 .
drwxr-xr-x  38 jason jason    4096 2006-07-25 18:50 ..
-rw-r--r--   1 jason jason    3443 2005-09-29 05:18 blah-001cefdfe0.desktop
-rw-r--r--   1 jason jason    1401 2006-07-23 23:03 evolution-mail.desktop
-rw-r--r--   1 jason jason 8460561 2006-07-25 20:41 firefox-1.5.0.4.tar.gz
-rw-r--r--   1 jason jason    1980 2006-07-25 03:21 firefox.desktop
-rw-r--r--   1 jason jason    5369 2006-07-25 20:59 installnewfirefox.sh
-rw-r--r--   1 jason jason    5176 2005-09-18 15:38 yelp.desktop
jason@Hp-Vectra-VL:~/Desktop$


```

---

### Post by aysiu on 2006-07-25
I don't know. That's a big mystery to me.

*installnewfirefox.sh* is clearly on your desktop, and the terminal clearly responded back that it *wasn't* on your desktop. I'm not sure what to do...

I guess you'll have to do it manually, since we can't get that script recognized:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by jason.b.c on 2006-07-25
> **aysiu said:**
> I don't know. That's a big mystery to me.

*installnewfirefox.sh* is clearly on your desktop, and the terminal clearly responded back that it *wasn't* on your desktop. I'm not sure what to do...

I guess you'll have to do it manually, since we can't get that script recognized:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

Wow.!  I have no idea how to do any of that..?

---

### Post by aysiu on 2006-07-25
> **jason.b.c said:**
> Wow.!  I have no idea how to do any of that..?
Which is why that script was created!

Really, it's just copying and pasting commands. Highlight. Copy (Control-C). Paste (Shift-Insert).

What are you doing on Breezy, by the way?

---

### Post by jason.b.c on 2006-07-25
Is there any other browser that i could get that would be alot easier to install.??

---

### Post by jason.b.c on 2006-07-25
> What are you doing on Breezy, by the way?

What do you mean..??

Why am i using it..???

---

### Post by aysiu on 2006-07-25
Breezy came out in October 2005. Dapper came out in June 2006.

Yes, why are you using Breezy?

If you don't want Firefox installed "properly," you can just unzip the .tar.gz (double-click and **Extract**) and double-click the *firefox* file.

---

### Post by jason.b.c on 2006-07-25
> **aysiu said:**
> Breezy came out in October 2005. Dapper came out in June 2006.

Yes, why are you using Breezy?



Because i can't in no way what-so-ever use Dapper.

It refuses to stop shutting down/Hibernating my computer when i don't even want hibernation enabled..

It was driving me crazy..!

Everybody told me to **"Just slide the sliders all the way to the right"** But that did not work even in the slightest..

So i gave up on it and installed breezy..At least it stays on all night without trouble there.

---

### Post by jason.b.c on 2006-07-25
Wait, Why is this output differant now..??


```
jason@Hp-Vectra-VL:~$ cd ~/Desktop
jason@Hp-Vectra-VL:~/Desktop$ ls -al
total 8320
drwxr-xr-x   3 jason jason    4096 2006-07-25 21:13 .
drwxr-xr-x  40 jason jason    4096 2006-07-25 21:50 ..
-rw-r--r--   1 jason jason    3443 2005-09-29 05:18 blah-001cefdfe0.desktop
-rw-r--r--   1 jason jason    1401 2006-07-23 23:03 evolution-mail.desktop
drwxr-xr-x   2 jason jason    4096 2006-07-25 21:13 ffsettings
-rw-r--r--   1 jason jason 8460561 2006-07-25 20:41 firefox-1.5.0.4.tar.gz
-rw-r--r--   1 jason jason    1980 2006-07-25 03:21 firefox.desktop
-rwxr-xr-x   1 jason jason    5369 2006-07-25 20:59 installnewfirefox.sh
-rw-r--r--   1 jason jason    5176 2005-09-18 15:38 yelp.desktop
jason@Hp-Vectra-VL:~/Desktop$

```

Or isn't it.???

---

### Post by jason.b.c on 2006-07-27
I would still like to figure this one out if someone would be willing to help...

Thanks...:D

---

### Post by aysiu on 2006-07-27
So right after that terminal output... what happens when you do this again? ```
./installnewfirefox.sh
```

---

### Post by jason.b.c on 2006-07-27
> **aysiu said:**
> So right after that terminal output... what happens when you do this again? ```
./installnewfirefox.sh
```

```
jason@Hp-Vectra-VL:~$ cd ~/Desktop
jason@Hp-Vectra-VL:~/Desktop$ ls -al
total 8324
drwxr-xr-x   3 jason jason    4096 2006-07-25 21:58 .
drwxr-xr-x  44 jason jason    4096 2006-07-27 20:18 ..
-rw-r--r--   1 jason jason    3443 2005-09-29 05:18 blah-001cefdfe0.desktop
-rw-------   1 jason jason    2460 2006-07-25 21:58 Commands
-rw-------   1 jason jason       0 2006-07-25 21:58 Commands~
-rw-r--r--   1 jason jason    1401 2006-07-23 23:03 evolution-mail.desktop
drwxr-xr-x   2 jason jason    4096 2006-07-25 21:13 ffsettings
-rw-r--r--   1 jason jason 8460561 2006-07-25 20:41 firefox-1.5.0.4.tar.gz
-rw-r--r--   1 jason jason    2008 2006-07-26 00:50 firefox.desktop
-rwxr-xr-x   1 jason jason    5369 2006-07-25 20:59 installnewfirefox.sh
-rw-r--r--   1 jason jason    5176 2005-09-18 15:38 yelp.desktop
jason@Hp-Vectra-VL:~/Desktop$ ./installnewfirefox.sh
The most recent release of firefox is detected to be 1.5.0.5. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.com/) Is it correct [y/n]? y
Please choose the localization (language) for firefox. Enter the number of your choice from the list below.
0: ar
1: bg
2: ca
3: cs
4: da
5: de
6: el
7: en-GB
8: en-US
9: es-AR
10: es-ES
11: eu
12: fi
13: fr
14: fy-NL
15: ga-IE
16: gu-IN
17: he
18: hu
19: it
20: ja
21: ko
22: lt
23: mk
24: mn
25: nb-NO
26: nl
27: pa-IN
28: pl
29: pt-BR
30: ro
31: ru
32: sk
33: sl
34: sv-SE
35: tr
36: zh-CN
37: zh-TW
Enter your choice of localization: 8
You have chosen localization "en-US". Is that correct [y/n]? y

Updating repositories list

Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Ign http://wine.budgetdedicated.com breezy Release.gpg
Hit http://wine.budgetdedicated.com breezy Release
Ign http://wine.budgetdedicated.com breezy/main Packages
Hit http://wine.budgetdedicated.com breezy/main Packages
Get:1 http://us.archive.ubuntu.com breezy Release.gpg [189B]
Hit http://us.archive.ubuntu.com breezy Release
Ign http://us.archive.ubuntu.com breezy/universe Packages
Hit http://us.archive.ubuntu.com breezy/main Packages
Hit http://us.archive.ubuntu.com breezy/restricted Packages
Ign http://us.archive.ubuntu.com breezy/universe Packages
Get:2 http://us.archive.ubuntu.com breezy/universe Packages [3028kB]
99% [2 Packages gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com breezy/universe Packages
  Sub-process gzip returned an error code (1)
Get:3 http://us.archive.ubuntu.com breezy/universe Packages [3028kB]
99% [Working]
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com breezy/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 3B in 11s (0B/s)
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done

Making sure libstdc++5 and the old Firefox are installed

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
The following packages have been kept back:
  cpp cpp-4.0
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done

Backing up old Firefox preferences


Changing to home directory


Downloading Firefox from the Mozilla site

--22:19:01--  http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.5/linux-i686/en-US/firefox-1.5.0.5.tar.gz
           => `firefox-1.5.0.5.tar.gz'
Resolving ftp.mozilla.org... 63.245.208.138
Connecting to ftp.mozilla.org|63.245.208.138|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://releases.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.5/linux-i686/en-US/firefox-1.5.0.5.tar.gz [following]
--22:19:02--  http://releases.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.5/linux-i686/en-US/firefox-1.5.0.5.tar.gz
           => `firefox-1.5.0.5.tar.gz'
Resolving releases.mozilla.org... 156.56.247.196, 216.165.129.141, 64.12.204.21, ...
Connecting to releases.mozilla.org|156.56.247.196|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.


Downloading Firefox signature from the Mozilla site

--22:19:04--  http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.5/linux-i686/en-US/firefox-1.5.0.5.tar.gz.asc
           => `firefox-1.5.0.5.tar.gz.asc'
Resolving ftp.mozilla.org... 63.245.208.138
Connecting to ftp.mozilla.org|63.245.208.138|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://releases.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.5/linux-i686/en-US/firefox-1.5.0.5.tar.gz.asc [following]
--22:19:05--  http://releases.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.5/linux-i686/en-US/firefox-1.5.0.5.tar.gz.asc
           => `firefox-1.5.0.5.tar.gz.asc'
Resolving releases.mozilla.org... 156.56.247.196, 216.165.129.134, 216.165.129.141, ...
Connecting to releases.mozilla.org|156.56.247.196|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 186 [text/plain]

100%[====================================>] 186           --.--K/s

22:19:06 (4.55 MB/s) - `firefox-1.5.0.5.tar.gz.asc' saved [186/186]


Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: requesting key 1AF32821 from hkp server subkeys.pgp.net
gpg: key 0E3606D9: "Mozilla Software Releases <releases@mozilla.org>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Tue 25 Jul 2006 09:48:06 PM CDT using DSA key ID 1AF32821
gpg: BAD signature from "Mozilla Software Releases <releases@mozilla.org>"
Previous command did not complete successfully. Exiting.
jason@Hp-Vectra-VL:~/Desktop$

```

I've already downloaded it..

Does this mean it's installed now..???

---

### Post by jason.b.c on 2006-07-27
> Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)

Nope..!  Guess not...

---

### Post by nanotube on 2006-07-28
> **jason.b.c said:**
> ```

gpg: Signature made Tue 25 Jul 2006 09:48:06 PM CDT using DSA key ID 1AF32821
gpg: BAD signature from "Mozilla Software Releases <releases@mozilla.org>"
Previous command did not complete successfully. Exiting.
jason@Hp-Vectra-VL:~/Desktop$

```

I've already downloaded it..

Does this mean it's installed now..???

as you can see at the end of the output, the gpg signature didn't match, so the install did not complete. so, delete firefox tar.gz and firefox-1.5.0.5.tar.gz and firefox-1.5.0.5.tar.gz.asc from your home directory (/home/jason), and then run the script again. because apparently the download got corrupted in the process.

---

