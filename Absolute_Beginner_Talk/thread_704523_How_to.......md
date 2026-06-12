---
title: "How to......"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by RavenStandsAlone on 2008-02-22
Total newbie here. 

How do I find the command prompt to run an installer?

Raven

:confused:

---

### Post by taurus on 2008-02-22
Are you trying to install Ubuntu from the LiveCD?  If it is, then there is an icon on your desktop that says *install*.  Click on that.

---

### Post by billgoldberg on 2008-02-22
If you are reffering to the terminal aka the command line interface:

"applications ->accessories"

---

### Post by dca on 2008-02-22
From the panel:  Applications -> Accessories -> Terminal
 
...if that's what you're talking about...

---

### Post by billgoldberg on 2008-02-22
If you post what you want to install people will be able to give you better instructions.

---

### Post by RavenStandsAlone on 2008-02-22
> **billgoldberg said:**
> If you post what you want to install people will be able to give you better instructions.

I want to install Adobe FlashPlayer and it tells me:  To install the Standalone Player for Linux:



- This installer is script-based and cannot be run from a GUI.

- Uncompress install_flash_player_6_linux_sa.tar.gz.  A directory called install_flash_player_6_linux_sa is created.  Navigate to this directory.

- From the command line, type ./flashplayer-installer to run the installer.  For root users, gflashplayer will be copied to /usr/bin. For non-root users, it will be copied to a folder named bin in your home directory.

Is that enough?

Thanks for the quick responses by the by,

Raven

---

### Post by taurus on 2008-02-22
Assuming you have downloaded and save install_flash_player_6_linux_sa.tar.gz to your Desktop directory.  Open a terminal and run

Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvzf install_flash_player_6_linux_sa.tar.gz
cd install_flash_player_6_linux_sa
sudo ./flashplayer-installer
```

---

### Post by RavenStandsAlone on 2008-02-22
> **taurus said:**
> Assuming you have downloaded and save install_flash_player_6_linux_sa.tar.gz to your Desktop directory.  Open a terminal and run

Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvzf install_flash_player_6_linux_sa.tar.gz
cd install_flash_player_6_linux_sa
sudo ./flashplayer-installer
```

It is not on my desktop, it is in a folder called TMP that I have no clue whatsoever as to where it is located. When I ran the applications > accessories > Terminal I got a dialogue box that opened with; "raven@ubuntu2:~$" and a blinking cursor. Then what next?

---

### Post by taurus on 2008-02-22
You don't even know where that directory, TMP, is?  Run this command from a terminal, that blinking cursor, and post the output here.

```
find . -name install_flash_player_6_linux_sa.tar.gz -print
```

---

### Post by bodhi.zazen on 2008-02-22
Try starting a thread with a more appropriate title.

	> How to......

	Is not a very descriptive title. Who wants to click on that title to see what it is about ???

	See this link.

	[http://ubuntuforums.org/showthread.php?t=700739](http://ubuntuforums.org/showthread.php?t=700739)

---

### Post by RavenStandsAlone on 2008-02-22
> **taurus said:**
> You don't even know where that directory, TMP, is?  Run this command from a terminal, that blinking cursor, and post the output here.

```
find . -name install_flash_player_6_linux_sa.tar.gz -print
```

Okay: 

raven@Ubuntu2:~$ find . - name install_flash_player_6_linux_sa.tar.gz -print
find: invalid predicate `- '
raven@Ubuntu2:~$ 

and then nothing happened. It was just the blinking cursor again.

You need to tell me exactly what to put in that box. Better yet, exactly what the box should look like before I hit  "enter."

Okay, next?

---

### Post by NullHead on 2008-02-22
> **RavenStandsAlone said:**
> Total newbie here. 

How do I find the command prompt to run an installer?

Raven

:confused:

Ok you're trying to install flash player and don't know where it got downloaded to. Well re-download it to your home directory with this command:```
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
```
Then follow the instructions taurus gave; ```
tar xvzf tar -xvzf install_flash_player_9_linux.tar.gz 
cd install_flash_player_9_linux
sudo ./flashplayer-installer
```

---

### Post by steveneddy on 2008-02-22
> **RavenStandsAlone said:**
> Uh, the three people who have contributed positively to this thread instead of being judgemental. I know absolutely nothing about Linux iterations. Telling me to open a command prompt that is not called "command prompt" but is called "terminal" instead is useless.

:confused:

See? told ya.

---

### Post by seventhc on 2008-02-22
Hi RavenStandsAlone,
how about we make it work with this post..
1: first, we will start from scratch.
so go [here ]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz")and download the file 

2: don't save it, tell it to open with 'Archive Manager'

3: extract it to your desktop

4:open a terminal..go to [I]Applications>Accessories>Terminal
[/I]when that opens paste this in
5:cd Desktop/install_flash_player_9_linux
then run this
6:./flashplayer-installer
during the install it will ask you to close all open browsers, close them and say yes..

---

### Post by terry_gardener on 2008-02-22
raven 

since you said that you have extracted to the tmp folder.

goto terminal via applications select accessories then click terminal. 

type: cd /
then: cd tmp
then ./flashplayer-installer
press enter.

follow onscreen instructions. 

if this doesn't work goto website. 
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

click the tar.gz file under option 1. 
then leave it on open and click ok. 
archive manager should open click extract and then in the new window click raven and click extract. 

open terminal as descrbed above and type "./flashplayer-installer" and press enter and follow on-screen instructions. 

hope this helps

---

### Post by RavenStandsAlone on 2008-02-22
> **terry_gardener said:**
> raven 

since you said that you have extracted to the tmp folder.

goto terminal via applications select accessories then click terminal. 

type: cd /
then: cd tmp
then ./flashplayer-installer
press enter.

follow onscreen instructions. 

if this doesn't work goto website. 
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

click the tar.gz file under option 1. 
then leave it on open and click ok. 
archive manager should open click extract and then in the new window click raven and click extract. 

open terminal as descrbed above and type "./flashplayer-installer" and press enter and follow on-screen instructions. 

hope this helps


This is what I have so far;

"raven@Ubuntu2:~$ cd/
bash: cd/: No such file or directory
raven@Ubuntu2:~$ cd /
raven@Ubuntu2:/$ cd tmp
raven@Ubuntu2:/tmp$ ./flashplayer-installer
bash: ./flashplayer-installer: No such file or directory
raven@Ubuntu2:/tmp$ install_flash_player_6_r79_linux_sa.tar.gz
bash: install_flash_player_6_r79_linux_sa.tar.gz: command not found
raven@Ubuntu2:/tmp$ install_flash_player_6_linux_sa
bash: install_flash_player_6_linux_sa: command not found
raven@Ubuntu2:/tmp$ install_flash_player_6_linux_sa/flashplayer-installer

ERROR: Your architecture, \'ppc\', is not supported by the
       Macromedia Flash Player installer.

raven@Ubuntu2:/tmp$"

That did nothing also. I did experiment with various commands following the path to the tmp folder.

---

### Post by terry_gardener on 2008-02-22
please try the 2nd part of my post and reply with the results. 

start from where it saysd if this doesn't work......

---

### Post by NullHead on 2008-02-22
> **RavenStandsAlone said:**
> This is what I have so far;

"raven@Ubuntu2:~$ cd/
bash: cd/: No such file or directory
raven@Ubuntu2:~$ cd /
raven@Ubuntu2:/$ cd tmp
raven@Ubuntu2:/tmp$ ./flashplayer-installer
bash: ./flashplayer-installer: No such file or directory
raven@Ubuntu2:/tmp$ install_flash_player_6_r79_linux_sa.tar.gz
bash: install_flash_player_6_r79_linux_sa.tar.gz: command not found
raven@Ubuntu2:/tmp$ install_flash_player_6_linux_sa
bash: install_flash_player_6_linux_sa: command not found
raven@Ubuntu2:/tmp$ install_flash_player_6_linux_sa/flashplayer-installer

ERROR: Your architecture, \'ppc\', is not supported by the
       Macromedia Flash Player installer.

raven@Ubuntu2:/tmp$"

That did nothing also. I did experiment with various commands following the path to the tmp folder.
Try this command:```
sudo apt-get install flashplugin-nonfree
```

---

### Post by RavenStandsAlone on 2008-02-22
> **RavenStandsAlone said:**
> This is what I have so far;

"raven@Ubuntu2:~$ cd/
bash: cd/: No such file or directory
raven@Ubuntu2:~$ cd /
raven@Ubuntu2:/$ cd tmp
raven@Ubuntu2:/tmp$ ./flashplayer-installer
bash: ./flashplayer-installer: No such file or directory
raven@Ubuntu2:/tmp$ install_flash_player_6_r79_linux_sa.tar.gz
bash: install_flash_player_6_r79_linux_sa.tar.gz: command not found
raven@Ubuntu2:/tmp$ install_flash_player_6_linux_sa
bash: install_flash_player_6_linux_sa: command not found
raven@Ubuntu2:/tmp$ install_flash_player_6_linux_sa/flashplayer-installer

ERROR: Your architecture, \'ppc\', is not supported by the
       Macromedia Flash Player installer.

raven@Ubuntu2:/tmp$"

That did nothing also. I did experiment with various commands following the path to the tmp folder.

So, apparently I found the correct command parameters but have the wrong version for this CPU architecture. PowerPC 400 MHz, iMac G3, 512MB RAM, 40Gigabyte HDD.

What say ye now gentlemen?

---

### Post by lespaul_rentals on 2008-02-22
> **NullHead said:**
> Try this command:```
sudo apt-get install flashplugin-nonfree
```

+1 to NullHead.

---

### Post by terry_gardener on 2008-02-22
looking at the system requirements for flash 9 they are powerpc 500mhz g3 128mb ram. 

[http://www.adobe.com/products/flashplayer/productinfo/systemreqs/](http://www.adobe.com/products/flashplayer/productinfo/systemreqs/)

this might be the problem cpu is purely not fast enough since you have 400mhz cpu. 

Thats my guess

---

### Post by NullHead on 2008-02-22
Hmm...  a search [here]("http://packages.ubuntu.com") shows that there is no plugin for ppc. See [this]("http://packages.ubuntu.com/search?keywords=flashplugin-nonfree&searchon=names&suite=gutsy&section=all") search.

---

### Post by RavenStandsAlone on 2008-02-22
> **seventhc said:**
> Hi RavenStandsAlone,
how about we make it work with this post..
1: first, we will start from scratch.
so go [here ]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz")and download the file 

2: don't save it, tell it to open with 'Archive Manager'

3: extract it to your desktop

4:open a terminal..go to [I]Applications>Accessories>Terminal
[/I]when that opens paste this in
5:cd Desktop/install_flash_player_9_linux
then run this
6:./flashplayer-installer
during the install it will ask you to close all open browsers, close them and say yes..

That came real close. This was the result of that procession:

raven@Ubuntu2:~$ cd Desktop/install_flash_player_9_linux
raven@Ubuntu2:~/Desktop/install_flash_player_9_linux$ ./flashplayer-installer

ERROR: Your architecture, \'ppc\', is not supported by the
       Adobe Flash Player installer.

raven@Ubuntu2:~/Desktop/install_flash_player_9_linux$

---

### Post by NullHead on 2008-02-22
Anyone think he should try gnash?

---

### Post by terry_gardener on 2008-02-22
cant hurt trying gnash, from the min system requirements on adobe website says it needs 500mhz cpu and he only has 400mhz. which is why i think he is getting the error.

---

### Post by NullHead on 2008-02-22
Same here.

Try this set of comands,Raven.

```
sudo apt-get install gnash mozilla-plugin-gnash
```

---

### Post by RavenStandsAlone on 2008-02-22
> **NullHead said:**
> Same here.

Try this set of comands,Raven.

```
sudo apt-get install gnash mozilla-plugin-gnash
```

raven@Ubuntu2:~$ sudo apt-get install gnash mozilla-plugin-gnash
Password:
Sorry, try again.
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gnash
raven@Ubuntu2:~$

---

### Post by terry_gardener on 2008-02-22
can you check 2 things for me please raven. 

goto system administration and click software sources. in the first tab ubuntu software make sure that there is a tick in the community maintained open source software (universe) 

click close if it asks you to reload click reload. 

open synaptic package manager and type in your password. click the search button and type gnash. 

if you can see it in there right click gnash and click mark for installation. and then right click mozilla-plugin-gnash and click mark for installation. then click apply. 

note: if it asked for to mark other software aswell click ok. 

please post results.

---

### Post by RavenStandsAlone on 2008-02-22
> **terry_gardener said:**
> can you check 2 things for me please raven. 

goto system administration and click software sources. in the first tab ubuntu software make sure that there is a tick in the community maintained open source software (universe) 

click close if it asks you to reload click reload. 

open synaptic package manager and type in your password. click the search button and type gnash. 

if you can see it in there right click gnash and click mark for installation. and then right click mozilla-plugin-gnash and click mark for installation. then click apply. 

note: if it asked for to mark other software aswell click ok. 

please post results.

1. There is no "software sources." There is a link marked "Software properties."
2. There is no "Ubuntu software" tab either. The first tab in Software Properties is "Installation Media."
3. There is no "community maintained open source software (universe)
4. There are lines with check boxes. Such as; "Ubuntu 6.06 LTS (Binary) Community maintained (Universe)" and "Ubuntu 6.06 LTS (Source) Community maintained (Universe)" etc.

"note: if it asked for to mark other software aswell click ok." Does that mean "If it asks for you to mark "Other Software" as well, click "Ok?"

One of the things I do know about computers is that if you misspell or mis-capitalize it counts for nothing. You have to be very specific and you must spell all of the words correctly. There is no "almost got it right" in binary! 

I don't want to be percieved as an assh__e, I only want questions answered precisely, the way that I am asking! When the opportunity occurs for me to assist someone on PC I do not send instructions like: "click on the little thingie with the C:\ and put in regedut/ficks and expect the person reading that to have any clue as to what it should read like" c:\ regedit/fix."

---

### Post by RavenStandsAlone on 2008-02-22
> **terry_gardener said:**
> can you check 2 things for me please raven. 

goto system administration and click software sources. in the first tab ubuntu software make sure that there is a tick in the community maintained open source software (universe) 

click close if it asks you to reload click reload. 

open synaptic package manager and type in your password. click the search button and type gnash. 

if you can see it in there right click gnash and click mark for installation. and then right click mozilla-plugin-gnash and click mark for installation. then click apply. 

note: if it asked for to mark other software aswell click ok. 

please post results.


And I do appreciate the effort.

"if you can see it in there right click gnash and click mark for installation. and then right click mozilla-plugin-gnash and click mark for installation. then click apply." You must have missed where I said that I was working on an iMac G3. There is only one button on the mouse. How do you propose that I "right click?"

---

### Post by aysiu on 2008-02-22
As the OP has [decided to no longer post on these forums](http://ubuntuforums.org/showpost.php?p=4384464&postcount=23), there's no point in this thread continuing, so I'm closing it.

---

