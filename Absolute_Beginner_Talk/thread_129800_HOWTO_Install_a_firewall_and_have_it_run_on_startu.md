---
title: "HOWTO: Install a firewall and have it run on startup"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by issueperson on 2006-02-14
Hey all,
I'm new to the Ubantu community and discovered on install that ubuntu does not have a built-in firewall.  Linux tends to be more secure than a windows box, but all it takes is one exploit to completely screw you up.  I highly recommend that one of your top priorities be to install a firewall and have it run at boot.

This will take you through the steps if you aren't too familiar with ubuntu/debian.

Open a terminal and paste this in the window:
---------------------------------------------
sudo apt-get install firestarter
---------------------------------------------
then follow the prompts to install it.

this will install the "firestarter" firewall.  the problem is, you have to have root privlages to run it, so if you don't want to get an error message every time you start your computer about how you don't have permission:

EDIT:[COLOR="Red"]
Open a terminal and type:
----------------------------------
export EDITOR=gedit && sudo visudo
----------------------------------[/COLOR]

and in the file that opens, add to the very last line (replacing "username" with your login name):
-------------------------------------------------------------------
username ALL= NOPASSWD: /usr/sbin/firestarter
-------------------------------------------------------------------
BE SURE TO REPLACE "username" WITH YOUR LOGIN NAME.
now save the file and close it.

This will allow you to run the firestarter program with the sudo command without having to type in your password.

The last step is to get firestarter to boot at startup.
Click on Applications > System > Preferences > Sessions
And click on the "Startup Programs" tab.  
Click "+ Add"
and paste 
--------------------------------------
sudo firestarter --start-hidden
--------------------------------------
into the command line.

next time you boot linux, your firewall should start too (it will appear as a play button icon on your toolbar).

if you want to go ahead and start it without rebooting, you can type in a terminal:
--------------------
sudo firestarter
--------------------
There is also a shortcut to Firestarter installed on the System Tools menu.
Hope that helps some of you.

issueperson

---

### Post by wrtpeeps on 2006-02-14
cheers! Great instructions here!

---

### Post by gibson on 2006-03-07
Hi, thanks for this.... always wanted to get rid of firestarter asking for a password when i login, plus i never knew about the "--start-hidden" parameter :D .

One thing i noticed, however, when you add firestarter in your sessions you use sudo and not gksudo/kdesu. Should we use sudo or gksudo?

Ps - i dont really know what the difference is between these two, but to quote from the Wiki

> NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs....

EDIT: here is the link i used - [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

anyone have any ideas/opinions on this?

All the best

---

### Post by Klaidas on 2006-03-07
gksudo is if you use gnome
kdesudo is if you use kde

---

### Post by kaamos on 2006-03-07
Good howto.

Should be noted though that most of the above is unnecessary unless you want the tray icon. Firestarter can be made to start at boot simply by checking that option in the firestarter preferences. The gui is needed only for changing settings and looking at logs.

To verify that fs is running:
```
sudo /etc/init.d/firestarter status
```

EDIT: also this should never be done!
> 
Open a terminal and type:
----------------------------------
sudo gedit /etc/sudoers
----------------------------------
If you make a typo, you might loose the ability to use sudo! Instead, use
```
export EDITOR=gedit && sudo visudo
```
visudo checks that the file is ok before saving it.

---

### Post by meborc on 2006-03-07
my 2 cents are that gksudo is a **_popup _**that will ask you for your password... but as we are not going to type it anywayz... :rolleyes: i guess we can use both

---

### Post by gibson on 2006-03-07
[QUOTE=Klaidas]gksudo is if you use gnome
kdesudo is if you use kde[/QUOTE]

Hey. Thanks for the fast reply. I should have rephrased my question.

I am aware of the difference between gksudo and kdesu, however.
I work in gnome so lets just talk about gksudo.

When to use gksudo or sudo, as the wiki says use gksudo for "graphical" programs, but in the main post, sudo has been used to launch it... is this a good or bad practice? and what is the major difference between sudo and gksudo?

Hope they clarifies my question

Thanks again
G

---

### Post by meborc on 2006-03-07
[QUOTE=gibson]Hey. Thanks for the fast reply. I should have rephrased my question.

I am aware of the difference between gksudo and kdesu, however.
I work in gnome so lets just talk about gksudo.

When to use gksudo or sudo, as the wiki says use gksudo for "graphical" programs, but in the main post, sudo has been used to launch it... is this a good or bad practice? and what is the major difference between sudo and gksudo?

Hope they clarifies my question

Thanks again
G[/QUOTE]

u should use **sudo** in terminal, but when not using terminal u need a program (gksudo) to issue the sudo command after asking for password via popup... tell me if i'm wrong as i doubt myself :-k

---

### Post by Xian on 2006-03-07
[QUOTE=kaamos]If you make a typo, you might loose the ability to use sudo! Instead, use

Code:

export EDITOR=gedit && sudo visudo[/QUOTE]

This is important and should be changed in the how-to.

---

### Post by towsonu2003 on 2006-03-07
you do not need to run firestarter gui (the thing you see on the desktop) everytime computer boots. it is run with root permissions -> anything that runs on root permissions is a security risk -> it is a security risk (one that is absolutely not necessary). 

once you configure firestarter, it will run in the background, regardless of the gui. ^above poster gave the command[1] for that. the gui is just a frontend for easy configuration. you use it when you need further configuration. 

so? don't autostart its gui on every boot. there is a long thread on this in the security section, check it out.

[1]sudo /etc/init.d/firestarter status

---

### Post by issueperson on 2006-03-08
if you start the gui... however... you can see when you have people pinging away at your IP.

will not having the gui speed things up at all?  what are the benefits besides not having the icon on the taskbar?

also, if someone would like to explain to me what you should do to allow sudo permissions in greater detail (private message will work), i'll edit the howto.  i'm new to the debian/ubuntu world and don't know all the ins and outs.

> visudo checks that the file is ok before saving it.

once i save the file that is opened by issuing that command, it will save it back as the original file but just check it first?

---

### Post by mlind on 2006-03-08
read man page about sudo and visudo. even sudoers file says it MUST be edited
with visudo. 

I recall having issues running firestarter with root permissions
without password on Dapper. It was related to display permissions
that should have been granted using xhost or xauth.

I dunno if it was my configuration tho.

---

### Post by kaamos on 2006-03-08
visudo creates a copy of the original /etc/sudoers and then you can edit the copy. When the files is saved, visudo checks that it is ok and then copies it ovet /etc/sudoers.

---

### Post by Pekz0r on 2006-03-17
I can't find the package with apt-get install firestarter

I can't find anything like in with apt-cache search ether

Please help me

---

### Post by steve.horsley on 2006-03-17
[QUOTE=Pekz0r]I can't find the package with apt-get install firestarter

I can't find anything like in with apt-cache search ether

Please help me[/QUOTE]

Have you added the multiverse and universe repositories to Synaptic?
[http://wiki.ubuntu.com/AddingRepositoriesHowto](http://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by Pekz0r on 2006-03-17
Thanks, but the probelm is that i don't have a GUI so i can't follow that guide. 
I've been searching the forum but i can't find anything about how you can do that

---

### Post by towsonu2003 on 2006-03-17
closely following that wiki page, edit your sources.list:
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo nano /etc/apt/sources.list

and uncomment repositories in that text file. nano shows important keys at the bottom of the screen.

---

### Post by Pekz0r on 2006-03-18
OKey, thanks:D

Edit: i get the following error when i try to start fs: 

(firestarter:8598): Gtk-WARNING **: cannot open display:

What does that mean? And what is wrong?

---

### Post by steve.horsley on 2006-03-18
Firestarter is a GUI front-end for the firewall. It (like all other Linux GUI firewalls) writes scripts that configure iptables. Iptables is the inbuilt command-line packet filtering thingy.

Without a GUI, you can't run firestarter and therefore can't have it write the script for iptables. You will either have to write an iptables configuring script by hand, or perhaps rustle one up by running firestarter on a machine that does have a GUI, then copying the script across. But I'm not 100% sure how it arranges for the script to be run every time Linux boots.

---

### Post by Pekz0r on 2006-03-18
hmm, okey

Are there any firewalls for terminal servers?

---

### Post by mlind on 2006-03-18
[QUOTE=Pekz0r]hmm, okey

Are there any firewalls for terminal servers?[/QUOTE]

IPTABLES is a firewall built in linux kernel. Firestarter is just a GUI frontend for
configuring rules for it. You can edit iptables rules from terminal session too
if that's what you're after.

---

### Post by mlind on 2006-03-18
[QUOTE=Pekz0r]OKey, thanks:D

Edit: i get the following error when i try to start fs: 

(firestarter:8598): Gtk-WARNING **: cannot open display:

What does that mean? And what is wrong?[/QUOTE]

If you get this error after configuring NOPASSWD sudo permission for Firestarter,
it's because root is not allowed  to use X server as output device without user's
permission.

---

### Post by towsonu2003 on 2006-03-18
I don't know any terminal firewall scripts, but I'm sure there are. check out this howto [http://www.linuxguruz.com/iptables/howto/iptables-HOWTO.html](http://www.linuxguruz.com/iptables/howto/iptables-HOWTO.html)

---

### Post by Kersus on 2006-03-19
Okay, I followed the edited instructions in the first message.

I went to run Firestarter, not there.

I got the universe multiverse repositories.

I got firestarter.

BUT, when I try and run Firestarter it says "ppp0 is not ready"

Yes I am connected.  I'm using it right now to type this.  Firestarter even has a received and sent numbers on it (which keep going up) for ppp0, but will not start.

What do I do?

---

### Post by Unicast on 2006-03-19
Ok, here's an interesting one for you....

I've installed Firestarter and configured it to start at start-up, and get the "play" symbol in the system tray. Ok so far.

But when I visit [THIS SITE](http://www.auditmypc.com/whats-my-ip.asp) it tells me what my "external" IP address is AND my private IP address. :-k 

Question is, how do I configure Firestarter to block the retrieval of my private address?

---

### Post by towsonu2003 on 2006-03-19
@Unicast: You can't. afaik people use proxies to mask own ip address. firewall will only block/allow incoming and outgoing requests / traffic. nothing more. 

@Kersus: I am not sure, but try restarting firestarter, go to preferences>network, change ppp0 to something else, save and close (exit firestarter), start it again, and choose ppp0. I'm not sure whether this will work. I do this when I switch network interfaces and firestarter forgets to refresh its settings.

---

### Post by Unicast on 2006-03-20
[QUOTE=towsonu2003]@Unicast: You can't. afaik people use proxies to mask own ip address. firewall will only block/allow incoming and outgoing requests / traffic. nothing more. [/QUOTE]
Thanks but I think you missed my point. :D

That site reports your private (internal) IP address assigned to your machine by your router. SPI (stateful packet inspection) is not implemented on my router's firewall - hence the installation of Firestarter. But it looks like even Firestarter allows external sites to grab your private (internal) IP address.

Incidentally I know all about the use of proxies to try and hide your external ISP-assigned IP address - I'm not intereted in doing this. I'm more concerned about keeping my private (internal) IP address private - if you see what I mean. :D

---

### Post by towsonu2003 on 2006-03-20
[QUOTE=Unicast]
That site reports your private (internal) IP address assigned to your machine by your router.[/QUOTE]
oops -sorry I missed that part by a mile :oops: I'm pretty much ignorant about routers, so I shut up ;)

---

### Post by steve.horsley on 2006-03-20
That's not a firewall problem. 

Either your browser is telling it your IP address, or you are using a proxy that's telling it. That web site can't reach in and find out on its own. If it's your browser that's telling it, don't blame the firewall for not censoring the connection contents.

Strangely, the site doesn't find my internal address, even if I enable javascript. I use firefox.

---

