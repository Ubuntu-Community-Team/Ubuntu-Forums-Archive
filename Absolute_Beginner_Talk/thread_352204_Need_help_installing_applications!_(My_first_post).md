---
title: "Need help installing applications! (My first post)"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by EarnestLearner on 2007-02-03
Hello community:

I am a newbie. This is my first time ever using anything other than Windows. I have managed to install Ubuntu 6.10 (Edgy Eft). I have become a pro at installing and removing software using the Applications tab --> Add/Remove... But I have no clue where to begin when I want to install applications that I download from the internet.

I understand that there is a text-based terminal which accepts commands a lot like the way command.com did for Windows. I also think I need to know how to run shell scripts.

Your help is appreciated.

---

### Post by alwiap on 2007-02-03
i am a newb too, please tell me too :D

---

### Post by kylevan on 2007-02-03
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

Title says it all: "How to install ANYTHING in Ubuntu"

---

### Post by bodhi.zazen on 2007-02-03
First, you should see if the application is available in the Ubuntu repositories.

Here is how to enable more repositories:

[http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

Then: Open **Synaptic**, update and search ...

If you want to install outside of the repositories:

[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by phossal on 2007-02-03
You might ask about specific applications, too. There are lots of ways to do almost everything, and some are more fitting to an individual's preferences than others. Plus, seeing how you install a *single* app, broken down step by step, will quickly get you up to speed with your apps, help you get a quick overview of some basics, and give you a chance to work with many individuals - all who have different styles of teaching and preferences all their own.

---

### Post by benner on 2007-02-03
this page has a 'table of equivalents' to get you thinking about some software you may want to look for...

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

---

### Post by simmo72 on 2007-02-03
EarnestLearner,
Learn how to use the terminal based apt-get.
It takes care of finding and installing dependancies for any package you're trying to install.
A lot of the "how tos" on the interwebs have command line instructions that you can copy (right click > copy) from the webpage and paste into a terminal (right click > paste) - saves on typing and making mistakes - just read the whole thread before you execute!

---

### Post by simmo72 on 2007-02-03
Another thing you'll find useful is adding repositories to your /etc/apt/sources.list file
by doing a:
sudo gedit filename
or nano or pico as your user friendly editor!
That will let you install anything that you need that the ubuntu higher ups decree as working.

---

### Post by simmo72 on 2007-02-03
Now, can you help me?

I have an issue and would like to post a question but I am blind as to how to do this!

What am I not seeing?

Cheers.

---

### Post by phossal on 2007-02-03
Go into the forum related to your question, and then click "Make New Post", just like you click "Post Reply" or whatever in this thread.

---

### Post by EarnestLearner on 2007-02-03
Thank you so much! I have a lot of reading to do. I think I have a basic understanding of what Synaptic Package Manager does and what repositories are. The guide to install anything on Ubuntu was very helpful!

I know I'll be back with tons of questions. Thanks for all the prompt responses!! I'm enjoying the community already.

---

### Post by simmo72 on 2007-02-03
Cheers Phossal!

S.

---

### Post by EarnestLearner on 2007-02-03
Okay. So here's the situation thus far:

I am trying to install a precompiled archive with the extension .tar.gz. Any ideas?

---

### Post by phossal on 2007-02-03
Depending on what it is, right-click and extract? Must you be so vague? :)

---

### Post by EarnestLearner on 2007-02-03
It's a VPN client. Okay, I have extracted the archive. The directory vpnclient has been created in my home directory. It contains the following files:

cisco_cert_mgr   IPSecDrvOSFunctions.h  linuxcniapi.c     vpnapi.h
Cniapi.h         IPSecDrvOS_linux.c     linuxcniapi.h     vpnclient
config.h         IPSecDrvOS_linux.h     linuxkernelapi.c  vpnclient.ini
cvpnd            ipseclog               linux_os.h        vpnclient_init
driver_build.sh  libdriver64.so         Makefile          vpn_install
frag.c           libdriver.so           mtu.h             vpn_ioctl_linux.h
frag.h           libvpnapi.so           sample.pcf        vpn_uninstall
GenDefs.h        license.rtf            unixcniapi.h
interceptor.c    license.txt            unixkernelapi.h

---

### Post by phossal on 2007-02-03
There should be instructions for installing that in one of two places: 
1) Among the extracted files in a text file called "read me"
2) On the web where you got it.

It has scripts and makefiles, etc. That isn't the *easiest* thing you could choose to install out of the gate. You almost certainly want to do this:
```
sudo apt-get install build-essential
```
That will install the compiler set, which you'll need.

---

### Post by EarnestLearner on 2007-02-03
I appreciate your efforts. Unfortunately:

[LIST=1]
[*]There is no file in the archive called read me
[*]The Linux version of the VPN client is not supported by my school.
[/LIST]

---

### Post by phossal on 2007-02-03
Where do you download a .tar.gz file full of headers and make files from? Wherever the *code* source of that program is, a *human* source is likely close by. That human probably wrote some instructions for installing his program.

---

### Post by EarnestLearner on 2007-02-03
I have already installed build-essentials using Synaptic Package Manager as per the instructions on the "How to install anything in Ubuntu" page. I have downloaded the software from my school's web site. Their IT services only support Windows.

Are applications in Linux *THAT* complex to install? In Windows, if there is no readme.txt, I used to simply click on the executable. There is a file called "vpn_install". Any ideas?

---

### Post by phossal on 2007-02-03
> **EarnestLearner said:**
> There is a file called "vpn_install". Any ideas?
Um. Click it? Or issue: sudo chmod +x vpn_install  (and then launch it from the command line?)

I'm not sure anything is difficult in Ubuntu, depending on your skill set. A tar.gz file isn't something you would typically download in Windows. It seems like anyone supporting it would supply a simple instruction set. For example, you might run:
```
sudo make
```

Without knowing the program, I can't tell you how to install it with any certainty. There isn't *the* way to install and launch programs. There are 10 popular languages, 5 popular methods for launching them, etc.

---

### Post by riven0 on 2007-02-03
Why don't you just install it through Synaptic? Compiling from source is the hardest way to install programs. Just search for **vpnc** to install the Cisco-compatible client. Otherwise, search for vnc to get a list of all other apps and choose from there.

---

### Post by EarnestLearner on 2007-02-03
Awesome! I was able to find and install the VPN client using Synaptic Package Manager. Now the only trouble is.. How do I run it?

---

### Post by phossal on 2007-02-03
> **riven0 said:**
> Why don't you just install it through Synaptic? Compiling from source is the hardest way to install programs. Just search for **vpnc** to install the Cisco-compatible client. Otherwise, search for vnc to get a list of all other apps and choose from there.

Experience talks. lol I've never used it, and didn't recognize it. Plus, I couldn't tell if he was being intentionally cryptic or was actually clueless. ;) Now I'm *convinced* that an instruction set exists. lol

---

### Post by EarnestLearner on 2007-02-03
> **phossal said:**
> Um. Click it? Or issue: sudo chmod +x vpn_install  (and then launch it from the command line?)

I'm not sure anything is difficult in Ubuntu, depending on your skill set. A tar.gz file isn't something you would typically download in Windows. It seems like anyone supporting it would supply a simple instruction set. For example, you might run:
```
sudo make
```

Without knowing the program, I can't tell you how to install it with any certainty. There isn't *the* way to install and launch programs. There are 10 popular languages, 5 popular methods for launching them, etc.

Intriguing. Thanks for the information. I had no idea it was that convoluted.

---

### Post by EarnestLearner on 2007-02-03
> **phossal said:**
> Experience talks. lol I've never used it, and didn't recognize it. Plus, I couldn't tell if he was being intentionally cryptic or was actually clueless. ;) Now I'm *convinced* that an instruction set exists. lol

If I come off as cryptic, it's because I actually do have a lot of general knowledge of computing in *Windows* but am clueless in Linux. I was concerned that my last question about the vpn_install file might just appear too stupid to be genuine. I assure you, I am a Linux newbie!

---

