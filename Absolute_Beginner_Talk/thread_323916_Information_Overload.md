---
title: "Information Overload"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by tcyk on 2006-12-23
There is a marvelous assortment of instructions for using Linux, so much that I can't sort through them to answer my questions.

Originally, I downloaded jre-1_5_0_07-linux-i586-bin. It has been over half a year and I still haven't managed to install it. I found very detailed instructions that told me where to store it etc., but somehow it didn't work for me. 

I read that I had to enable extra repositories. I followed the instructions I found at [http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources) but I don't believe it worked.

I have been learning Ruby in windows but I want to use it in Linux. I think its in my machine.Synaptic package manager says it is and that irb is installed but I can't find them.

I did manage to get gforth installed but haven't worked out how to transfer my windows forth files to Linux. My floppy drive is a usb device and I haven't discovered how to get Ubuntu to recognize it.

I need a driver for my Epson R320 printer  but don't know what I should try since Epson evidently fails to make Linux/Unix drivers. At least I never found one.

I don't want to give up on Ubuntu. I like some of the features a lot, but ...
I get so frustrated with trying to solve these problems for myself (the best way to learn). I find volumes of literature but what I find either doesn't work or I don't know how to use the information correctly.

Tonight was the final straw. Someone wrote a procedure that began with su. Fine, I entered it, was asked for my password, and was told 'sorry'. yet when I try to use the synaptic package manager, it thinks my password is great. If 'su' isn't asking for my root password, I have no idea what it wants.

When I try to use sudo, I get a list of parameters and don't know how to proceed from there. I'm not a dummy. I ran dos before there was windows. The Linux terminal isn't so different from dos. Regardlessly, I feel like a dummy.

Charles Gray -- [email]tcyk@aol.com[/email]

---

### Post by nalmeth on 2006-12-23
No problem, you came to the right place.

What version of Ubuntu are you running? The current stable, long-term support version is Dapper Drake 6.06. 

Java has been open-sourced, so its now in the main repositories. If you are running a really old version, I can't be certain it has been backported for Breezy(5.10) or Hoary (5.04).

su refers to the root password. Ubuntu doesn't have a root user by default, and uses sudo instead, which you seem to know. Use sudo instead of su.

I don't know what your sudo problems are, if you could post the output of the errors it would be helpful, maybe someone can point out the problem. 

You would probably find a linux driver (community made) on linuxprinting.org

Please let us know what version of Ubuntu you are running, you said half a year, so I would imagine either Breezy or Dapper, if I were to guess.

---

### Post by deadgobby on 2006-12-23
> **tcyk said:**
> There is a marvelous assortment of instructions for using Linux, so much that I can't sort through them to answer my questions.

Originally, I downloaded jre-1_5_0_07-linux-i586-bin. It has been over half a year and I still haven't managed to install it. I found very detailed instructions that told me where to store it etc., but somehow it didn't work for me. 

I read that I had to enable extra repositories. I followed the instructions I found at [http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources) but I don't believe it worked.

I have been learning Ruby in windows but I want to use it in Linux. I think its in my machine.Synaptic package manager says it is and that irb is installed but I can't find them.

I did manage to get gforth installed but haven't worked out how to transfer my windows forth files to Linux. My floppy drive is a usb device and I haven't discovered how to get Ubuntu to recognize it.

I need a driver for my Epson R320 printer  but don't know what I should try since Epson evidently fails to make Linux/Unix drivers. At least I never found one.

I don't want to give up on Ubuntu. I like some of the features a lot, but ...
I get so frustrated with trying to solve these problems for myself (the best way to learn). I find volumes of literature but what I find either doesn't work or I don't know how to use the information correctly.

Tonight was the final straw. Someone wrote a procedure that began with su. Fine, I entered it, was asked for my password, and was told 'sorry'. yet when I try to use the synaptic package manager, it thinks my password is great. If 'su' isn't asking for my root password, I have no idea what it wants.

When I try to use sudo, I get a list of parameters and don't know how to proceed from there. I'm not a dummy. I ran dos before there was windows. The Linux terminal isn't so different from dos. Regardlessly, I feel like a dummy.

Charles Gray -- [email]tcyk@aol.com[/email]
 For one you can install Atumatix and get the Java to install really easy. Automatix.com
 Please post your errors when you use Sudo. Like sudo aptitude install file. Just like DOS. Linux is case sesative. So if your type in Sudo in a capital S. It will error out. 
Gobby

---

### Post by tcyk on 2006-12-23
I am running Dapper Drake on a Dell inspiron 9200 laptop. I bought the dvd for Ubuntu. repetitioned my hard drive and installed the whole package. I run it as a dual-boot system since .my favorite website doesn't support Linux. When I enter just sudo I get:
charles@Grumpy-Charlie:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
I could probably find what all this means but I am tired of searching and reading.

---

### Post by nalmeth on 2006-12-23
If thats the only thing bugging you about sudo, then theres no problem.
Its just detailing the usage of sudo.

Try this command:
sudo apt-get update
sudo apt-get install sun-java5-bin sun-java5-plugin

Please post if there are any problems with this.

What is that website BTW?

---

### Post by meng on 2006-12-23
> **nalmeth said:**
> If thats the only thing bugging you about sudo, then theres no problem.
Its just detailing the usage of sudo.

Try this command:
sudo apt-get update
sudo apt-get install sun-java5-bin sun-java5-plugin

Please post if there are any problems with this.

What is that website BTW?
This is by far the easiest way to install the JRE, but ensure you have universe and multiverse repositories enabled.

---

### Post by tcyk on 2006-12-23
When I enter sudo apt-get update, I get a list of packages that ends with the following:

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
  404 Not Found
Fetched 7B in 12s (1B/s)
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz](http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz](http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz)  404 Not Found
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I don't know the cause of the errors or failures. I went ahead and tried the installation with the following results:

charles@Grumpy-Charlie:~$ sudo apt-get install sun-java5-bin-plugin
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I will reboot the system and try again.

The website is Bridge Base Online where I play duplicate bridge in my spare time. User name is tcyk.

---

### Post by nalmeth on 2006-12-23
the fix to that problem is:
sudo rm -r /var/lib/dpkg/lock

I can see how these must frustrate you, but we're going to help you get everything you need.

Remember to enter the lines as I gave them to you. 
sun-java5-bin and sun-java5-plugin are different packages, so they both need to be entered in full

---

### Post by nalmeth on 2006-12-23
Also, the errors coming from apt-get update are due to problems with the mirrors of some of the repositories in your sources.list

You may also post the output of this command for us as well, so we can take a look at it:
cat /etc/apt/sources.list

I see that the website requires you to download a program to play. I cannot promise you that we can get that to work, but theres a non-zero chance we can. Lets stay positive

---

### Post by Ptero-4 on 2006-12-23
> charles@Grumpy-Charlie:~$ sudo apt-get install sun-java5-bin-plugin
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

This problem happens because you can't run two package managers simultaneously.

---

### Post by tcyk on 2006-12-23
I made some progress with jre. I did the sun-java5-bin bit and it was downloaded, or apparently so. I got the license agreement and selected yrs, etc.I tried to use it on pogo(my wife's favorite passtime and was told additional plugin was need and nonavailable. I my searches, I got back to sun and ran a program of theirs which was supposed to tell me if jre was properally installed. Apparently not although I later suspected that the application was for windows users.

I went back to terminal and reloaded the install instructions. I was told that I already had the latest version. I ran the application check again with the same negative results. Sun even had a link to pogo. I followed the link and again got the plugin needed message. It is now 1AM in Phoenix and I'm going to bed and will continue my efforts tomorrow. Thanks all for your effort to help me.

---

### Post by tcyk on 2006-12-23
My wife's oldest son showed up from Dallas. He is a Linux developer for some company. I Told him of my problems with jre and he said it was easy t fix. I tried to watch over his shoulder to learn what he was doing but there was no way I could keep up with him. He did tell me how to become root using sudo. In about 10 minutes he said it was installed. 

I tried to scroll back up in terminal to see what he did but was unable to understand. It appears he did something in /usr/alternatives/ that corrected my problem.

My next goal is to learn to configure this thing for email. He says that's easy too and he runs AOL like I do. I never could find AOLs server IP. If I can shake Paul loose from his mother for a few minutes, perhaps he will do it or me.

Again, thanks for all the help so far.

Charlie

---

### Post by OldTimeTech on 2006-12-23
I'm rather a newbie myself.....but maybe have a couple of hints to help.

First for the java, try installing Automatix2, [http://www.getautomatix.com](http://www.getautomatix.com).

For the print drivers, check on: [http://www.freestandards.org/en/OpenPrinting/Database/DatabaseIntro](http://www.freestandards.org/en/OpenPrinting/Database/DatabaseIntro)
This is a database with manufacturers and printer models that tell you if there is a driver and give it to you to download.

I have an "OLD" Epson and it had the drivers.

Last thought....when you use "su" you are in a terminal aren't you?

Hope at least some of this helped.

---

### Post by OldTimeTech on 2006-12-23
Sorry, somehow when I saw your post, I didn't see the rest.....maybe my old eyes, who knows.

Anyway, everyone said the same thing I did.....

Again sorry for not giving new info.

---

### Post by nalmeth on 2006-12-23
tcyk, I have a feeling the sun-java5-plugin is what you needed, sorry I wasn't around after that last post, but I'm glad you seem to have sorted things out.

---

### Post by tcyk on 2006-12-24
I thought I posted how thr jre problem was solved but I must have messed up. My wife's oldest son is a Linux developer. He came here for a few days before Christmas. I told him of my problem and he sat down at my computer and 10 minutes later told me the problem was fixed./usr/alternatives

I tried to wqtch over his shoulder to see what he did but things moved too fast for me to keep up. I believe he envolked root with sudo su - and then made some changes in /usr/alternatives/ but I am unsure of what he did

Anyway, jre is working now. I want to think everyone for their help. I have some additional questions and will make seperate posts for them.

Charlie

---

