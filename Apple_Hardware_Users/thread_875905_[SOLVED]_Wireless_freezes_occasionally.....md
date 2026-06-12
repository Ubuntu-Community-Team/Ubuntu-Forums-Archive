---
title: "[SOLVED] Wireless freezes occasionally...."
date: 2008-07-31
forum: Apple Hardware Users
---

### Post by Brightbelt on 2008-07-31
Hi,
I'm dual-booting on an aluminum iMac, and things work alright except that occasionally, my wireless just stops working. I have a BCM4328 wireless card.

The wireless "bars" are there on the task bar and they show that I'm connected, but pages hang and do not load online when I'm trying to browse. 

Usually a restart fixes it. But I'd like to know what this is about. And also, I think (although I'm not 100% positive) that this usually occurs after I'm online for a fair amount of time.

Btw, I can't remember for sure whether I use Ndiswrapper, but there's a fairly good chance I do. 

I appreciate any help or ideas anyone might have.

Many Thanks, Frank B.

---

### Post by cyberdork33 on 2008-07-31
> **Brightbelt said:**
> Hi,
I'm dual-booting on an aluminum iMac, and things work alright except that occasionally, my wireless just stops working. I have a BCM4328 wireless card.

The wireless "bars" are there on the task bar and they show that I'm connected, but pages hang and do not load online when I'm trying to browse. 

Usually a restart fixes it. But I'd like to know what this is about. And also, I think (although I'm not 100% positive) that this usually occurs after I'm online for a fair amount of time.

Btw, I can't remember for sure whether I use Ndiswrapper, but there's a fairly good chance I do. 

I appreciate any help or ideas anyone might have.

Many Thanks, Frank B.Yes you use ndiswrapper (it's the only thing that works!).

The problems you experience sound like typical ndiswrapper issues really... you could try other (older / newer) windows drivers, but I don't think there is any really good solution... Also you could try compiling a newer version of ndiswrapper than is in the repos...
[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

---

### Post by Brightbelt on 2008-08-01
Many Thanks Cyber for responding. I'm not experienced at all in compiling versions of programs, so I think I might be courting disaster by trying that. 

I'm still mostly a GUI-sympathetic user, though I do use the command line when I know what I'm doing or I am told where I'm going! :)

Thanks again, Frank B.

---

### Post by cyberdork33 on 2008-08-01
> **Brightbelt said:**
> Many Thanks Cyber for responding. I'm not experienced at all in compiling versions of programs, so I think I might be courting disaster by trying that. 

I'm still mostly a GUI-sympathetic user, though I do use the command line when I know what I'm doing or I am told where I'm going! :)

Thanks again, Frank B.
Compiling ndiswrapper should be pretty easy.

Get dependencies:
```
sudo apt-get install build-essential linux-headers-`uname -r`
sudo apt-get build-dep ndiswrapper
```download your source code and unpack it. Then navigate to the folder in the terminal with cd.

then run:
```
./configure
make
sudo make install
```PS there might not be a configure script, but just try it...

---

### Post by Brightbelt on 2008-08-01
Many Thanks, Cyber! Like I said, if I'm told what to do at the command line, I can try almost anything.

However, I can't even log on to Ubuntu right now - see my thread titled > I installed Proprietary graphics driver, now there's no x server or GUI

I could use your help there too :). I don't even know how I can get to a console there. I used to know more about restoring the x server when I was using PCs a lot, but I'm cautious here on a Mac since it's new to me.

Many Thanks for all your help,

Frank B.

---

### Post by cyberdork33 on 2008-08-01
> **Brightbelt said:**
> Many Thanks, Cyber! Like I said, if I'm told what to do at the command line, I can try almost anything.

However, I can't even log on to Ubuntu right now - see my thread titled 

I could use your help there too :). I don't even know how I can get to a console there. I used to know more about restoring the x server when I was using PCs a lot, but I'm cautious here on a Mac since it's new to me.

Many Thanks for all your help,

Frank B.
I am getting there. I keeps getting bumped to the top so I haven't made it to that one yet.

---

### Post by Brightbelt on 2008-08-01
Here's so we know the outcome, Cyber; I think you were right about there not being any configure script:
```
brightbelt@brightbelt-desktop:~/Desktop/ndiswrapper-1.53$ ./configure
bash: ./configure: No such file or directory

```

Many Thanks for trying... I may read the install file later and see if I can pull it off.

Frank B.

---

### Post by Brightbelt on 2008-08-01
I think I did it! I got the new version installed. 

How can I do a listing in the terminal to make sure which version of Ndiswrapper I am using?

I'm pretty sure, it's the 1.53, since I un-installed the version (1.50) I had through Synaptic. I almost quit and tried to re-download ndiswrapper through Synaptic, but of course, no wireless at that point so I tried installing 1.53 again. 

Many Thanks Cyber,...Frank B.

---

### Post by Brightbelt on 2008-08-01
Got it. This checks the version:

```
ndiswrapper -v
```

I'm on 1.53 - cool.

---

### Post by cyberdork33 on 2008-08-01
see you did it! and did that fix your problem then?

---

### Post by Brightbelt on 2008-08-02
Hey Cyber. Thanks for checking back -  I need to browse for a while and actually see if it makes any difference. 

Btw, when you used the word 'compile' when talking about installing Ndiswrapper, that kind of threw me off. I thought compiling was a more indepth work with the driver code etc. That word has always scared me off for some reason.

I've done some installations like this one here and there; I lean towards Synaptic because it's so easy to make mistakes using the terminal and more often than not, you have no clue why errors are being thrown back at you. 

But it's nice to have the latest version of something too. :)

Thanks, Frank B.

---

### Post by Brightbelt on 2008-08-02
Okay, I've been browsing off and on since last night and so far, no freezes.

Thanks. :)

---

### Post by cyberdork33 on 2008-08-02
> **Brightbelt said:**
> Btw, when you used the word 'compile' when talking about installing Ndiswrapper, that kind of threw me off. I thought compiling was a more indepth work with the driver code etc. That word has always scared me off for some reason. compiling is just turning source code into binary data that the computer can execute. the deb files from the repos (and other locations) usually already contain the binaries. Other systems like red hat, use an rpm format that is similar to deb, and still others always compile from source like gentoo.

> **Brightbelt said:**
> I've done some installations like this one here and there; I lean towards Synaptic because it's so easy to make mistakes using the terminal and more often than not, you have no clue why errors are being thrown back at you. 

But it's nice to have the latest version of something too. :)
Generally, if the version in the repo works, then that is good enough. You should only compile applications yourself if you are getting an updated (or older) version in order to fix a problem or gain some new function that you need.

> **Brightbelt said:**
> Okay, I've been browsing off and on since last night and so far, no freezes.
Good deal!

---

