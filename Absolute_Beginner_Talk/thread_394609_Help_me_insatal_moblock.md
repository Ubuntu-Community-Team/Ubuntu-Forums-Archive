---
title: "Help me insatal moblock"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Rick123 on 2007-03-27
Hi all, i need a walk through how to install moblock. And i think its very important to use moblok. 
On my xp i got peerguradian 2 and its a most have if you are a downloader like me. But i cant instal moblock because i cant linux, the ony thing i know is were the terminal is, dont know what the terminal do, yes i know you can copy text from internet and paste it in there and stuff happen =).
Any way heres an anddres to another thread about moblock and how to install it :

[http://www.ubuntuforums.org/showthread.php?t=192559&highlight=moblock](http://www.ubuntuforums.org/showthread.php?t=192559&highlight=moblock) 

does not make sense of it??

heres whats happen when i tryed by my slef:


> [B][I]Edgy eft (6.10) Installation instructions


    Install these two debs (netfilter libs)
    [http://www.ubuntuforums.org/attachme...d=11647417](http://www.ubuntuforums.org/attachme...d=11647417) 58
    [http://www.ubuntuforums.org/attachme...d=11647417](http://www.ubuntuforums.org/attachme...d=11647417) 58[/I][/I][/B]

So i click on the text and a autodownloader downloaded the stuff, then it was some kind of an automatic installer to, name: gdebi pack instaler, so i use it and think it instald went well, but i dont know were the file has gone tho? =(



[B]> Add to /etc/apt/sources.list
Code:

deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main[/B]

So i dont know what to make of this? ad to: /etc/apt/source.list, okay dont understand, but i tryed write it in terminal, accses denied!? ok the i tryed write the deb text, so i copy this two lines that says something about httpmoblock-deb etc etc to the terminal at once, have tryed them separat too and then push enter, comand not found? 


> [B]Run these commands (in terminal), to accept packages from moblock-deb
Code:

gpg --keyserver subkeys.pgp.net --recv DEDA0559
gpg --export --armor DEDA0559 | sudo apt-key add -[/B]

Okay now we come to some text that really says: run this in terminal, so i thought, i try to write it in the terminal and see what happen, And its worked, the hole hell breaked lose, allot of text was floding my eyes i mean =), so after i copy paste that text i really dint know what i have done we come to the next part.


> [B]    Install it!
    Code:

    sudo apt-get update
    sudo apt-get install moblock-nfq[/B]

like it say, install it, but i dint try this command because i got the rest wrong, So i thought i try to do a post and see if you can help me install and get moblock working for me,

thanks, and yes my english could be better, hehe =) but it isnt.

---

### Post by sisco311 on 2007-03-27
> So i dont know what to make of this? ad to: /etc/apt/source.list, okay dont understand, but i tryed write it in terminal, accses denied!? ok the i tryed write the deb text, so i copy this two lines that says something about httpmoblock-deb etc etc to the terminal at once, have tryed them separat too and then push enter, comand not found?
write this in the terminal:
```
gksu gedit /etc/apt/sources.list
```
enter your password
this will open a file
copy and paste this lines at the end of the file:
> deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main
save the file and exit from the text editor(Ctrl+s, Alt+F4)
repeat the last step(write this in the terminal):
```
sudo apt-get update
sudo apt-get install moblock-nfq
```

---

### Post by Rick123 on 2007-03-27
Thank you very much, i did what you told me and i think it worked!

 I saw,  what i figure out was moblock instaling with level 1 and 2 protection. I dont know if you know this or not but i ask anyway, 

now when i have installed moblock, were is it?? were did it go, how do i access, how do i see what its blocking? isnt moblock like peerguradian with an nice interface? how can i be sure moblock is running?

---

### Post by gingin on 2007-04-10
go to system-administration - sympatic p.m.

in sympatic p.m .  status then search moblock

---

### Post by oni5115 on 2007-05-10
I'm having an issue as well, I can find moblock in the package manager, but there are two of them.  ipq and nfq.  The problem is that neither of them install properly because of dependency issues.

the ipq version says:
libc6 (>=2.3.6-6) but 2.3.6-0ubuntu20.4 is to be installed

the nfq version says:
libc6 (same as above)
libnetfilter-queue1 (>=0.0.12) but is not installable
libnfnetline1 (>=0.0.16) but is not installable
libnetfilter-queue1 but is not installable

I'm guessing the libc6 requires a kernel update? :confused: 
The others I'm not sure about at all really.
I'm using Dapper Drake, so that could be why they are not working.  Anyone know how to get around this?

---

