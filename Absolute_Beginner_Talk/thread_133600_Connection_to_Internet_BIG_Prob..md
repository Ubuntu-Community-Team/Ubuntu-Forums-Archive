---
title: "Connection to Internet BIG Prob."
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-02-20
Hi
 I finally got everything working after cleaning off the hard drive and re-loading of everything. And I mean everything.
So I thought I might change my WEP key on the router and my D-Link PCMCIA card.
Well I forget to do a save and I didn't get anything changed. I made sure everything was put back to previous state. I re-booted computer and Router.

Now I can only get the Ubuntu Forum web page. All other web pages hang up or only partial display of page. If this sounds impossible I would agree. It seems that every time I make a small unrelated change it brakes something somewhere else. Is anyone else having this problem with Ubuntu? This has happened before.

1. Since it take hours to reload everything is there something I can do to fix the current problem with only some web pages working?  I have turned off the Firewall ( Firestarter) I know the wireless and router work because I can connect to The Forum with them, but only to the forum. What is very interesting is I have the same problems when I connect directly to the router. So I don't think it is a problem with Router because I can connect with Windows and all works OK. I only have Ubuntu on the Hard drive. This makes no sense to me. How can a change that did not successfully occur cause this kind of a problem. 
 I have unplugged the Ubuntu Disk drive and inserted a Windows Hard drive and I can connect to all my web pages via the Bookmarks with the same router. And by the way the Windows system seems to run much faster on bring up WEB pages even though I have made suggested changes to speed up Firefox.
I don't understand why Ubuntu is so slow. I would think it would be much faster than  Windows.

2.Is there a command to see how much space is used by a directory. The information now shown is free space on the whole drive and I don't want to use a calculator to add up each file. . I would like to save some of the directories to CD so it will not take soo long to re-load. This will be probably the last time I am going to re-load Ubuntu. I admit I' m new to linux but  it does not make a lot of sense to be re-loading everything every time one make a small change. Changing a WEP Key should not cause the current problem.
3. Any help would be appreciated. You know the more I think about this, it's crazy. How can one only see one web page.

Thanks

Kent

---

### Post by steve.horsley on 2006-02-20
I have no good ideas about your network problem, except maybe reboot the router too. 

For disk usage the command is **du.** Try frinstance: **du -hc /home/steve**

---

### Post by kent41 on 2006-02-20
[QUOTE=steve.horsley]I have no good ideas about your network problem, except maybe reboot the router too. 

For disk usage the command is **du.** Try frinstance: **du -hc /home/steve**[/QUOTE]
Thanks for the command. And yes I re-booted the Router and it works well with the Windows Hard drive in the same computer.

---

### Post by kent41 on 2006-02-20
Well i have done a hard reset on my router and still i am having problems getting to WEB pages. However i can get to the Forum every time. Is there something hard coded into Ubuntu or Firefox that lets me get to the Forum only ? 

When i try to get something from Google or Yahoo Firefox hangs. Also this time i only installed the Ubuntu CD and did not try to add or  update any other applications.

I still can exchange the hard drive in the laptop and Windows works great in all aspects. 

Does anyone have any ideas on what might be going on here.

---

### Post by steve.horsley on 2006-02-21
This is mighty weird. No, there is nothing special coded into firefox, nor to Ubuntu as far as I know. Since you say you can connect to the other sites but they hang halfway through loading, it's not that DNS is broken but somehow the machine remembers the address of the forums. I really don't know what might be happening. 

Maybe firefox is scrambled somehow. Can you try another browser?

---

