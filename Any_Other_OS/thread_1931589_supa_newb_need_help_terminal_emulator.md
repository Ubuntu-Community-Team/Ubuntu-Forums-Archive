---
title: "supa newb need help terminal emulator"
date: 2012-02-25
forum: Any Other OS
---

### Post by shang xia jiu on 2012-02-25
I just insatll BT5
 
seems ok,:D but when i look for terminal emulator i don't see one.
 
i tried my stick that has portable hyperteminal, tera term, and putty these seem to work but are slow and quircky.
I tried to install secureCRT, and ZOCpro 6.29 both worked but are also wierd.
 
I went to vandyke and got a 30 day evaluation copy of crt for ubuntu 11x64.
 
now when i goto install looks like i have no tool to open the .deb file.
 
I get an 
ERROR
 
"THERE IS NO application installed for Debian package files"
 
can you guys suggest
 
thank you:D

---

### Post by HeroOfCanton on 2012-02-25
BT5 is in no way, shape, or form, for newbs. :D Are you sure you want to dive into linux head first like that? May want to consider another distro to get your feet wet first...

The terminal emulator is called Quypt. I would suggest learning a little more of the basics first though. And stay out of trouble. ;)

---

### Post by shang xia jiu on 2012-02-25
do you refer to terminal emulator is beyond basic?
 
DB5 looks just the same as ubuntu , 
different desktop, and some great tools already installed and your already logged in as root.
 
 
thanks for the info i will check out Quypt, but secure CRT is what i need to use
 
not sure what kind of trouble i am suposed to stay out of? you think when i am logged as root I might send out a broadcast storm and confuse the ccies, or create a layer 2 Dos attack, and they will think that thier is a spanning tree loop? or I do a layer 2 attack by sending 1000's of packets from one rig spoofing MAC's to flood the CAM table to crash the memory. I still have trouble getting a router out of rommon> (sometimes), when tftp dun't work and i have to use Xmodem, jist depends how bad i bricked the router heh, & when i setup a gre 4to 6 tunnel, i have trouble, ya think microsoft will take away my mcitp? or cisco is gonna take away my ccnp.:grin: don't make it out to be a crime to learn something new mkay,* I already *bookmarked this joint an put it on my favo bar, i plan to learn some stuff here.

---

### Post by HeroOfCanton on 2012-02-25
I just meant that BT is a little tougher disto because it doesn't boot to the GUI, networking is off by default, etc. No offense intended. If you can handle it right off the bat more power to ya! Most people who would refer to themselves as a supa newb wouldn't want to take that steep learning curve, but it sounds like you are willing to do the work. That's all that matters.

A .deb *should* be able to be handled by the default package manager. From the terminal:

```

cd /*path*/
dpkg -i *package*.deb

```If you still have problems installing check out this thread from the SecureCRT forums [http://forums.vandyke.com/showthread.php?t=2077&page=2](http://forums.vandyke.com/showthread.php?t=2077&page=2)

Post #25 has a tip about loading the older Share Python runtime library in order to install. That was for ubuntu 11.04, but maybe it applies to BT5 as well? The support email for them is also listed in that thread and they seem very helpful towards the linux folks.

And stay out of any and all trouble. Don't make it out to be a crime to give general advice, mkay. ;) You could tell me you're not only certified, but Bill Gates himself. I have no way to confirm nor deny it. That's powerful software. 'nuff said.

---

### Post by enjoijesus94 on 2012-02-25
If You Know Nothing About Linux Good Luck Figuring Out BT5.

Get To Know How Linux Works.
And Everything 

Once You Have Everything Down Go Back And See How Everything Goes.

I Recomend Learning Bash Or At Least A Couple Of Commands.

For Example.
Moving Files.
Removing Files.
Updating ,Upgrading,Messing With Many Diffrent Things With The Kernel.

Oh And By The Way If Your In It For Pentesting Security Make Sure You Know What Your Doing.

Hope This Helps :popcorn:

---

### Post by shang xia jiu on 2012-02-25
nice mkay then
 
Code:
cd /*path*/dpkg -i *package*.deb
 
If you still have problems installing check out this thread from the SecureCRT forums [http://forums.vandyke.com/showthread.php?t=2077&page=2](http://forums.vandyke.com/showthread.php?t=2077&page=2)
 
:Pthanks
 
been watching some linux cbt nuggets for red hat,  .pdf bt5 reading-> just loaded bt5 today, did study CCNA security, have SDM running AAA and MD5 keys going but need a better router trying to get a 2651xm but i don't have much cash. I need to get up to speed fast for a job.

---

### Post by enjoijesus94 on 2012-02-25
> **shang xia jiu said:**
> nice mkay then
:Pthanks

No Prob Man 
Not Trying To Sound Offensive.

Its Just You Dont Wanna Get Into Trouble Or Mess Something Up.

Heres Somewhere To Start 


[http://ss64.com/bash/](http://ss64.com/bash/)

Cheers:)

---

### Post by oldos2er on 2012-02-26
Thread moved to Other OS/Distro Talk.

---

