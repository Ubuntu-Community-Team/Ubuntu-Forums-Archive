---
title: "lots of help needed =)"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by newbie_jhay on 2006-02-06
hi guys.... im just a new linux user and its quite a different experience for me though coz i found almost everything amazing except for a few things which i would really appreciate all the help you would give:

first, i did a dual boot between windows xp and ubuntu 5.10. everything was installed successfuly except that the ubuntu os seems to be quite slow, opening different applications (since i'm trying to explore everything) takes a lot longer even if im just opening a single application at a time.... 
i also checked on the device manager and it seemed that ubuntu hasn't recognized my mboard and processor yet... do i still need to do some updating of drivers and kernels? if i need to, where can i find or d/l these updates?

the next problem i encountered was that im having some difficulties trying to configure my internet connection? I am using a dsl connection which still requires me to enter a username and password and dial in to be able to connect....

I would really, really, really appreciate all your help.... i'll be waiting for ur replies... thanks very much guys =)

---

### Post by Perfect Storm on 2006-02-06
What's your computer specs?

---

### Post by newbie_jhay on 2006-02-06
hi, im sorry i forgot to mention that  =] ... 

im using an athlon xp 1600 and my mboard is an asus a7s333 w/ an sis745 chipset... ubuntu has already detected my vcard, soundcard, as well as my nic....

and by the way, my dsl connection also uses PPoE... as i was reading a thread here a while ago, someone stated a bit of a problem with the said connection, but i wasn't able to read the whole thread.... sorry.... =(

---

### Post by Perfect Storm on 2006-02-06
Open the terminal and write:
```
sudo apt-get install linux-k7
```
reboot.
This kernel fits your computer better.

I need to know which 3d card you have if you want to speed up things.

> dsl connection

Sorry have no experince with that, I'm a cable guy ;)

---

### Post by newbie_jhay on 2006-02-07
ei artificial intelligence, tnx for the info... i'll be trying it later when i get home... thanks so much!

---

### Post by ezphilosophy on 2006-02-07
Well, I think I can help you out with the pppoe problem.  I had the same problem.

[http://www.ubuntuforums.org/showthread.php?t=67629](http://www.ubuntuforums.org/showthread.php?t=67629)

So, first go to the command line and type

sudo pppoeconf

It will guide you through including asking for your username and password.  However, there seems to be a bug.  The fix link is:

[http://ubuntuforums.org/showthread.php?t=67117](http://ubuntuforums.org/showthread.php?t=67117)

This worked for me and I have no problems.

Hope this helps.

---

### Post by newbie_jhay on 2006-02-08
ei guys.... sorry for all the troubles, but i still am unable to fix these things, and the worst part is, i think i made a new problem again....

well first, i tried doing what artificial intelligence suggested with the 
#sudo apt-get install linux-k7, but here's the message that i got:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-k7

i've also tried doing it with and without the installation cd but same thing.... i've also tried doing something which i found in one of the threads i've read (sorry, i forgot which thread it was, again),

sudo apt-get install build-essential linux-headers-uname-r
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-uname-r

i've also tried substituting uname with my user name but same thing still, and i've also tried it with the installation cd in, but, to no avail.....

the thing is, after i tried these things, i rebooted my pc, and then, my resolution was just fixed to something lower than 800x600  i think it was something like 600x400 or something like that (sorry, i forgot the exact resolution)... i checked on the device manager, and it still recognized my video card (which was an nvdia geforcefx 5200), but i was unable to change my resolution and refresh rate which was fixed at 60.

and with regards to what ezphilophy suggested with the pppoeconf, it worked me through the configuration of my connection, but when i opened up firefox and tried browsing some websites, it seemed that i still am not connected to the internet.... (though i think i just missed something on that coz i haven't read all the threads and links that u've given =]....)

anyways, im really sorry guys if i seem to be quite a dummy here, its just that its something that's really new to me.... i really appreciate all the help that u've been giving me and i hope u won't get tired answering my questions.... thanks again so much!!!! :)

---

### Post by numbersix6 on 2006-02-08
> but i was unable to change my resolution and refresh rate which was fixed at 60

Try this, it worked for me:) 

> sudo dpkg-reconfigure xserver-xorg

---

### Post by newbie_jhay on 2006-02-09
ei guys.... im back... tnx numbersix6 for the info, it really helped a lot. i have now reconfigured my desktop.... tnx so much!!!

i hav also configured my dsl connection and i can now connect to my isp.... so that brings me to this question: could i do the apt-get install linux-k7 and direct it to download the file from the internet? could you recommend any sites for that.... 

im sorry for buggin you guys this much about this problem, its just that i think that i could still maximize my system's performance once i updated my kernel... i've also read another thread about updating the kernel, its somethin like the base kernel installed is 386 (something like that, and same as mine)... and it could still be upgraded to suit systems like mine for maximum performance.... i also would want to d/l some drivers which could be used for ubuntu to recognize my mboard coz i'm still not sure if others stuff like my usb ports would function normally....

again guys, i really appreciate all the help you've been giving me and im really thankful that all you guys here are really really really helpful!!! =)

---

### Post by kingsidy on 2006-02-09
if you are connected online apt-get install will do. or just select it from the base system menu in synaptic

---

### Post by newbie_jhay on 2006-02-09
hi kingsidy, tnx for the quick reply.... i've tried it again while online and here is the error i got:

apt-get install linux-k7
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

im not really that familiar with this error and again, i would really appreciate all your help.....

and before i forget, would it somehow be related with what i did before regarding my problem with reconfiguring the screen resolution. here's what i did:

 sudo dpkg-reconfigure xserver-xorg

and it really worked in helping me reconfigure my screen resolution (tnx again numbersix6)....

tnx again for the help!

---

### Post by kingsidy on 2006-02-09
you have two instances of the package manager running. you can only run one at a time make sure that the update and anything that has to do with package manager is closed. also make sure that you are not using it at the terminal either. then open synaptic, go to the base system and then install the k7 kernel

---

### Post by newbie_jhay on 2006-02-10
helo, i've been trying what you suggested in sypnaptic but i can't seem to find the linux-k7 kernel there? does it have another name for that? i've also tried looking for anything related to a k7 kernel but still can't find one? are there any other download sites for that?

and one more thing, regarding the dpkg, is there a way to stop that job? i've tried using the:  

#killall dpkg 

but to no avail.... another thing about that, is there a way where i can display the running jobs? i've tried doing 

#jobs

and even tried

#sudo jobs

but no effect... as in nothing happens.... i'm really sorry for being quite dumb here =)

but i really really do appreciate all the help...

tnx again guys!

---

### Post by r4ik on 2006-02-10
In Synaptic use the search option type K7 hit enter and it will pop up.

---

### Post by newbie_jhay on 2006-02-19
hi guys, sorry if i took a long time to reply back here, i've been busy with school....

i've tried doing all search in synaptic with regards to k7 but it yielded no results... but i guess its my fault... a friend of mine who also uses ubuntu told me that i might need to have universe and multiverse activated first... though i'm not really sure how to do that, but fortunately, my friend gave me a link on the how-to's for that....

anyways, thanks guys for all the help... i really appreciate it! =)

---

### Post by steve.horsley on 2006-02-19
Enablint the multiverse and universe repos is good, because it brings in a much wider choice of easy to install s/w, but linux-k7 is part of the base repository. It's there. See my screen attached screen shot.

But you could always do it from the command line:
sudo apt-get install linux-k7

---

