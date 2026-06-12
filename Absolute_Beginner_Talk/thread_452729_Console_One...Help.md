---
title: "Console One...Help"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by SteveN84 on 2007-05-23
Hello,

I installed  console one and received no errors during or after installation.  I went to issue the command to run console one and received this:   

ConsoleOne was not found in /usr/ConsoleOne/bin/../jre/jre/bin/java


I checked the folders and everything seems to be in place.

Any Ideas?????  Java related?????

---

### Post by SteveN84 on 2007-05-24
help

---

### Post by John Clayton on 2007-08-08
Hi,

Just had the jre/jre error - go into a command prompt, switch to root (sudo su then your password) then cd to 
```
cd /usr/ConsoleOne/jre/jre
```
Check that the directory contains the Java Runtime Environment ("ls")
then:
```
mv * /usr/ConsoleOne/jre
```
Finally
```
export C1_JRE=HOME=/usr
```
You should be able to run ConsoleOne now.  I can right up until it displays the splash screen, then it core dumps.

Good luck!

---

### Post by kjurkic on 2007-08-16
Keeping the thread alive....

I have ConsoleOne installed and it launchs, then craps itself with:

Aborted (core dumped)

So I am not sure where to go from here. 

I will rant that I am sick of the foot-dragging by novell; they should make up their squirrel-on-crack-on-middle-of-highway minds about which management tool - ConsoleOne, NetWareAdmin, or iManager....GRRRR! At the least they could make the ConsoleOne tool TRULY cross-platform rather than this Fv(! around.:mad:

anyway, I don't think this Aborted issue is directly a ConsoleOne fault, but I cant get this happenin. I have been able to get C1 running on DreamLinux and several other distros; even on VectorLinux about 4 years back, but no joy here so far.

Thanks
Ken

---

### Post by marcantonio on 2007-10-01
Not sure if this thread is still relavent but I just installed with instructions from here:

[http://shadowphax.blogspot.com/2007/07/novell-console-one-on-ubuntu-704.html]("http://shadowphax.blogspot.com/2007/07/novell-console-one-on-ubuntu-704.html")

and it seems to have worked well.

HTH,
Marc

---

### Post by kjurkic on 2007-10-01
marcantonio:

Thanks for the link, but that is exactly what I have done, and still no joy on the C1.:(

Ubuntu is one of the best all-round distro's I have played with, but my search for one that integrates well with netware, and ISN"T a bloated pig that would make microserf proud (suse), continues.

Thanks
Ken

---

### Post by BDNiner on 2007-10-04
I am having kinda the same issue. Console One opens but i don't get the core dumped error message. It is just a blank console one window.

---

### Post by kjurkic on 2007-10-04
BDNiner,

It sounds like your case might be java related. That was happening to me until I got the right JRE (Java runtime executable? engine?)

I don't have any other ideas right now; the search continues. My current workaround is having a VMware virtual WinXP installation, and using MS Crapware for those times I need to access netware shares.

Ken

---

### Post by BDNiner on 2007-10-04
kjurkic,

thanks for you prompt respone. how do i check what version of java i have installed? I installed innotek virtual box instead of vmware. but that crashes often. and i have a windows xp machine at work that i use. i would like my laptop to be able to run console one and the novell client so that when i am on the road i can still administer our systems. i think there is a old open source project for the novell client that i am going to try and install today and see if i can get access to our network shares.

---

### Post by kjurkic on 2007-10-04
Yes, I played with that old "netwhere" client, but haven't gotten it working since about '02 or '03, when I had it working on a Slackware install.

For administration of netware (here) I need C1. I can even skip the client, as the latest C1 allows me to move files around (tho not from linux dekstop<-->netware server)

If you need to have these tools all working, I would suggest SLED (Suse linux enterprise desktop). I was able to get the client and C1 working with minimal fuss, but the hardware requirements are a bad as VISTA. I spent DAYS researching all the crap/bloat I could remove, and finally got it working halfway decent on a p4-2Ghz-1GbRAM. The problem is that my laptop is a PIII 600w 320MbRAM.....Then all the annoyances with traditional linux tools began. Many network tools I like (ie etherape & cheops) were a pain to get working, plus to protect their butts, Novell removed a LOT of media player capability. There is a script available that puts all the controversial media codecs back in, tho.

Hope this is helpful

Ken

---

### Post by marcantonio on 2007-10-04
I had this problem the first time I ran it.  Then I actually cd'd into the directory and ran ./ConsoleOne and it worked.  Now it works both ways so I that might not help much.

Marc

---

### Post by BDNiner on 2007-10-04
I used SLED 10 and had everthing working fine there. my company didn't want to purchase a license and since i am still a noob i did not want to even attempt to manually install updates and patches. I had an ubuntu desktop before i swtiched to the laptop and had everything working fine there also but it was a dual boot with xp and i really messed that one up. So once we got an old dell laptop back from the field i snatched it and attempted to get ubuntu working on it. i also tried opensuse but i am not a fan. so right now i am using iManager to do all my administration. and any complex java based programs are dog slow over a network.

---

### Post by kjurkic on 2007-10-04
FWIW, I had ConsoleOne working good on my old laptop using DreamLinux (also Debian based) and I had NONE of these issues. My only problem there was the Snap-ins for Groupwise; never did get those enabled. I also had the Groupwise client working. 

I may end up back on DreamLinux - it works beautifully on old equipment, and used a nice ndiswrapper widget months before I saw similar from any other distro. The only problem I had that was never resolved was the refusal of the DL installer to see more than 10GB of my 100GB drive.

My notebook currently runs PuppyLinux - brutally fast, but the layout of that distro is so different that getting the Novell stuff working is too much of a time & braincell commitment

Ken

---

### Post by BDNiner on 2007-10-04
i am looking at Dream Linux right now. I don't like the fact that it feels like a mac but this can be changed. I am more anti mac than anti windows. I just think they make poor products. We don't use groupwise at all here, so i can't comment on that. We use basecamp for our project sharing and stuff like that. i have never heard of puppy linux, so i am investigating that right now also. The Novel Client worked well, on the first install actually once i got the correct libraries. It is not the official Novell Client but all i need to do is authenticate so that i can access the network shares.

---

### Post by kjurkic on 2007-10-04
which novell client was it that you got working? The Novell *rpm, or the old netwhere?


As I noted, puppy is "different". The audience is single user pc's, so there is no username/password at login. It's hardware detection I have found to be second-to-none, especially wireless. They just release a new version that is intended to be Slackware compatible.

Regards,
Ken

---

### Post by BDNiner on 2007-10-04
i used the old open source one, there is a post in these forums about how to set it up and where to find one library file that is needed but not available in the repositories. i have not successfully converted the rpm from the Novell site.

[http://ubuntuforums.org/showthread.php?t=459717](http://ubuntuforums.org/showthread.php?t=459717)

This is the link to the post i followed. and use dialog instead of dialogue

---

### Post by kjurkic on 2007-10-05
I found a fix from here, but using slightly different choice

[https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/68020](https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/68020)


**I followed this**:
---------------------------------------------------------------------------
 tasadar_f  wrote on 2006-10-24:  (permalink)

With sun jre1.5 azureus not work.
With java-gcj work perfectly.

Use this:
sudo update-alternatives --config java
choose java-gcj

I need azureus work with sun java jre1.5 because I use mercury messenger that only work with sun jre1.5
--------------------------------------------------------------------------

**But instead I chose the Sun java 1.5**

-------------------------------------------------------------------------
en@dreamer:/usr/ConsoleOne/bin$ sudo update-alternatives --config java
There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-gcj/jre/bin/java
          3    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          4    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.
ken@dreamer:/usr/ConsoleOne/bin$ ./ConsoleOne &
[1] 3644
ken@dreamer:/usr/ConsoleOne/bin$ Novell JClient 1.3.1172-1.3.1172.  Copyright 1999 Novell Inc. All Rights Reserved.
-------------------------------------------------------------------------

And ConsoleOne launched just fine. I logged in & got busy..........So its a JAVA problem, not a C1 problem

HTH
Ken:)

---

### Post by kjurkic on 2007-10-09
C1 itself is working as it should, but when I try to add groupwise snapins, C1 flakes out....I kinda need those snapins for C1 on linux to be useful to me.

back to the dungeon......

Ken

---

### Post by BDNiner on 2007-10-11
Did not work for me. I only have options 1 and 2 when i run 

sudo update-alternatives --config java

When i type ConsoleOne it says command not found.

---

### Post by kjurkic on 2007-10-11
BDNiner:
I had to install the extra java versions. Can't remember if I used apt-get or synaptic, or just d/l'd from SUN......

Also, each time I run C1, I have to make the JRE_HOME statement, and the full path:
./usr/ConsoleOne/bin/ConsoleOne (remember that it is case sensitive, plus I have to use the leading dot (.)

FWIW, OpenSuSe is free for d/l and should support all the Novell supplied tools. The most complete installation I ever had working was actually Suse9.3 - I had:

C1 (no g/w snapins)

novell client with working login script. shares accessed through Konqueror mounted network folders

groupwise cross-platform client

Remoteconsole (rconj IIRC) so I could get right to command console on netware

This was all fine on a p4 desktop with 512M-RAM, but I could never get satifactory performance on my old PIII laptop (read: windows was preferrable in this case), plus support for wifi and other drivers was abysmal to non-existant.

On a side note, I recall reading somewhere that properly installed, iManager actually has all the ConsoleOne tools, including all snap-ins. We have piles of novell legacy crap here, and for some reason iManager doesn't play right, so I am still tinkering.

On a CLEAN install I did for a small business, we used OES, and iManager works GREAT. Everythng that needs doing can be done in iManager, but they don't run Groupwise.

Regards
Ken

---

### Post by BDNiner on 2007-10-16
I am debating going with the latest release of opensuse. my company didn't want to pay for novell support for enterprise desktop. i don't really like SUSE that much, but it seems like a logical choice.

it is great that rconj works, i like the remote control from the windows version but it is not in the linux verson. I may have our Novell guy push VNC to all our comptuers that way i can use that to remote control the computers. 

Yes we have iManager and iPrint working well, so you just have to go to our internal web page and you have all the functionality of conosle one except the remote control. It is great if i am on the road and need to do some simple user administration. but as far as creating application object to be delivered to workstations then i believe you have to use ConsoleOne. The only issue with iManager is it is slow because of all the java stuff. and you need to have the right version of java installed. i am still using 1.3.1_02.

I am actually going to setup another computer to try opensuse 10.3 on and see how it goes.

---

