---
title: "Any guide to managing an infrastructure based on ubuntu?"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by marshall_lai on 2006-11-21
This post is here for mainly 2 reasons:
1)  I am an ubuntu newbie running edgy.
2)  I am planning on running several ubuntu machines for home use and couldn't find ways to effectively manage them centrally....

OK.  Here is the long question.  I am a veteran with Windows network infrastructures (running SBS2003 and 4 XP pros machines at home on an AD domain on the SBS2003).  But I am a complete newbie with ubuntu and linux (well not complete.  I do know how to turn on, install packages, .....  etc basic stuff).

For MS networks, I have to say managing the whole infrastructure is easy with AD.  Almost all the machine settings can be managed centrally via group policies, and patches can be pushed out and managed via Windows server update services.  Anti-virus and anti-spy I am using networked edition of AVG.  Simple.  Life is good.

Now with ubuntu, how can I do the same thing?  Essentially, can I manage the whole infrastructure on my machine including controlling the patching of the different ubuntu workstations, adjusting their policies, centralized login.... etc.  Is there an ubuntu equivalent to the AD infrastructure, application deployment and patch management solution like the sbs2003 can offer?

I am at the stage where I am quite comfortable with my own ubuntu workstation but I will need to manage the computers for other members of my household and they are not computer gurus.....

Any help will be much appreciated.

---

### Post by adamkane on 2006-11-21
Ooh! Hitting Ubuntu right where it hurts. Canonical needs to get an AD replacement going, and they aren't.

This might get you started:

Install LDAP on Ubuntu
[http://times.usefulinc.com/2005/09/25-ldap](http://times.usefulinc.com/2005/09/25-ldap)

LDAP Address Book with Thunderbird
[http://ubuntuforums.org/showthread.php?p=1582401](http://ubuntuforums.org/showthread.php?p=1582401)

Please share anything you learn and find useful!

---

### Post by adamkane on 2006-11-21
As you may know, automatic updates is enabled by default using Ubuntu software repositories. As new patches are made available, every Ubuntu machine downloads the updates.

The question is, do you want to create a local server as your main software repository. You can create a local repository with falcon. Then as your local server is updated or downloads updates, the workstations see the new files, and install them automatically.

You of course would need to create a daily job to "sudo apt-get upgrade". I'm not sure how you would deploy scripts to all your workstations. More research.

---

### Post by marshall_lai on 2006-11-21
Thanks for those but those are only LDAP and does not offer any management solution of the individual workstations that I will need.

Are you implying that centrally managing a pure ubuntu (or any flavors of linux except Redhat.....) is not possible at the moment?  Not even with paid solutions?

That would certain hamper adoption of linux as MS alternatives, won't it?](*,)

---

### Post by marshall_lai on 2006-11-21
Yes I know that updates are automatically downloaded but I am looking for more (much more) than that.  I want to be able to control which workstations get what updates and if possible pushes application packages out to them.  I would also want to be able to see at a glance on which workstation is not updated and why, all of these are pretty much easy and automagically done with windows server update services.......

And I would like a centrally managed architecture where I can assign rights to users for the domain, and also assign specific rights to workstations.  Can this be done in linux?

---

### Post by adamkane on 2006-11-21
I don't have need yet for an authenticated network, so I don't have an answer for you.

Since you said you would be willing to pay for help, I have a very good Linux-based network admin team available to me here in Seattle. They have a real experienced easy-going Linux admin. His name is Mike (or Matt. I can't remember). He's been around for a long time, and always has very practical, affordable Linux solutions for everything. He always helped me remotely, so he should have no problem helping you.

Sorry to offer a paid solution. I use ubuntuforums for most user issues. I use Uptime for most business issues.

If you get an answer, hopefully you'll post it here. Like I said, Ubuntu needs more solutions. 

I know that there are Ubuntu server farms, but I think they deal with issues in a much different way than most MS admins are used to.

Uptime Technology
[http://www.uptimetech.com/](http://www.uptimetech.com/)

TEL: 206-547-1817
TEL: 888-999-0817

[EMAIL="networks@uptimetech.com"]networks@uptimetech.com[/EMAIL]
[EMAIL="security@uptimetech.com"]security@uptimetech.com[/EMAIL]
[EMAIL="info@uptimetech.com"]info@uptimetech.com[/EMAIL]

---

### Post by adamkane on 2006-11-21
Also howtoforge has some good ISP related setups to follow:
[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

---

### Post by marshall_lai on 2006-11-21
So am I correct in assuming that there is no easy and centralized way to manage a network of ubuntu (or linux) workstations?

That's a major bummer.  linux is almost perfect for replacing MS but I guess I will have to downgrade back to Vista.....](*,)

---

### Post by David Marrs on 2006-11-21
I would expect there to be something out there. SuSE and Red Hat are both marketted towards the corporate environment. Perhaps they have something closer to what you need.

---

### Post by 3rdalbum on 2006-11-21
I'm sure Red Hat would probably offer a solution to this - you might want to have a look at CentOS (which is built directly from the RHEL source code).

As far as automatic software updates goes, you would probably run a repository on your server and have the sources.list file on the client computers pointing to your repository; a cron job on the clients would allow you to run updates at scheduled times, and a cron job on the server would keep its own files up to date. I've no idea how to run a repository myself though.

---

### Post by marshall_lai on 2006-11-21
> **David Marrs said:**
> I would expect there to be something out there. SuSE and Red Hat are both marketted towards the corporate environment. Perhaps they have something closer to what you need.

Ouch.  Just read thru Red Hat and Novell SuSE.  The RHEL4 can do this via what they called Proxy Server or Satellite server but the details are very sketchy which makes me very concerned about how it works.

Novell's Zenwork is more promising as it is described in detail on their website.

But here comes the ouch factor:  They costs a boat load of money.......  Ah well, I guess I will have to stick with tried and true MS infrastructures.....  With SBS2003 going for below $400 and the Novell and RHEL asking for $1000+, it kinda defeats the purpose.  Even for home use, MS seems cheaper....

---

### Post by adamkane on 2006-11-21
Hmm..

[http://lwn.net/Articles/206961/](http://lwn.net/Articles/206961/)
> 
Do you pine for a good old days of Active Directory? Does WSUS make[FONT=monospace] [/FONT]your heart throb? Miss these things on Ubuntu? We do and so we have[FONT=monospace] [/FONT]decided to do something about it. Thus I would like announce the[FONT=monospace] [/FONT]creation of the ubuntu-directory team.[FONT=monospace]

[/FONT]What is our mission, you ask[FONT=monospace]? [/FONT]We aim to make Ubuntu rock, both as a client of directory services and[FONT=monospace] [/FONT]as a server of the same.

...



Most interesting.

---

### Post by marshall_lai on 2006-11-21
Yes. I just hope that they can finish all of those in 10 years.....

---

### Post by adamkane on 2006-11-21
NK. They may accomplish one or two goals a year. It's a project I'd like to help with though.

---

### Post by cantormath on 2006-11-21
> **marshall_lai said:**
> This post is here for mainly 2 reasons:
1)  I am an ubuntu newbie running edgy.
2)  I am planning on running several ubuntu machines for home use and couldn't find ways to effectively manage them centrally....

OK.  Here is the long question.  I am a veteran with Windows network infrastructures (running SBS2003 and 4 XP pros machines at home on an AD domain on the SBS2003).  But I am a complete newbie with ubuntu and linux (well not complete.  I do know how to turn on, install packages, .....  etc basic stuff).

For MS networks, I have to say managing the whole infrastructure is easy with AD.  Almost all the machine settings can be managed centrally via group policies, and patches can be pushed out and managed via Windows server update services.  Anti-virus and anti-spy I am using networked edition of AVG.  Simple.  Life is good.

Now with ubuntu, how can I do the same thing?  Essentially, can I manage the whole infrastructure on my machine including controlling the patching of the different ubuntu workstations, adjusting their policies, centralized login.... etc.  Is there an ubuntu equivalent to the AD infrastructure, application deployment and patch management solution like the sbs2003 can offer?

I am at the stage where I am quite comfortable with my own ubuntu workstation but I will need to manage the computers for other members of my household and they are not computer gurus.....

Any help will be much appreciated.

I would use dapper LTS. Its for long term support environments.
Edgy is still working out the bugs.

Here is a guide
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

---

### Post by marshall_lai on 2006-11-21
> **cantormath said:**
> I would use dapper LTS. Its for long term support environments.
Edgy is still working out the bugs.

Here is a guide
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

I think you may have misunderstood my question......

Essentially, I want to be able to centrally manage an entire ubuntu (or linux) infrastructure including:
1)  Central Patch and update management
2)  User based Policies for the whole network
3)  Centralized application deployment
4)  Workstation patch state and software inventory, and other status at a glance centrally.
.... etc

ubuntu as itself serves very well as a standalone workstation for gurus (less of the guru required then before, though).  However, when you try to manage more than a few of these workstations as a group and you have multiple users, it quickly becomes a nightmare.....  Management headaches of the linux infrastructure is the primary reason holding me back to deploying linux (more likely ubuntu) instead of the MS solutions......  Yes RHEL4 and SUSE works.  But it sort of defeats the purpose of being free......

---

### Post by ewl1217 on 2006-11-21
> 1) Central Patch and update management
I've seen suggestions here for automated updates. A simple cron job can handle this.
> 2) User based Policies for the whole network
What exactly do you mean by this?
> 3) Centralized application deployment
I just had an idea for program installation: host a script on a network server, and then have every client automatically download and run it. A simple bash script will do, and a cron job can take care of the automation. I'm sure someone could elaborate on this.
> 4) Workstation patch state and software inventory, and other status at a glance centrally.
 .... etc
This one has me stumped...

For information on cron, run this command:
```
man cron
```

Bash scripting is simple. A basic one would loook like this (in a plain text file):
```
#!/bin/bash
command_1
command_2
command_3
```
I think you get the idea.



Another approach to the entire project would be to have many thin-clients powered by one main server using LTSP. All software and settings would be on the server, but this may not be the best option if you've already made a big investment in your current hardware.

---

### Post by marshall_lai on 2006-11-21
> **ewl1217 said:**
> I've seen suggestions here for automated updates. A simple cron job can handle this.

What exactly do you mean by this?

I just had an idea for program installation: host a script on a network server, and then have every client automatically download and run it. A simple bash script will do, and a cron job can take care of the automation. I'm sure someone could elaborate on this.

This one has me stumped...



First I appreciate the info but a little bit more thoughts:
1)  Patch management is about CONTROL.  I want to be able to centrally control (ie, approve/disapprove an update, uninstall a patch for certain computers, etc).  If I don't need that, I can set all workstations to auto-update like you said and be done.....

2)  User policies in terms of what they can access and not access throughout the domain and internet.  What kind of permissions that they can have consistently on the LAN resources, all done centrally without going thru to each individual workstations.  And being able to control what each user can and cannot do on their machines, and have that be consistent across all the machines on the network.  And I don't mean thin clients type of situations.......

3)  Yes, that's essentially how it is done behind the scenes with MS Windows Server AD infrastructure, with a lot of dressing up in terms of control, permissioning, and management features.  These additions to basic scripts provides an unified way of management (not only install, but also removal, permissioning, and setting up options) are essential to managing the network effectively.  But then, much more than simple scripts are needed to be done to get this working.

4)  Essentially, we need an asset/infrastructure management database for this to work......

Can't we just take the spec of MS management solutions and work it into ubuntu (or linux) and ubuntu will be a killer replacement!

---

### Post by thk on 2006-11-21
> **marshall_lai said:**
> So am I correct in assuming that there is no easy and centralized way to manage a network of ubuntu (or linux) workstations?

That's a major bummer.  linux is almost perfect for replacing MS but I guess I will have to downgrade back to Vista.....](*,)

With free tools, you currently have to build it yourself. There are many ways to do what you want. You just have to learn some scripting tools. Check out cfengine, fai (fully automatic installs) and various ldap solutions. You can have for example centralized fine-grain control over user roles using ldap to set sudoers policy. There are also many commercial solutions like Novell ZENworks.Edit: I'll also mention that centralized inventory and patch management is available if you subscribe to RedHat's enterprise solution. Its all done through a web interface.

---

### Post by marshall_lai on 2006-11-21
[> **thk said:**
> With free tools, you currently have to build it yourself. There are many ways to do what you want. You just have to learn some scripting tools. Check out cfengine, fai (fully automatic installs) and various ldap solutions. You can have for example centralized fine-grain control over user roles using ldap to set sudoers policy. There are also many commercial solutions like Novell ZENworks.Edit: I'll also mention that centralized inventory and patch management is available if you subscribe to RedHat's enterprise solution. Its all done through a web interface.

That's right and it actually cost more than MS SBS2003....  Kinda of defeats the purpose.

MS SBS2003 Standard R2 which can do all of the above (unlimited number of computers for patch management) is selling around USD$350 here in HK retail.  And Window XP Pro OEM (because that's how I will get XP Pro normally), est USD$150.

Redhat Directory Server Small Business bundle:  USD5000.  Redhat WS USD$179.  
Novell Zenworks Management Suite + SUSE ES10. USD 459+349= USD798.  WS USD60 (ok 59.95).  So this will probably be roughly the same as a MS infrastructure for 5 ws and 1 server or less.  But more of a hassle to manage.....

Pretty difficult to justify a switch from MS.  Although I don't particularly like MS products.....

But the FDS seems to be a big step in the right direction....

---

### Post by thk on 2006-11-22
Never said it was cheap. (Unless you build a custom solution for which there are superb tools available like cfengine.)

I actually agree with you though that its currently far too hard to setup a small network of Linux machines with centralized management. My current solution is nfs, ldap + scripts to issue commands on all clients via ssh. My requirements are not very rigorous however. YMMV.

---

