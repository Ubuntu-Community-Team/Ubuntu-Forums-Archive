---
title: "Skype"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by nebu on 2008-02-23
I have enabled the medibuntu repository to get the video codecs from the net.....

when in install skype thru the synaptic..... it installs skype 2 beta.....

are there any known issues of this version with ubuntu7.10 ....

none of my contacts come on the list once i login..... i cant search for new contacts and i cant even make calls to normal phones using my skype credit!!!

---

### Post by JohnLM_the_Ghost on 2008-02-23
Haven't tried skype 2 beta yet.

However I'm using skype 1.4 and it works flawlessy.
You might want to try reverting to 1.4 (or other non-beta version). Download package from skype.com if it isn't available from repos (I use downloaded version)

---

### Post by duckgoesoink on 2008-02-23
> **nebu said:**
> I have enabled the medibuntu repository to get the video codecs from the net.....

when in install skype thru the synaptic..... it installs skype 2 beta.....

are there any known issues of this version with ubuntu7.10 ....

none of my contacts come on the list once i login..... i cant search for new contacts and i cant even make calls to normal phones using my skype credit!!!

I know it doesn't quite answer your question, but I'm running Feisty 7.04 and Skype 2 beta hasn't had any problems for me - I can make video calls all the way to New Zealand, and my credit shows up fine. Note: beta version has video support, stable version doesn't.

(Only problem I had was hardware related, namely the microphone - and it was fixed within a couple of days.)

---

### Post by Ripfox on 2008-02-23
Are you making video calls using Skype in Ubuntu or Windows? I haven't tried video conferencing in Ubuntu yet with any app. Just curious.

---

### Post by duckgoesoink on 2008-02-23
> **ripfox said:**
> Are you making video calls using Skype in Ubuntu or Windows? I haven't tried video conferencing in Ubuntu yet with any app. Just curious.

Ubuntu - Vista is being stupid and doesn't recognise my webcam since I had harddrive fixed, so I hardly use Windows anymore. But yeah, Skype video calls work great in Feisty anyway.

---

### Post by Ripfox on 2008-02-23
Hmmm...I will have to try that now. Thanks.

---

### Post by Chappy7777 on 2008-02-28
> **JohnLM_the_Ghost said:**
> Haven't tried skype 2 beta yet.

However I'm using skype 1.4 and it works flawlessy.
You might want to try reverting to 1.4 (or other non-beta version). Download package from skype.com if it isn't available from repos (I use downloaded version)
===========================
I just put up a post asking questions about the version at Skype.com  (version 1.4).  This is what I posted elsewhere. Sorry about asking the same thing twice, but I just read your post and it seemed like you might have the answer to the question below. Thanks.
========

I just went to skype's download page for 7.04 linux (which is what I am running). It all looked great until I saw

Software needed:

Qt 4.2.1+
D Bus 1.0.0
libasound2 1.0.12
libsigc++2.02

I looked for this software in synaptic and none of it came up as existing, never mind loaded.
Can someone tell me where and how to find this stuff? I am not new to Ubuntu, but I am pretty much an "unterminal" user. In other words, I install and remove using Synaptic as much as possible. The only thing I have installed that I am sure I needed to use a Terminal for is Real Player. That was easy enough after some kind soul on here told me what to type into terminal.

Skype makes downloading, installing, and using itself sound like a no-brainer. If that's true, I can likely do it.

Some feedback please.

---

### Post by muadnu on 2008-02-28
I'm running skype 2 beta with gutsy (amd64), no problems so far, even my webcam is working flawlessly.

---

### Post by Oldsoldier2003 on 2008-02-28
> **Chappy7777 said:**
> ===========================
I just put up a post asking questions about the version at Skype.com  (version 1.4).  This is what I posted elsewhere. Sorry about asking the same thing twice, but I just read your post and it seemed like you might have the answer to the question below. Thanks.
========

I just went to skype's download page for 7.04 linux (which is what I am running). It all looked great until I saw

Software needed:

Qt 4.2.1+
D Bus 1.0.0
libasound2 1.0.12
libsigc++2.02

I looked for this software in synaptic and none of it came up as existing, never mind loaded.
Can someone tell me where and how to find this stuff? I am not new to Ubuntu, but I am pretty much an "unterminal" user. In other words, I install and remove using Synaptic as much as possible. The only thing I have installed that I am sure I needed to use a Terminal for is Real Player. That was easy enough after some kind soul on here told me what to type into terminal.

Skype makes downloading, installing, and using itself sound like a no-brainer. If that's true, I can likely do it.

Some feedback please.
apt-get update
apt-get install skype

the beta version works flawlessly on my system btw...

---

### Post by duckgoesoink on 2008-02-28
I didn't even look at the software requirements when I installed Skype 2.0 beta for Linux, but it installed just fine - works great. I'm running 7.04 Feisty too.

---

### Post by anorexicpillow on 2008-02-28
when I enter apt-get install skype it says "E: Couldn't find package skype" even though I downloaded it from the skype website onto my desktop. when  I use the package installer it says "Error: dependency is not satisfiable: libasound2"

---

### Post by Oldsoldier2003 on 2008-02-28
> **anorexicpillow said:**
> when I enter apt-get install skype it says "E: Couldn't find package skype" even though I downloaded it from the skype website onto my desktop. when  I use the package installer it says "Error: dependency is not satisfiable: libasound2"


apt-get is for remote packages. if you have the package on your desktop open it with the appropriate installer

usually you can right click...

---

### Post by duckgoesoink on 2008-02-28
Did you download the package for Ubuntu 7.04+? The extension is .deb - it works like an .exe file in windows. Just open it, and follow the instructions.

---

### Post by anorexicpillow on 2008-02-28
when i double click it runs the package installer but says "Error: dependency is not satisfiable: libasound2"

---

### Post by Oldsoldier2003 on 2008-02-28
> **anorexicpillow said:**
> when i double click it runs the package installer but says "Error: dependency is not satisfiable: libasound2"
try apt-get install  libasound2 then try reinstalling Skype

---

### Post by anorexicpillow on 2008-02-28
Reading package lists... Done
Building dependency tree... Done
libasound2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


:S

---

### Post by Oldsoldier2003 on 2008-03-01
[QUOTE=anorexicpillow;4423359]Reading package lists... Done
Building dependency tree... Done
libasound2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


:S[/QUOTE
]hmm try this from a terminal window. I'm no guru but maybe updating and then running fix will resolve your package listing issue.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f 
sudo apt-get install skype
```

---

### Post by JohnLM_the_Ghost on 2008-03-02
> **Chappy7777 said:**
> ===========================
I just put up a post asking questions about the version at Skype.com  (version 1.4).  This is what I posted elsewhere. Sorry about asking the same thing twice, but I just read your post and it seemed like you might have the answer to the question below. Thanks.
========

I just went to skype's download page for 7.04 linux (which is what I am running). It all looked great until I saw

Software needed:

Qt 4.2.1+
D Bus 1.0.0
libasound2 1.0.12
libsigc++2.02

I looked for this software in synaptic and none of it came up as existing, never mind loaded.
Can someone tell me where and how to find this stuff? I am not new to Ubuntu, but I am pretty much an "unterminal" user. In other words, I install and remove using Synaptic as much as possible. The only thing I have installed that I am sure I needed to use a Terminal for is Real Player. That was easy enough after some kind soul on here told me what to type into terminal.

Skype makes downloading, installing, and using itself sound like a no-brainer. If that's true, I can likely do it.

Some feedback please.
You might also try to download one for debian or for one "other linuxes"... anyways i'm running 7.10 Gutsy. So I probably have different software packages availble...

---

### Post by Claus7 on 2008-04-19
Hello,

for dapper drake users this is what I did:
[http://ubuntuforums.org/showthread.php?p=4749162#post4749162](http://ubuntuforums.org/showthread.php?p=4749162#post4749162)

Regards!

---

