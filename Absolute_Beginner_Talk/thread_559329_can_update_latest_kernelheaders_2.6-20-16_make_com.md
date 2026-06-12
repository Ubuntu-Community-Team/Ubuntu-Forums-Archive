---
title: "can update latest kernelheaders 2.6-20-16 make computer unbootable?"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by ronny_d on 2007-09-25
Hi only people who know about this:


can latest update of kernelheaders 2.6-20-16 make a computer unbootable and unusable?


Or was this a simultaneous "happening" that i had the bad luck to fall into and all i got was: 

cannot find tty


and a flickering at the on/off computer button.... resulting in a breaking down... and unbootable kernel..., it just got stuck and nothing more. I had to buy myself a new computer... (...)



Now, i don't want to mess up this one. Somehow cpu info gives me that i do not have the permissions (very strange!) while i have administration permissions... (in this latest bought secondhand computer):


e:~$ cpu info
cpu: cfg_parse_file: Permission denied
There was an error parsing the configuration file. Exiting.


Can someone who knows for sure on all this, who can tell it with  proven certainty, and who is an expert on this, tell me whether it is possible my former computer was unbootable after upgrading the kernel via automated update from Ubuntu Feisty Fawn because of that kernelheader update or not?



So now i do not dare to update those specific kernelheaders; i just have this other computer a few days... and cannot permit myself the money.



Please, only serious people with knowledge on this reply... Thanks.

---

### Post by alienexplorers on 2007-09-25
The latest Kernel update caused my system to not be able to boot X.  Had to redo the drivers for my video card.  After that it worked fine again.

---

### Post by ronny_d on 2007-09-25
p.s.: i after rebooting (for the kernelheaderupdates to have effect..., well: yes) came into 'cannot find tty' in a black screen and a list of commands i could use (but i could not), none of the commands leading me to Ubuntu... and the whole machine got stuck and broke down, when i unplugged it and plugged it in again it even did not want to boot anymore half and come into 'cannot find tty' **** (sorry) and all i heard was "crack" and saw the on/off button only flicker, it was destroyed, unusable. 


My question so is whether kernelheader update linuxheaders-2.6.20-16-generic and linux-image-2.6.20-16-generic and app-install-data-commercial, this package of "automatic" updates..., can make hardware not suited to boot or whatever the technical logic may be but anyhow making the system unbootable and unusable...? 


I bought this little computer without any system on it, totally empty, then installed Ubuntu from a cd released April 2007 for Intel processors. 


I am talking on a pc (not a laptop) and so it is the desktop version of Feisty Fawn that i have installed for my pc.


Hope someone can answer my questions about this nasty behaviour that i experienced with 'cannot find tty' and other "stuff".

---

### Post by ronny_d on 2007-09-25
> **alienexplorers said:**
> The latest Kernel update caused my system to not be able to boot X.  Had to redo the drivers for my video card.  After that it worked fine again.




Thank you for your reply; but from the drivers it sounds like technical logic to me, but i had no specially installed drivers at all, i had a very simple installation without any special drivers or whatsoever. 


Anyway:what was this **** (really sorry) on 'cannot find tty' and a list of commands i never heard about and no starx command possible, nothing..., just dead. 

So i had no special video drivers at all. And either do i have any special drivers on this tiny nice small computer (pc). 


Kernel updates shouldn't be doing any 'cannot find tty' when no special nvidia or whatever drivers are installed. 


And what does this mean that you say you had to configure x-server again? What do you mean? The whole system is based on x-server..., so i do not understand what you mean (well, that may be because i am no expert). 

How did you configure this x-server from that black screen with 'cannot find tty' then? 

Thank you anyway for your reply. I hope to gain more insight on this.

---

### Post by ronny_d on 2007-09-25
startx 

was what i meant


(but it did not work; for the rest the commands were really strange to me and i did not know what to do with them at all)

---

### Post by ronny_d on 2007-09-25
Anyway, if the boot comes into 'cannot find tty', an automatic choice for 'configure x-server? yes/no" should be there and type: yes. And then the x-server better be there... :) ... but of course!


:lolflag:


(so sorry...)

---

### Post by ronny_d on 2007-09-25
:popcorn: Is it a serious advice (or is it paranoya?) to 'uncheck' these updates:


linux-headers-2.7-20-1
linux-headers-2.6-20-16-generic 
linux-image-2.6.20-16-generic
app-install-datea-commercial

?

---

### Post by ronny_d on 2007-09-25
linux-headers-2.6-20-16, not 2.7-20.16 of course...


(i am going to sleep, i live on the other side of the world)

---

