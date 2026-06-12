---
title: "Moving DIrectory.."
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by dercoss on 2006-11-06
I have a directory that is in "home". Do run it I have bee told I should move it to the /usr/lib directory. The directory contains the Limewire beta for Linux.

Firstly, does this directory need to reside in /usr/lib? If not where should it go, and finally how on earth do move it?

I have tried sudo mv LimeWIre /usr/lib

but nothing gets moved. Could somebody point me in the right direction here please...

dc

---

### Post by Iarwain ben-adar on 2006-11-06
Hi,
try this
```
sudo ln -s ~/limewire_dir/limewire_beta_file /usr/lib/ 
```

This should make a symlink from your ~/limewire folder to /usr/lib

Note: replace the "limewire_dir/limewire_beta_file" with the file folder, and the file itself.


Iarwain

---

### Post by dercoss on 2006-11-06
I'll give it a go and let you know..

dc

---

### Post by dercoss on 2006-11-06
Nope, no luck..

Why is it proving so hard to move a directory from one location to another? It seems a pretty basic task to somebody with experience only of Windows...

dc

---

### Post by Iarwain ben-adar on 2006-11-06
Well,
did you get any error while trying?

What did you try,
did you check if the link exists in the /usr/bin/ ?

and btw: to move a dir[code]sudo mv ~/limewire_dir/ /usr/bin/

DO NOTE: linux is case-sensitive (or whatever it's called :D)
meaning: uppercase is not the same as lowercase
eg. Limewire is not the same as limewire ;)


Iarwain

---

### Post by dercoss on 2006-11-06
I can't get any command that I try to work. For example. I tried making a new director in /usr/bin with this while in that directory..

sudo mkdir test

Nothing seems to happen. There is no directory. If I don't use sudo then I get a permisson denied error which I assume is how it should be.

I'm trying to convince a member of my family of the virtues of linux over Windows but to be honest I don't think the average computer use would have the patience for all this faffing about...

dc

---

### Post by dercoss on 2006-11-06
Now I seem to have fallen foul of some cardinal rule and will apparently be reported...

"holly is not in the sudoers file.  This incident will be reported."

Crikey... My computer has grassed me up to a higher power..

I thought by typing sudo I would become a root user for the duration??

Does anybody know of a good book that will enable me to sit down and work through the basics of Linux (and Ubuntu in particular)? I feel that if I could just get a little more understanding of things I would be up and running....

dc

---

### Post by Iarwain ben-adar on 2006-11-06
Could you post the output of those commands?
sudo mkdir /test (don't make it in the /usr/bin, because it would be crowded to go and search for it there..)
and 
sudo ls /


Iarwain

---

### Post by Iarwain ben-adar on 2006-11-06
> **dercoss said:**
> Now I seem to have fallen foul of some cardinal rule and will apparently be reported...

"holly is not in the sudoers file.  This incident will be reported."

Crikey... My computer has grassed me up to a higher power..

I thought by typing sudo I would become a root user for the duration??

Does anybody know of a good book that will enable me to sit down and work through the basics of Linux (and Ubuntu in particular)? I feel that if I could just get a little more understanding of things I would be up and running....

dc

For the book,
you could use [this](http://www.amazon.com/Official-Ubuntu-Book-Benjamin-Mako/dp/0132435942/sr=1-1/qid=1162814940/ref=pd_bbs_sr_1/103-2114333-4948621?ie=UTF8&s=books) one :D


Iarwain

---

### Post by dercoss on 2006-11-06
Here are the results in reverse order...

sudo mkdir /test   Nothing. It just goes to the prompt
sudo ls /          As above..

dc

---

### Post by Iarwain ben-adar on 2006-11-06
:?

Don't know about that ..

Something stupid is wrong, but i don't know what :?

Sorry dude


EDIT: can you do _anything_ with sudo?


Iarwain

---

### Post by dercoss on 2006-11-06
It appears not...

dc

---

### Post by dercoss on 2006-11-06
I've given up on the machine concerned. It is for my niece and if I have trouble with Linux she is going to be completely lost with it and I'm going to get endless phone calls to help her out. Back to Windows XP for now...

I keep reading about how easy it is to run a linux equipped machine but the truth is that for the casual user the opposite is true. Most people have some exposure to Windows and expect to be able to just click and install things. All this terminal stuff will never fly for the likes of my niece who just wants to use the machine.. I know Linux fans will claim otherwise but Linux is not and I would imagine never going to be a serious rival to Windows or Mac based systems in the general computer user market, at least not for those who have don't have access to technical help on a regular basis..

My neice, who is just coming up to 13 (the laptop is for her birthday)would die rather than be branded a nerdy computer type...

However, I find it all very interesting and have set aside a spare pc to build up my experience. I have also ordered the book you recommend. It seems to be just the thing for me to get up to speed with Linux (and Ubuntu in particular). Personally, I feel that if I could learn enough I would be happy to move over from Windows in the long term..

Thanks for the help..

dc

---

### Post by Iarwain ben-adar on 2006-11-06
No problem :D

Just so you know,
i (and i think most on this forum) do not make a problem of the fact
that you are returning to XP.
The most important thing is that you have your (or your niece's) laptop
working as you (again, or your niece) want(s) it.

When you come back,
we'll try to help you again :D

Anyways,
Hope that it works out for you,

and say happy birthday to your niece ;)


Iarwain

---

### Post by dercoss on 2006-11-07
Thanks; my niece would probably say "whatever"...

I'll be back when I brushed up my Linux skills a little...

Thanks for the help..

dc

---

### Post by dercoss on 2006-11-11
I have just installed Ubuntu 6.10 and the book recommended here has arrived. I shall be digging into it over the next few days..

dc

---

### Post by Iarwain ben-adar on 2006-11-12
Hi,
Nice to hear =)

If you have any questions,
the forum's the place to go ;)


Iarwain

---

