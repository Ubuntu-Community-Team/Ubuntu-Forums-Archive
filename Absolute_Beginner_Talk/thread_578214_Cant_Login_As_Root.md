---
title: "Cant Login As Root"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by pidu87 on 2007-10-17
I Just installed 7.04 and _cant login as root_ only the account I made.:popcorn:

---

### Post by FredB on 2007-10-17
This is a security feature. If you want to be root, you can do it for a little amount of time (15 minutes every time ?) by using sudo command.

man sudo is your friend.

---

### Post by Cannaregio on 2007-10-17
```
sudo -i
``` if you need root for longer. 
But beware: running your box in root for long periods is going to damage you soon or later.

---

### Post by BertP on 2007-10-17
just a beginner here, but I believe a book I checked out a month ago said that Ubuntu does not create a root account.  It then gave instructions on how to create one, but I have no clue how to do that now.

---

### Post by aysiu on 2007-10-17
You don't need to log in as root. That's why.

Please explain why you *think* you need to log in as root, and we'll explain the proper way to accomplish that task.

---

### Post by Madpilot on 2007-10-17
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

All you need to know about Ubuntu's security model - including how to bend/break it, by doing un-advised things like creating a root login.

---

### Post by Scroobytec on 2007-10-17
> **aysiu said:**
> You don't need to log in as root. That's why.

Please explain why you *think* you need to log in as root, and we'll explain the proper way to accomplish that task.

So far the only reason I have had to log in as ROOT has been to download and install new virus defs when I was testing AVG Anti Virus, and to install one or two applications/packages.

But then I figured out how to do this in the first week of switching to Feisty from SUSE 10.2 and trying Fedora Core 6. As I am a bit impatient and tend to often jump in before having a look, the not being able to create a ROOT password was a bit disconcerting for a while! So then it was RTFM (or forums and blogs in this case) till I found out that it was not required.

Being a Server 2000 and 2003 person makes me want to have "FULL CONTROL":lolflag: so I just HAD to gain control - not that I use it much - these days I hardly ever switch from auto log-on.
[B]
GUTSY IS COMING - JUST ONE MORE SLEEP. IT IS LIKE CHRISTMAS IN OCTOBER!!!!!!!!!!!![/B]

---

### Post by hyper_ch on 2007-10-17
You have full control... but you shouldn't acquire full control all the time like you do on Windoze... just on a per-need basis ;)

---

### Post by FredB on 2007-10-17
> **hyper_ch said:**
> You have full control... but you shouldn't acquire full control all the time like you do on Windoze... just on a per-need basis ;)

Indeed. This is why unix are safer than windows... Not having a root account as default account ;)

---

### Post by hyper_ch on 2007-10-17
> **FredB said:**
> Indeed. This is why unix are safer than windows... Not having a root account as default account ;)

It's one of the reasons why Linux is safer...

---

### Post by GutsyGibbon on 2007-10-17
You don't need it.
As some people have already said, you can use the root with a terminal command.


If you still wish to log in as Root, follow these instructions:
1. Go to "System->Management->Login Screen".
2. Click the "Security" Tab.
3. Check "Allow local system administrator login".
4. Enjoy, you may now log in as "Root".


***GutsyGibbon (Dean)***

---

### Post by FredB on 2007-10-17
> **hyper_ch said:**
> It's one of the reasons why Linux is safer...

Or maybe the main one ?

Having linux-powered pc since end of 2004, I think this is main reason of the safety of linux and other unix like systems.

---

### Post by hyper_ch on 2007-10-17
Well, another highly imported reason is the concept of the software repositories where you almost find anything you need - from a trusted source.

In Windoze - if you don't have the $$$ to buy the software (well, to licence it...) or are unwilling to - then you will hunt it down on warez sites or p2p with a very good chance that it's infected with malware.

---

