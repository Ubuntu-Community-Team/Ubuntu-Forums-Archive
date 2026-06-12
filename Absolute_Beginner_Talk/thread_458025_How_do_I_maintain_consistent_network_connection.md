---
title: "How do I maintain consistent network connection?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by evolving_monkey on 2007-05-29
Hello all,

I have been able to see other computers with Feisty after install with no configuration or addition of packages. The problem is that sometimes I can see the other two computers on the network and sometimes I can't. I haven't been able to figure out any patterns that point me to a cause. Then again I'm not sure I know enough about Linux to know what I'm looking for. The Windows boxes are having no problems seeing each other. I can access the internet with no problem. How do I make the network more consistent and reliable? Are there other packages I need to install?

Additional information:
-The network consists of a server (Windows Server 2000 Standard) and two other computers with Windows XP Pro (only one XP if I have this one           booted into Ubuntu).
-All computers connect through a Lynksys router all ethernet (router also has wireless but only an HP 7410 All in One Printer connects that way).

Thanks for your time.

---

### Post by esoterica on 2007-05-29
Sounds like a typical piece of crap Broadcom network card causing your problem to me. I have had my share of problems with Broadcom based Wireless cards mainly. Under Linux and Windows, they don't remain connected to the network and constantly drop on you at the worse possible times. The only way to get them connected again is to disable, then reinable the stupid card, or wait forever and sometimes they wil magicly reconnect on their own, this or have to reboot. A real pain in the ***, I have all but one of them finally replaced from all my systems and that one is soon to go as well.

I had  to just about threaten to take Dell to court before I could finally get them to replace their "Dell" branded wireless mini cards built into my laptops (which are actually Broadcom) with the Intel cards. Once I got rid of those Broadcom cards I've never had these problems your talking about again.

Edit:
P.S.
I've also had similar problems with even the high end Linksys cards as well. Seems the only ones I haven't had problems with are the Intel or sometimes the Netgear nic's have worked ok for me. Windows 2000, XP, Vista and Linux

---

### Post by evolving_monkey on 2007-05-29
Thank you for the response.

The nic card that is in this system is an Intel Pro 100 built into the mainboard. It's a Gateway that's a few yewars old. I'll open the box later and see if I can tell the chipset maker but I think that it is an Intel chipset (I could be wrong). I do know that I have never had the problem when I have windows booted. 

I appreciate your time. I will post back with information about the chipset of the onboard Intel Pro 100 nic. 

So far my problems with Ubuntu have been minimal and usually "user error". I can't help but think I might just have something configured wrong.

Thanks again.

---

### Post by lazyart on 2007-05-29
Try setting the ubuntu machines to a static IP address.  For whatever reason that seems to work for me.

---

### Post by esoterica on 2007-05-29
I doubt I'd be able to help you any further, my only experience like this has been solely related to Broadcom nics doing this to me with no fix other than getting rid of them and replacing them with something more reliable. If it's an Intel card in there already though I wouldn't have a guess as to what would be causing what your describing, sorry.

---

### Post by evolving_monkey on 2007-05-29
I have now noticed that when I click on the network browser the windows network icon is still there but when I click on it the name of the network no longer shows up....at all. It seems I have completely lost the ability to see the windows workgroup. I haven't made any changes to anything so I am not sure what has changed.

Can anyone recommend a good web site on Samba and Linux/Windows networking. Is there usually some configuring necessary  or is it supposed to "just work"?

Also, i tried assigning a static ip to the computer after I could no longer see the workgroup. I could still reach the internet but it did not improve the original problem. I changed it back to dhcp.

I should also mention that I have installed any software with regard to the network, not even samba. Initially when I could see the workgroup in the network browser I assumed I didn't have to install anything additional (Feisty 7.04). Is there any additional software I need to install including samba if it is not included by default in the Feisty 7.04 install.

---

### Post by evolving_monkey on 2007-05-29
Actually it looks like samba is not installed only samba-common. Do I need to install anything additional?

---

### Post by esoterica on 2007-05-29
Here's all the info on what your asking. I haven't used Samba in a few years, but back in the day when I did use it it worked very well, but did take some messing with it to get it working. This was back in the day though when everything Linux required some messing with to get it working and just about none of the GUI interfaces actually worked. A lot has seemed to change since then and I'm very impressed by how things in Ubuntu juat actually work as expected.

[https://help.ubuntu.com/7.04/server/C/windows-networking.html](https://help.ubuntu.com/7.04/server/C/windows-networking.html)

---

