---
title: "[SOLVED] Brand New User"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by cinnamonbuntu on 2008-04-18
I've been putting off this post for about 2 days cause I know how hugely noobtastic it will make me look, but I've passed the point of caring. So Heres a few brand new person questions:

How do I extract tarballs? 
I've been using the command tar -xvzf filenamehere but it always tells me that the specific filename ive named doesnt exist. I've tried downloading them to home, desktop, and my personal user file. I switched to whichever directory i put them in with cd directory commands before attempting to detar but it hasn't worked once on a single file, so clearly I'm doing something wrong. 

How do I get root level access?
So far I've only performed a few actions that denied me access because of non-root status, but theres been several install guides that just say "install it as root" and no one knew (most likely) really knows how to do that. I own the PC in question, I install the OS, so i can log root. I just don't know how.

How would I install a driver made specifically for Linux?
I have a realtek wireless card, theres a linux driver available from realtek themselves, I've downloaded it, and I have no clue what to do from there. I've followed readme instructions but it just repeats the same error for about 15 seconds or 100 or so lines of code then closes itself. Theres too much happening too fast to read it well. I'm assuming that if I knew what I was doing I could get it installed. Perhaps I'm just reading the readme too literally. 

I've read up on a lot of basic commands and what not from how to's and guides while I was researching what version of Linux I wanted, but I just can't find anything that tells me what to do when tar doesn't work for you, or how to install a single driver. 

TY to all who reply to this.

P.S. Any good guides that you can supply to help me learn. Ideally I'd like to be answering more and asking less on these forums.

---

### Post by Tomatz on 2008-04-18
1 If you like gui's then just r-click on the tar and extract here. Or to use the **cli** (command line interface) change to the directory the tar is located. I assume the tar was on the **desktop** so the problem was that in the terminal you were in your **home** folder. All you needed to do was:

**cd ~/Desktop**

then 

**tar -xvfz filenamehere** [COLOR="Red"][edit hehe didn't see that thanks hyper!][/COLOR]

2 To get root access type **sudo** in front of the command then type your password e.g.

**sudo nautilus**

*This will open the file manager with root privileges *

3 Read the wiki's, howto's and readme (the latter usually located in the archive with the driver). Or ask on the forums ;)

---

### Post by Mick8882003 on 2008-04-18
take a look at my wiki, and some of the links off it, answer a few questions.

---

### Post by hyper_ch on 2008-04-18
> **cinnamonbuntu said:**
> How do I extract tarballs?
```

tar xvfz FILENAME

```

> **cinnamonbuntu said:**
> How do I get root level access?
Prepend commands with "sudo" [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> **cinnamonbuntu said:**
> How would I install a driver made specifically for Linux?
What do the instructions say, where does something go wrong? You can put the output on the screen into a file by appending at the end a "> /path/to/file.log"

> **cinnamonbuntu said:**
> I've read up on a lot of basic commands and what not from how to's and guides while I was researching what version of Linux I wanted, but I just can't find anything that tells me what to do when tar doesn't work for you, or how to install a single driver.
If hardware doesn't work out of the box then you can face some serious problems. You are lucky if the manufactuere provides linux drivers.


> **cinnamonbuntu said:**
> P.S. Any good guides that you can supply to help me learn. Ideally I'd like to be answering more and asking less on these forums.
[http://www.psychocats.net](http://www.psychocats.net)
[http://www.ubuntuguide.org](http://www.ubuntuguide.org)
[https://wiki.ubuntu.com](https://wiki.ubuntu.com)
[http://www.linuxcommand.org](http://www.linuxcommand.org)

---

### Post by christianxxx on 2008-04-18
> **cinnamonbuntu said:**
> I've been putting off this post for about 2 days cause I know how hugely noobtastic it will make me look, but I've passed the point of caring. So Heres a few brand new person questions:

There's no such thing as a noob question, we have all been there before, or are noobs ourself.

> 
How do I extract tarballs? 
I've been using the command tar -xvzf filenamehere but it always tells me that the specific filename ive named doesnt exist. 
 
Your method is really the only one I use, but remember Linux is case-sensitiv. To make sure you get the correct filename, type only the first few letters and use TAB-key to complete the name. If it won't complete the name, the location might be wrong or wrong casing on the first letters.

> 
How do I get root level access?
So far I've only performed a few actions that denied me access because of non-root status, but theres been several install guides that just say "install it as root" and no one knew (most likely) really knows how to do that. I own the PC in question, I install the OS, so i can log root. I just don't know how.

For terminal, use:
```
sudo *command*
```
You can also initiate Gui-programs from the terminal using ```
gksudo *command*
```, or just initiate from Gui. Any method will require your password, given that you account has admin (root) privileges.

> 
How would I install a driver made specifically for Linux?
I have a realtek wireless card, theres a linux driver available from realtek themselves, I've downloaded it, and I have no clue what to do from there. I've followed readme instructions but it just repeats the same error for about 15 seconds or 100 or so lines of code then closes itself. Theres too much happening too fast to read it well. I'm assuming that if I knew what I was doing I could get it installed. Perhaps I'm just reading the readme too literally. 

I actually gave up on the realtek drivers and used ndiswrapped with the windows drivers. There should be plenty of threads with howto's on ndiswrapper.

> 
I've read up on a lot of basic commands and what not from how to's and guides while I was researching what version of Linux I wanted, but I just can't find anything that tells me what to do when tar doesn't work for you, or how to install a single driver. 

[http://ubuntuguide.org]("http://ubuntuguide.org") is wonderful, but I also recommend the ubuntu-wiki, [http://help.ubuntu.com/community]("http://help.ubuntu.com/community")

Have fun!

---

### Post by cinnamonbuntu on 2008-04-18
Thanks guys. Gave those a reread. Saw them before, but only breezed through em before. I wasn't in the wrong directory. Good to know what I've been doing so far though haha. I've been using the **** out of sudo whenever I was getting a permission issue because I read somewhere that did that. Just didn't know why. Alright suppose I'll get a bit more in depth in my questioning.

I'm in the same location for every file I'm trying to unpack, and install. The main issue I'm having now, is the driver problem.

Ndiswrapper is now installed. 

Sudo Ndiswrapper -l returns absolutely nothing. It just opens a fresh command line.

Sudo Ndiswrapper -i /desktop/net8185.inf returns:
 couldn't open net8185.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219

I find this strange as I'm not currently in that directory and I'm specifying which directory the file is in. So I'm wondering if it has something to do with my phrasing. I've followed several very well written how-to's on the subject of ndiswrapper, and regardless I get this same error when following the guild verbatim.


I also have a linux driver, but haven't got the foggiest when it comes to how to go about adding that. I went to System->Preferences->Hardware Settings  just now as was suggested by one guide to check my driver via GUI, and in a shocking new developement! Theres no such place. There was something there along those lines when I was using the Live CD, but theres a lot of stuff that is missing from the live CD, now that I have a real version installed for some reason. 

Anyway basically the last noob thing I need to know for now is "how do I install drivers?" So far I've followed the readme instructions, and a how-to to no avail.

Heres the readme:
Running the scripts can finish all operations of building up modules from source code and start the nic:

	(1)Build up the driver from the source code
         	./makedrv

    	(2)Load the driver module to kernel and start up nic
    		./wlan0up
           (if "insmod: error inserting 'r8180.ko': -File exists." met,
	        ./wlan0rmv
		./wlan0down
		./wlan0up
	    should be OK.

Followed those, and just closes the terminal instantly no matter what I try.

EDIT: multiple people posted while I was writing this out, so I'd like to thank you guys as well, and I've had to add some new wiki's and sites to my "list of things to read" haha.

Edit2: Heres the outcome of ./makedrv

./ieee80211/
./ieee80211/ieee80211_module.c
./ieee80211/ieee80211_rx.c
./ieee80211/tags
./ieee80211/Makefile
./ieee80211/ieee80211_crypt_tkip.c
./ieee80211/ieee80211_softmac.c
./ieee80211/readme
./ieee80211/ieee80211_crypt_ccmp.c
./ieee80211/ieee80211.h
./ieee80211/ieee80211_tx.c
./ieee80211/ieee80211_softmac_wx.c
./ieee80211/ieee80211_crypt.h
./ieee80211/ieee80211_wx.c
./ieee80211/license
./ieee80211/ieee80211_crypt_wep.c
./ieee80211/ieee80211_crypt.c
rtl8185/
rtl8185/README.adhoc
rtl8185/r8180_sa2400.h
rtl8185/Makefile
rtl8185/copying
rtl8185/README.master
rtl8185/r8180.h
rtl8185/install
rtl8185/r8180_max2820.h
rtl8185/r8180_max2820.c
rtl8185/r8180_rtl8225.h
rtl8185/r8180_wx.h
rtl8185/authors
rtl8185/tags
rtl8185/r8180_pm.c
rtl8185/r8180_hw.h
rtl8185/r8180_gct.c
rtl8185/r8180_gct.h
rtl8185/r8180_rtl8225.c
rtl8185/readme
rtl8185/r8180_93cx6.h
rtl8185/ieee80211.h
rtl8185/license
rtl8185/r8180_pm.h
rtl8185/changes
rtl8185/r8180_rtl8225z2.c
rtl8185/r8180_wx.c
rtl8185/r8180_rtl8255.c
rtl8185/r8180_93cx6.c
rtl8185/r8180_sa2400.c
rtl8185/r8180_core.c
rtl8185/r8180_rtl8255.h
rtl8185/ieee80211_crypt.h
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/nick/RTL8185/Linux/ieee80211/tmp
make -C /lib/modules/2.6.24-16-generic/build M=/home/nick/RTL8185/Linux/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/nick/RTL8185/Linux/ieee80211/ieee80211_softmac.o
/home/nick/RTL8185/Linux/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_init&#8217;:
/home/nick/RTL8185/Linux/ieee80211/ieee80211_softmac.c:2236: warning: assignment from incompatible pointer type
/home/nick/RTL8185/Linux/ieee80211/ieee80211_softmac.c:2237: warning: assignment from incompatible pointer type
/home/nick/RTL8185/Linux/ieee80211/ieee80211_softmac.c:2238: warning: assignment from incompatible pointer type
/home/nick/RTL8185/Linux/ieee80211/ieee80211_softmac.c:2239: warning: assignment from incompatible pointer type
/home/nick/RTL8185/Linux/ieee80211/ieee80211_softmac.c:2240: warning: assignment from incompatible pointer type
/home/nick/RTL8185/Linux/ieee80211/ieee80211_softmac.c:2241: warning: assignment from incompatible pointer type
  CC [M]  /home/nick/RTL8185/Linux/ieee80211/ieee80211_rx.o

---

### Post by hyper_ch on 2008-04-18
I'm pretty sure you got tons of error messages when doing step 1 - building the driver from source

first, install build-essential

```

sudo apt-get install build-essential

```

Then try to build the driver with this:
```

./makedrv > ~/Desktop/output.txt

```

and post the output.txt then.

---

### Post by cinnamonbuntu on 2008-04-18
The magic box says I already have the most recent version of build-essential so nothing was installed.

Heres the output as requested:

---

### Post by cinnamonbuntu on 2008-04-18
so I finally got ndiswrapper to work and got my wireless card up and running. 

I'd like to thank everyone who posted here for the speedy and sound advice. Not one thing someone said was at all superfluous. I'm shocked coming from a windows community to here. The dedication, and level of intelligence I've seen here in just 6 short days is exemplary.

BTW a HUUUUUUUUUUGE thank you goes out to the poster that said "Linux is case-sensitive" that was the issue. I have a really big problem of randomly capitalizing words while typing. Not a pen/pencil issue for some reason just happens at the keys. 

Thank you all again.

---

### Post by hyper_ch on 2008-04-18
You <tab>-completion... when entering filenames / dirs on the cli you can use the tab-key to auto-complete the name

---

