---
title: "Need to find libmp3lame.so !!"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-09-10
Couldn't find it in Synaptic, even tried sudo aptitude install libmp3lame.so
in the terminal and it can't find it. I'm pretty sure my repos are up to date. How to get this elusive beast,lol. Thanks ! :)

---

### Post by orb9220 on 2006-09-10
It is in synaptic as liblame0 and has these files installed

/.
/usr
/usr/share
/usr/share/bug
/usr/share/bug/liblame0
/usr/share/bug/liblame0/control
/usr/share/doc
/usr/share/doc/liblame0
/usr/share/doc/liblame0/copyright
/usr/share/doc/liblame0/changelog.Debian.gz
/usr/lib
/usr/lib/libmp3lame.so.0.0.0
/usr/lib/libmp3lame.so.0

---

### Post by orb9220 on 2006-09-10
Just found out it is audacity is expecting libmp3lame.so but the actual is libmp3lame.so.0 so if you add the .zero on the end and click ok then you  will be able to set the higher bit rates.

But it dosn't WORK! Still trying to fiqure what the (*(&(&(*)__(^ is going  on.

Mayebe audacity needs upgrading cannot find just the libmp3lame.so but libmp3lame.so.0 and libmp3lame.so.0.0.0 is there any idea's.

---

### Post by Drakkor on 2006-09-10
Yeah,thanks,Orb,you're right,but I found the answer in another post that I can't find now,but basically all you have to do in Audacity is go to......
Edit>Preferences>File Formats>MP3 Export Setup>Find Library, and then it'll 
ask you whether you want to find the libmp3lame.so file now,select yes,then
at the bottom where it says"Only libmp3lame.so", click there and select
"All files" and find libmp3lame.so.0.0.0 and hit OK and you should be good to go ! As shown here.  Good Luck !  :)

---

### Post by RichPicker on 2007-02-18
That worked for me. Thank you. 

Rich

---

### Post by teknosexual on 2007-03-07
I know this is an old thread, but I just had this problem a few minutes ago, and I finally found a solution. So maybe this will help somebody...

1. First, I downloaded the latest release of [**LAME**]("http://sourceforge.net/project/showfiles.php?group_id=290&package_id=309") in tar.gz archive (currently 3.97 is current version).

2. Next, I extracted these files to my **Desktop**.

(Then I spent 20 minutes trying to find a basic tutorial of how to use the terminal--not just where it is, but [examples of commands]("http://monkeyblog.org/ubuntu/installing/#installing_with_terminal")!)

3. Open the **Terminal** (Applications > Accessories > Terminal).

4. Assuming you extracted the files to your Desktop (**remember it's CASE sensitive!**), type the following in this order (and after each command, press Enter):
[LIST]
[*]**cd Desktop**
[*]**cd lame-3.97**
[*]**./configure**
[*]**make**
[*]**sudo make install**
[/LIST]
After the last command ("sudo make install"), you'll be prompted to enter your system password, do so and press enter. The LAME files will now be installed. Once you see "username@ComputerName: ~/Desktop/lame-3.97$" as the last line in the Terminal, go to the next step.

5. Open Audacity, and click on Edit > Preferences > File Formats. Then click the Find Library button. Now, Audacity starts you out in the wrong folder, so navigate up until you hit the **usr **folder. Then go into **local**, then **lib**. You should see the file **libmp3lame.so** right there, so select it and hit OK. Audacity will automatically update whatever it needs to.

And now you can export as MP3.

From one beginner to another, good luck!

---

### Post by Platinum89 on 2007-03-17
Followed the instructions, but after I type in ./configure I get the following...

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

---

### Post by johnthei on 2007-03-18
ok I am an idiot and new to ubuntu.  
I tried what tkenosexual says, but when I get to the ./configure, I get an error message saying   ''error. C computer connot creat executables. See 'Config.log'  ''

ok.  Where is this log, and what am i doing wrong.

also.... tried to go past this error message just to see what would happen, when I got to my password logon, it would not let me TYPE a letter. I had just a black box the size of a letter but could not get it to accept my password. I am the admin o this.

---

### Post by Drakkor on 2007-03-18
The password will not be visible, but will still work!

---

### Post by johnthei on 2007-03-18
ok..but what about the C computer error message?

---

### Post by scxtt on 2007-03-18
try doing **sudo aptitude install build-essential** 1st, then doing it again ...

but i'm not sure why you can't just install lame from the repos, worked fine for me ...

---

### Post by ratbagradio on 2007-04-18
This post was a godsend. Locating and engineering Lame on Ubuntu(Edgey) without going up the wall was indeed a challenge for my capacity to keep calm. Someone who ""knows" --and "knows" the business well-- should write it up covering all the nuances of the  whole terrible journey as a easy to follow DIY. The confusion is so unnecessary. And installing LAME on Windows is so easy! -- on Linux/Ubuntu it is SOOOOOO hard!

I was fed up and took on Jokosher (another audio editor for Linux)but they then offer a brutally convoluted relationship installing and tweaking  gstreamer. which seems more demanding of p[ig ignorant grey matter than Lame's Linux relationship with Audacity.

So there's this big hole in Ubuntu media accessibility that won't be filled until these issues are addressed.Fortunately later releases of Audacity "may" include Lame already installed.

> **teknosexual said:**
> 
.................
4. Assuming you extracted the files to your Desktop (**remember it's CASE sensitive!**), type the following in this order (and after each command, press Enter):
[LIST]
[*]**cd Desktop**
[*]**cd lame-3.97**
[*]**./configure**
[*]**make**
[*]**sudo make install**
[/LIST]
....................
From one beginner to another, good luck!

PS: I upgraded to Edgey yesterday from Dapper: yum. Love it!

---

### Post by Drakkor on 2007-04-18
And now you can install Fiesty tomorrow,lol  :D

---

### Post by epicaricacy on 2007-05-02
thank you! libmp3lame.so is now a happy part of my computer.

---

### Post by NJC on 2007-05-26
> **Drakkor said:**
> 
Edit>Preferences>File Formats>MP3 Export Setup>Find Library, and then it'll 
ask you whether you want to find the libmp3lame.so file now,select yes,then
at the bottom where it says"Only libmp3lame.so", click there and select
"All files" and find libmp3lame.so.0.0.0 

Thanks - this worked great after I installed the Lame package. Nice to finally get this fixed!

---

### Post by Drakkor on 2007-08-24
Yeah, it's time to do this again, had to re-install the system, I have downloaded lame from the repos, but I can't seem to find it, isn't it supposed to be in usr/lib ?? Thanks ! :)

---

