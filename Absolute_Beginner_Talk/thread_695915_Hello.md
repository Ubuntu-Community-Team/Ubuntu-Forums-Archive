---
title: "Hello"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by cool11 on 2008-02-13
Hello Everyone, 
This is my first post on this community and i am new to ubuntu and linux. I would be installing ubuntu on my system in a few days and would like to ask you which is the best antivirus, antispyware and firewall for Ubuntu. I am using Zonealarm for my windows OS.
Would be needing more help later,

Thanks and regards

---

### Post by phr0ze on 2008-02-13
You won't need any. Linux has the firewall built in. Though I always recommend a home router in any case. As for anti-spyware and anit-virus, these threats just don't exist in the wild for ubuntu. There is less risk of getting infected using ubuntu than there is with windows running these products.

John

---

### Post by Paqman on 2008-02-13
That's easy to answer!

Ubuntu has a built-in firewall, you won't need to install one. There is a handy GUI for configuring the firewall called Firestarter, but it doesn't need to be left running. Just run it to configure things if you need to, then shut it down.

Antivirus/antispyware aren't needed at all. There aren't really any virus threats in the wild for Linux. Spyware is unheard of because we install all our software from repositories which are maintained by trustworthy sources.

Welcome, by the way!

---

### Post by cool11 on 2008-02-13
not even a firewall?

---

### Post by Paqman on 2008-02-13
> **cool11 said:**
> not even a firewall?

Good, isn't it? :)

---

### Post by jaytek13 on 2008-02-13
You don't really need any of these utilities. Ubuntu along with most Linux distributions come with a preconfigured firewall called iptables. The default configuration is more than adequate for most people, but if you would like to have a GUI frontend to edit the ports and whatnot you can use firestarter.

As far as antivirus and spyware, it's really not necessary. Not only are most viruses and spyware written for Windows, it would be incredibly difficult for someone to actually write a virus for Linux that would affect your system in any way due to how permissions work. Most consider having either of these on your system a waste of resources that will just slow down your computer.

---

### Post by firestormx37 on 2008-02-13
As the two posters above said, the firewall is integrated into the operating system.  You don't need to install one, because the firewall is active just by starting the computer.  You can configure the options for the firewall with Firestarter.

---

### Post by seventhc on 2008-02-13
While av isn't needed, if your friends from windows send you files that you may forward to someone else using windows you can use clam av if you want. It isn't for your protection so much as theirs.
I used to use it, but I don't anymore.
Firewall is built in, it's called iptables. If you want a gui for it you can install firestarter but you don't need to.
iptables starts up with your machine and if your using a router that too would have a firewall.
Firestarter is something I used to use also, but now I don't.

---

### Post by phr0ze on 2008-02-13
As stated, the firewall function is built in. It requires very little care from most users.

EDIT: Wow, these posts are coming fast on this one. Can you feel this is one of linux/ubuntu's bragging points.

---

### Post by Paqman on 2008-02-13
> **seventhc said:**
> It isn't for your protection so much as theirs.


I tend to take the point of view that it's their responsibility to protect their systems from Windows threats. I don't use my machine for work though. If I did I would probably scan things as a courtesy.

---

### Post by cool11 on 2008-02-13
Wow that is really nice and thanks so much for so many replies, got most of it but does iptables allow program control?

---

### Post by Paqman on 2008-02-13
The default setup for iptables won't block anything that you install.

---

### Post by jaytek13 on 2008-02-13
The default configuration is that all ports are blocked, but if program X needs to use port Y, iptables will open port Y for the program, and close port Y once the port is no longer needed to be open.

---

### Post by cool11 on 2008-02-13
Thanks for the info [:)]

---

### Post by cool11 on 2008-02-13
One more thing what is the "repository" all about?

---

### Post by jaytek13 on 2008-02-13
A repository is just a location where you can install files from. For instance, if you wanted to install from a cd, you would use the cd as your repository. Typically repositories are http addresses. Most of the ones you would need are already enabled in the synaptic package manager for you (system->administration->package manager), but sometimes you would need to add a repository if you wanted to install something that wasn't in the default ones included.

---

### Post by TheBoat on 2008-02-13
The following is a link to one of Ubuntu's help documents. It explains the repositories and how to use them.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by seventhc on 2008-02-13
> **Paqman said:**
> I tend to take the point of view that it's their responsibility to protect their systems from Windows threats. I don't use my machine for work though. If I did I would probably scan things as a courtesy.
I agree. but on the same level, I wouldn't want to be the person responsible for messing up someones machine. Might make me look bad, but I guess I don't care to much since I have stopped using it lol
But truth is, at this point in time, I haven't been trading any files back and forth.

---

