---
title: "Wine Audio Error!"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by 9090s on 2007-11-06
At winecfg in the "Audio" tab i am getting this msg:

There is no audio driver currently specified in the registry.

A recommended driver has been selected for you.
You can use this driver or select another if available.



after that i click ok


at the Test sound it says

Audio Test Failed!



at the Control Panel says

launching control panel is not implemented yet.



what to do?
i have to change some setting for playing wow

(i hear sound from the pc e.x. from XMMX but not clearly.)

---

### Post by 9090s on 2007-11-06
Any1?

---

### Post by keithcausey on 2007-11-07
Hello, I am sorry that I can't report anything substantive but I have had no success in this forum for the year that I have been asking questions. Sorry about the negativity but that is the truth. My progress with Ubuntu as been best served by typing my questions in a Google search bar formatted as conversational speech. As for your problem, I have installed wine on three different computers and every one or them is doing the same thing that you describe. If I find a solution then I will report that back to you. Oh - here is a pointless icon I will include for no reason... :guitar:[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by Choad on 2007-11-21
me too man, me too

winecfg doesnt even give me any console output to work with. it just says "audio test failed" on every single one

the really bad thing is that i had sound working in feisty :(

---

### Post by Bram-NL on 2007-12-26
**Great news!** I got it working! :)

What I did is using the latest binaries from [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb). So the steps to take are:

[LIST]
_Add the repository to Ubuntu:_
[*]wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -


[*]**For Ubuntu Gutsy (7.10)**:
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list


[*]**For Ubuntu Feisty (7.04)**:
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list


_And at last, install or upgrade Wine:_
[*]**If you *don't* have Wine installed yet**:
sudo apt-get update && sudo apt-get install wine


[*]**If you have Wine *already* installed**:
sudo apt-get update && sudo apt-get upgrade
[/LIST]

That's it :)

---

### Post by keithcausey on 2008-01-30
Hi - this is what I got when I used the code that you included for gutsy...

sudo wget [http://wine.budgetdedicated.com/apt/...t.d/gutsy.list](http://wine.budgetdedicated.com/apt/...t.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list
--04:27:30--  [http://wine.budgetdedicated.com/apt/...t.d/gutsy.list](http://wine.budgetdedicated.com/apt/...t.d/gutsy.list)
           => `/etc/apt/sources.list.d/winehq.list'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
04:27:34 ERROR 404: Not Found.

---

### Post by keithcausey on 2008-01-30
I have now installed Wine on 6 computers. I am a big Linux fan but I am totally confused about the forums. This makes a full quarter of a year that I have been asking the same question and getting the same results for each implementation of wine on each of the computers that it is running on - audio control panel not implemented yet - any takers? This problem is so ubiquitous for me (I am batting 100 here - none of the computers I have ubuntu on run this command at all) that I can't believe that nobody else has it. Thanks in advance

---

### Post by devnu11 on 2008-01-30
From what I have read wine is constantly in development and new features are being added monthly. I have seen the same notation about not being implimented. I can only guess the wine developers are working on or will be working on that section of the configuration. I am guessing this is not an Ubuntu thing but a wine thing.

---

### Post by rdoyle on 2008-01-31
> **keithcausey said:**
> Hi - this is what I got when I used the code that you included for gutsy...

sudo wget [http://wine.budgetdedicated.com/apt/...t.d/gutsy.list](http://wine.budgetdedicated.com/apt/...t.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list
--04:27:30--  [http://wine.budgetdedicated.com/apt/...t.d/gutsy.list](http://wine.budgetdedicated.com/apt/...t.d/gutsy.list)
           => `/etc/apt/sources.list.d/winehq.list'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
04:27:34 ERROR 404: Not Found.

Don't know why the original link did this, but replace the "...t.d" in these lines with "sources.list.d" (without the quotes).

---

### Post by gamergonelinux on 2008-02-03
It cut it off like that because it read it as a url and automatically made it a hyperlink. If you put your mouse cursor over it you'll get the full url. Just type it in manually.

---

### Post by affert on 2008-02-06
FYI: 
When I click the "test audio" button, it tells me that the test failed.  However, when I load a program, audio seems to work fine.  I haven't done much more testing, so I don't know much more than that.   All that to say: don't just trust the tester...

(ubuntu 7.10, wine 0.9.54)

---

