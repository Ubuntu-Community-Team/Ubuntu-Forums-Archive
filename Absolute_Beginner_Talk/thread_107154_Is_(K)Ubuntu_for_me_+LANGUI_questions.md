---
title: "Is (K)Ubuntu for me? +LAN/GUI questions"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by Mathias-K on 2005-12-22
Hi guys.. I've been trying to figure out if Linux was the right OS for me for some time. Having tried Mandriva 2005, SimplyMEPIS, Ubuntu 5.10/6.04F2, Edubuntu 5.10 and Kubuntu 5.10/6.04F1, i must say that MEPIS seems to be the easiest and (K)ubuntu seems to be the prettiest and smoothest for me.

I've read quite a lot of guides and very insightful articles the have given me quite a mixed picture of this community. There seems to be an attitude towards people wanting to rely almost solely on GUI - why is that? Wouldn't it be good to make things fixable via menus? And finally - Is it possible to run and update (K)ubuntu without using the Terminal or should i find another distribution for that?

This leads me to my current network/internet problem with Kubuntu 5.10. I'm unable to access the internet and have tried System Settings - Network Settings. Here my network device is stated Disabled. When i access Administrator Mode and enables it, it whips back to disabled mode after aproximately 1-2 seconds.. Any help without coding back and forth? Is the reason for my problem that i did not configure LAN in the install? Can that be done from my GUI?

I really like the Ubuntu community, i'm just surprised that so many things are done in the terminal when the package programs and the GUI seems so much more easy. What is the reason that almost everything is not made to work by packages and GUI?

I'm not trying to troll anyone, i'm just curious as to why things are run this way. Feel free to correct me - in fact i very much hope that most of my impressions are somewhat wrong :)

Regards Mathias

---

### Post by estel on 2005-12-22
The attitude that GUI == Bad isn't prevailant in the Ubuntu community, I assure you :)

> And finally - Is it possible to run and update (K)ubuntu without using the Terminal or should i find another distribution for that?

Yep, of course :). There are many applications, the included one being **Synaptic** which deal with installation of software. It can also update software, but there's a special Update Manager which will pop-up every time an update is released for any of the packages that you have incstalled.

Mainly, I think that the community talks about the console commands because it's easier to type them than it is to describe a Menu process ;).

---

### Post by localzuk on 2005-12-22
Welcome to linux. In time, most probably, you will realise that one of the greatest powers of ubuntu/linux is the shell (terminal). You can do huge amounts of things here that would take a much longer time to do by GUI (graphical user interface - just in case you are conused).

To try and enable your network card, you must configure the device. You must either tell it to use a dhcp server or a static ip address. For information on this, take a look at the help guide in System/Help in the menus.

Many things that are done in graphical way are very restrictive in what can be done - even in windows. (For example, in order to work properly with network routes you must use the command line in Windows).

---

### Post by Mathias-K on 2005-12-22
Thanks for the info. I guess i was just focusing on some guys who behaved arrogantly towards people preferring GUI over CLI.

Okay, i connect my ethernet cable, click on system settings, network connections. I am told that i need to assume administrator mode.. Okay, i click the button and type my password when i'm prompted only to return to the windows which tells me that i need administrator priviledges..:confused:

---

### Post by localzuk on 2005-12-22
Hi, are you the original user that set up the Ubuntu installation and are you logged in as that original user?

If you aren't then the likelyhood is that you won't have 'sudo' rights.

---

### Post by Mathias-K on 2005-12-22
Yes i am the only and original user.

But even if i wasn't, would i not go into sudo/administrator/root mode if i entered the password?

---

### Post by estel on 2005-12-22
As long as you're on the sudoers list :)

---

### Post by Mathias-K on 2005-12-22
[QUOTE=estel]As long as you're on the sudoers list :)[/QUOTE]

Please explain. There is no other user than this one, then why on earth would it not allow me to be the sudo?

Well, i inserted the CD and had it trying to establish network contact, which failed..? Okay, i thought, then what about a PCI Ethernet card. Then the install would be able to configure the network, but when i enter Kubuntu afterwards, there is still no way to access the internet and there is still the double problem of disabled devices and no way of entering sudo mode. I even tried giving it a false password to see if it was just a strange bug, but then it prompts me that it is false, so it's only when i use the correct password that it does simply nothing :confused: 

Can anyone blame me for having a relaxed feeling when booting back to WinXP knowing that ethernet works right out of the box here? 

Also, is Dapper supposed to solve this "problem" - or rather lack of simplicity versus WinXP?

---

### Post by bscbrit on 2005-12-22
Well sudoers can provide access to root powers to both users and groups.  If your user name is not in the list (and sudoers doesn't care how many users there are, but it usually only places the first user in the list as default) then it won't let you do anything.  If you look at your sudoers file does it contain your user name, and/or does it mention %admin?  If it does, then making yourself a member of the admin group will restore your root powers.  See 'man group' if you need to go down this road.

---

### Post by bscbrit on 2005-12-22
When we get your root powers restored (sounds like the script from a Harry Potter film....!) we can start on your network.  Now your observations about linux being 'harder' than Windows may be true but until we find out what is wrong with the network configuration then we cannot really say.  After all, if you network card is not fitted correctly, you couldn't really blame either linux or Windows.  If there is a missing driver, then that is also something you cannot blame either OS for.  True, for Windows most manufacturers provide a driver and they don't often do the same for linux - but that is the fault of the manufacturer of the network card and not of either OS.
However, linux is different from Windows - if they were the same why would anyone change from one to the other?  You have probably spent years working with Windows (and learning about it, although you probably never thought about it that way) and how long have you worked with linux?  Years, months, weeks, days or hours?  Hardly a fair way to do a comparison.
Sort out your root access, and then on to the network....

---

### Post by Mathias-K on 2005-12-22
When a user is obviously completely lost (+ a totally new Ubuntu user in my case) why don't you just give him a clue what you are talking about? I have never heard about this so-called "sudoers list" - can't someone elaborate? :)

[QUOTE=bscbrit]Now your observations about linux being 'harder' than Windows may be true but until we find out what is wrong with the network configuration then we cannot really say.  After all, if you network card is not fitted correctly, you couldn't really blame either linux or Windows.[/QUOTE]

I'm running a tripple boot system with Windows XP, SimpleMEPIS and Kubuntu 5.10, all fresh and not modded in any way. So i stuck in the ethernet cable in the PCI card that i put in as i said in a post before.

WinXP - Works right out of the box!
SimpleMEPIS - Works right out of the box!
Kubuntu 5.10 - Errors...

How does this compare with your statements that there are no limitations to Linux and that i can't blame Kubuntu?

---

### Post by localzuk on 2005-12-23
The sudoers file is the way of enabling 'admin' rights to a user. It can be used to give general rights or just the right to run one application in admin mode. It can be found at /etc/sudoers.

However, I think that is a red herring as if you are not in that list then you will be unable to alter the list.

The password you enter in the box should be the same as your user account - note: this password will only work for admin tasks in that account, so if you create another user and give them admin rights in sudoers they will have to use their password, yours will not work.

Could you identify which model of network card you have?
Also, could you go to a terminal and type ```
ifconfig
``` and post the output here? (You can put the output in a file by adding > out.txt to the end. It should create a file called out.txt in your home directory).

Linux is not limited and it is likely not Kubuntu's fault, rather as a earlier poster stated it is usually due to bad support by hardware manufacturers.

---

### Post by bscbrit on 2005-12-23
I'm sorry - it wasn't my intention to confuse you further.  Your post #8 gave me the impression that you understood sudo.  I was mistaken and I apologise.  Localzuk has given a further steer but, if you reboot into recovery mode, then you can do what you like whether you are named in sudoers or not, I think.
And if you haven't got sudo rights then we cannot really configure much of your network.

EDIT: I can sense the frustration in your posts and, believe me, we all understand how you feel.  But persevere with us and we will try to get your system up and running as quickly as possible.

---

### Post by bscbrit on 2005-12-23
Try this link from the ubuntu wiki for information about sudo

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

(Thats why its in my interesting reading links)

---

### Post by Mathias-K on 2005-12-24
Hi, i'm trying to post my ifconfig, but it gives me errors when I type "sudo ifconfig out.txt" or just "ifconfig out.txt".. Why is there no graphical way of doing this?

To add insult to injury, I'm not allowed to access /etc/sudoers, and when I try to boot up in safety mode, it gives me a command line and no idea what to type? I tried "X", which just gave me the 100% useless flashy X-screen.

Any suggestions?

---

### Post by bscbrit on 2005-12-24
ok, one at a time now....

The command is

sudo ifconfig >out.txt

Note, the > is important, and there is no space between > and out.txt



Why is there no GUI? -  Well there is, (but without sudo you can't use it, like I have already said) try System -> Administration -> Networking, but also take the time to look at [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm), which also answers the question about the command line.

'Safety Mode' is called recovery mode, and it is based on a command line because it might be the X system that you are trying to recover.....  Chicken and egg, really.  But this way works, especially if you read the link in the previous paragraph.

As I pointed out in the post yesterday at 11:33, when we get the sudoers file sorted you can start on your network.  Please enter recovery mode, and then enter the following commands

cat /etc/sudoers >/home/<username>/out.txt
chown <username>: /home/<username>/out.txt

I do not know your username on your system, but you can fill in the missing <username> _without the < and >_

Reboot into normal mode, and copy the contents of out.txt to your next post.

When we give you back your sudo access, we can start on your network.  Which is why I gave you the link yesterday to [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo).

:D

---

### Post by Mathias-K on 2005-12-24
Hi

sudo ifconfig >out.txt gives me:

eth0   Link encap:Ethernet  HWaddr 00:13:8F:44:20:B9..
       inet6 addr: fe80::213:8fff:fe44:20b9/64 Scope:Link
       UP BROADCAST MULTICAST MTU: 1500 Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
       Interrupt:17 Base address:0xe400

lo     Link encap:Local Loopback
       inet addr:127.0.0.1 Mask 255.0.0.0
       inet6 addr: ::1/128 Scope:Host
       UP LOOPBACK RUNNING MTU:16436 Metric:1
       RX packets:37 errors:0 dropped:0 overruns:0 frame:0
       TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:2672 (2.6 KiB) TX bytes:2672 (2.6KiB)

I can see that the IP address obviously is not right, but i can't do anything about it without sudo rights.. Should i reinstall Kubuntu completely? I can't believe that has to be the way to solve Linux problems..

---

### Post by bscbrit on 2005-12-24
No, just do what I asked you to do in the previous post please. :smile:

Hint FORGET YOUR NETWORK - YOU CAN'T FIX IT UNTIL YOU GET ROOT POWERS VIA SUDO!

"I can see that the IP address obviously is not right, but i can't do anything about it without sudo rights.. Should i reinstall Kubuntu completely? I can't believe that has to be the way to solve Linux problems.."

---

### Post by Mathias-K on 2005-12-24
Okay, i think i got it right (i'm not used to this mix of bleeding egde GUI and absurdly ancient troubleshooting aka Linux :P)

"#/etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
#See the man page for details on how to write a sudoers file.
#

#Host alias specification

#User alias specification

# Cmnd alias specification

# Defaults

Defaults, !lecture,tty_tickets.!fqdn

# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL"

I don't know if that made any sense to you, but it's what i get from doing exactly what you told me to.. Don't you see this kind of troubleshooting as a weakness for Ubuntu?

---

### Post by bscbrit on 2005-12-24
Thats fine - it shows that both 'root' and all members of the admin group have 'root' powers via sudo.  The first is perhaps stating the obvious, the second suggests that your current user name is not a member of the admin group.

Solution.  Make your current user name a member of the admin group.

How. reboot into recovery mode, and type the following

adduser <username> admin

Then, to check that it has worked, type

groups <username>

The system will then show you all the groups that <username> belongs to.  Just check that 'admin' is in there.

reboot into normal mode, and try accessing System -> Adminstration -> Networking.  When it asks for your password, use your normal log-on password for <username>.

---

### Post by Mathias-K on 2005-12-24
When i type:

adduser mathias admin

 i get this message:

'mathias' is already a member of 'admin'

.. but it still does not work. When i enter administrator mode in Network Settings, it just returns to non-sudo mode.. :S

Thanks for your help so far, and merry cristmas :)

---

### Post by bscbrit on 2005-12-24
OK. Time to do a little more thinking.....

Do you have an automatic log on when you first boot up, or do you still have to enter your password?

Things to try.

Create a new user (see 'man adduser')

Add the new user to the admin group using the method that you have just used for mathias.

See what permissions you get.


I might be a little slow in replying over the next few days!  But Merry Christmas and happy ubuntu'ing....

---

### Post by Mathias-K on 2005-12-24
I'll have a go at it..

Thanks for your help so far :)

---

### Post by localzuk on 2005-12-24
You should now add something such as username ALL=(ALL) ALL to the file by using ```
echo "username ALL=(ALL) ALL >> /etc/sudoers"
```

To answer the method of troubleshooting question - no. It is a very good method as it allows the problem to be narrowed down enormously and the root of the problems be dealt with rather than the apparant problems.

Using the command line isn't absurdly ancient, imo. Even microsoft have realised this and are creating a more advanced 'command prompt' which closely resembles the linux one.

---

### Post by Mathias-K on 2005-12-25
[QUOTE=localzuk]You should now add something such as username ALL=(ALL) ALL to the file by using ```
echo "username ALL=(ALL) ALL >> /etc/sudoers"
```[/QUOTE]

I solved the problem by searching through some old threads on this forum and typing 

kdesu kcontrol

which gave me control. I also learned that this is problem is widely known and is a problem in KDE, not Kubuntu, as well as the fact that i has laid reported, yet unsolved in Bugzilla since april.. Which to me is a setback for KDE/Kubuntu.. Let's hope it is solvable for the Dapper release. 

[QUOTE=localzuk]To answer the method of troubleshooting question - no. It is a very good method as it allows the problem to be narrowed down enormously and the root of the problems be dealt with rather than the apparant problems.[/QUOTE]

I have absolutely no chance of ever guessing those codes. If it was all GUI-emphasized i could perhaps find the solution.

[QUOTE=localzuk]Using the command line isn't absurdly ancient, imo. Even microsoft have realised this and are creating a more advanced 'command prompt' which closely resembles the linux one.[/QUOTE]

I was a bit frustrated when i wrote that, and probably a result of my general feeling of Linux alienation. In my opinion it is too "coded" and "geeky" (even though i'd consider myself a nerd :)). For example, when you boot in recovery mode, why is there just a codeline, and not a menu of options perhaps looking akin to the installer? 

Another example is package management. Things are called "xorgaglxdrv" instead of Video Card Driver - why?

But i'm glad i could figure it out with help from this forum.. Onto my next problems - getting codecs.. Happy holidays :)

---

### Post by bscbrit on 2005-12-25
Well, I am not a user of KDE and I'm sorry that I had not heard of this particular problem before.  However, you have now solved the problem yourself (and that must make you feel somewhat bettter?) and I wish you luck with your further exploits in Ubuntu.

---

### Post by Mathias-K on 2005-12-25
This thing might be what converts me back to Gnome.. Or at least i'll make a quad boot between Ubuntu / Kubuntu / Mepis / WinXP sometime this holiday.. Thanks for you help :)

---

