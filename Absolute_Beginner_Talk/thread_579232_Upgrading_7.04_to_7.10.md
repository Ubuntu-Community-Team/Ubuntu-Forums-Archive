---
title: "Upgrading 7.04 to 7.10?"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by bigpilot on 2007-10-18
Is it easy to upgrade? I want to keep all my settings etc.

---

### Post by ronald.higgins on 2007-10-18
Which settings specifically ?

The only thing that really got overwritten that I noticed was my ssh_config, that I had to edit again for my needs, havent spotted any missing apps or files if that's what you mean.

you can run the update using "sudo update-manager -d" , it will prompt you what packages arent supported anymore and will be removed if applicable.

rH

---

### Post by Sef on 2007-10-18
**Back up** your home partition before upgrading.  It is not 100% guaranteed that all will go without a hitch, i.e., any problems.

---

### Post by genbuntu on 2007-10-18
> **ronald.higgins said:**
> Which settings specifically ?

The only thing that really got overwritten that I noticed was my ssh_config, that I had to edit again for my needs, havent spotted any missing apps or files if that's what you mean.

you can run the update using "sudo update-manager -d" , it will prompt you what packages arent supported anymore and will be removed if applicable.

rH

So can I know what exactly will I have to re-edit  after the ssh_config gets overwritten? 
How about the status of the following things:
1) Desktop items
2) Items in home folder 
3) Extra applications that I have installed

I believe the above three will remain safe but just wanted to confirm.

4)My firewall (iptables) settings, power, screensaver settings etc..

5) I have a dual-boot with windows-XP. I hope there is no risk to that. (Note that GRUB is not the primary boot-loader though)

---

### Post by ronald.higgins on 2007-10-18
Well as Sef pointed out, when in doubt ... backup :)

---

### Post by bluefightingcat on 2007-10-18
Hi,

It's the first time I am going to update a Kubuntu distribution. I started with 7.04. When I installed Feisty I made 2 linux partitions. One with a mount point / and one with mount point /home.

I was wondering would it be wiser to upgrade or might it be better to just reinstall from scratch? In case I install from scratch is there a way to keep my /home partition without losing all the data??

BFC

---

### Post by WorldTripping on 2007-10-18
I am wondering a similar thing.

I downloaded Gutsy today, and am going to upgrade from Feisty.

I can happily lose my / and /home as all my data is stored in a LUKS encryped partition that gets mounted when I need it.

My Q's are;

Will I need to re-install dm-crypt and LUKS to access this data after an upgrade ?

Will all my codecs still be in place e.g. libDVDcss2

Will my server still be in one peice, or will I need to reinstall apache php etc ?

Hope someone can help.

---

### Post by Beggar on 2007-10-18
> **ronald.higgins said:**
> Which settings specifically ?

The only thing that really got overwritten that I noticed was my ssh_config, that I had to edit again for my needs, havent spotted any missing apps or files if that's what you mean.

you can run the update using "sudo update-manager -d" , it will prompt you what packages arent supported anymore and will be removed if applicable.

rH

This is the wrong command higgins, from the help:

 -d, --devel-release   Check if upgrading to the latest devel release is
                        possible

The command most users want to run is 

```
gksu update-manager --dist-upgrade
```
or if you have a twisted sense of humor like me, for some odd reason, this works too.
```
gksu update-manager --dist-ugprade
```

---

### Post by Jalazmi on 2007-10-18
hi,

i use ubuntu 7.10 beta, so how i can upgrading to ubuntu 7.10..?

---

### Post by Beggar on 2007-10-18
Jalazmi, if you have the RC (beta as you called it), then just make sure your up to date and you have the final release.

---

### Post by Jalazmi on 2007-10-18
thx Beggar :)

---

### Post by bigpilot on 2007-10-22
Sorry, let me rephrase the question: how can I upgrade KUBUNTU 7.04 to 7.10. I can't find any 'Upgrade System' menu entry (like in Xubuntu and Ubuntu). I tried dist-upgrade too but it said there are no updates.

BTW my Xubuntu upgrade did work flawlessly but I had a strange error: whilst upgrading the XScreensaver OpenGL screensaver kicked in. Thing was, when it prompted me for my password IT DIDN'T RECOGNIZE MY PASSWORD ANYMORE. I just waited until disk activity seemed to cease and then logged in. It seems the upgrading went ok, but I'm not 100% sure.

---

### Post by bigpilot on 2007-10-23
I found instructions how to upgrade Kubuntu 7.04 to 7.10 [here]("http://kubuntu.org/announcements/7.10-release.php#upgrade")

---

