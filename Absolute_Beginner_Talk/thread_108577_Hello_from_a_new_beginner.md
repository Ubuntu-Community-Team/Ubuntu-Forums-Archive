---
title: "Hello from a new beginner"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by riccoh on 2005-12-26
Hello all,

I have been trying, to no avail, to make Linux work for me. After buying & failing to make Linspire work, I have gotten a set of Ubuntu discs. I am encountering the same basic problem with it as with Linspire; I cannot get to the internet. With Linspire it won't recognize my dsl modem. With Ubuntu I can't even find a place in the software to ask it to LOOK for my dsl modem.
Is there some way to get Ubuntu to look for & configure to my modem, & ask me for user name/passwords, etc? 

I would like very much to jettison XP & it's seemingly endless string of patches, but it's automatic nature is looking pretty good right now. Any help would be appreciated.

Riccoh

---

### Post by paddyg on 2005-12-26
If you've got Ubuntu 5.10, Just take a look at

System-->Administration-->Networking

Glad to hear you are moving on...

---

### Post by kennethalan on 2005-12-26
I've got a similar problem, which I explained in another thread "wireless adsl connection" an hour or so ago.

I've looked at system-admin-networking, and I don't have the slightest idea wht I must do.

Also, I've looked at the help menu, which says to follow Applications-systemTools-Networking,  then to "executre the following command: network-admin" ... 

Hoever, I don't understand where and when I must enter this command.  I've tried typing it in every space that I come across in these network menus, and noting seems to react.  

I installed my DLINK modem/router under windows, but it seemed to work alright with Ubuntu Live when the router was connected by cable to the computer.  Since I've gone wireless (with the same router) I am unable to access internet on Ubuntu live.  

Do I neeed to use the driver disc for the Dlink wireless USB adapter

Monsieur Paddy G, have you got any ideas?

---

### Post by paddyg on 2005-12-26
kennethalan, is your wireless connection successful in windows?
Does ubuntu detect your wireless card correctly?---in terminal just type
```
lspci
```
or
```
dmesg
```

---

### Post by kennethalan on 2005-12-27
THank you for your response paddyg

Yes, under windows the wireless connection works, it's a veritable marvel!  I am using it now.

I don't belive That I have a wireles terminal card.  The wireless connection is established by a DLINK adapter that is plugged into a USB port.

The problem with the instructions that you have given me:  I don't understand at all where I must enter these commands.  I am aa "newbie", habituated to windows, I have never entered a commanded, I have only "clicked" on options proposed to me.  The help menu for the Ubuntu "networking" page gave me some commands as well, but as well I was got lost trying to enter them anywhere I could!

So, please explain in more detail what I must do.

Thanks

---

### Post by poofyhairguy on 2005-12-27
[QUOTE=kennethalan]THank you for your response paddyg

Yes, under windows the wireless connection works, it's a veritable marvel!  I am using it now.

I don't belive That I have a wireles terminal card.  The wireless connection is established by a DLINK adapter that is plugged into a USB port.

The problem with the instructions that you have given me:  I don't understand at all where I must enter these commands.  I am aa "newbie", habituated to windows, I have never entered a commanded, I have only "clicked" on options proposed to me.  The help menu for the Ubuntu "networking" page gave me some commands as well, but as well I was got lost trying to enter them anywhere I could!

So, please explain in more detail what I must do.

Thanks[/QUOTE]

Ok. Lets simplify things. Really. Your card does not work, right? Then we must assume its not a "Linux compatible" card. Not the end of the world, just harder than it working out of the box. This happens often, as wireless card makers are bad about Linux compatibility.

First thing I would do is plug it into your network with a wire. Get on teh internet somehow, even if its a pain. Just temporarily. The alternative is downloading each thing needed on the Windows side and using a pen drive or something to move it to the Linux side and install it with odd commands. Thats not fun. So plug it in for now.

Got that? Ok now you need the terminal. Its under "Applications -> Accessories -> Terminal"

Got that? Good. Next install Automatix. 

That is THE program in Ubuntu, and can fix many other problems for you. But you really need it for one thing in particular. How to install? 

Two commands. Copy and paste them into terminal, one at a time:

```
wget http://beerorkid.com/automatix/automatix-ubuntu_4.0-1_i386.deb
```

Then, when its done:

```
sudo dpkg -i automatix-ubuntu_4.0-1_i386.deb
```

then when its done, close terminal and run Automatix. How? You will find it in:

"Applications -> System Tools -> Automatix"

When it starts hit OK to disclaimers. Then find the checkmark option that says:

> WiFi configurator Graphical user interface

Hit ok. That will install ndisgtk. A developer made that program to give users like you a way to use Windows wireless drivers in Linux. Once Automatix installs it, follow this guide:
> 
Put in the CD-Rom that came with your WPC54G card. Go to System => Administration the last item in this list will now have &#8220;Windows Wireless Driver. Click it, a new small window opens, click on &#8220;Install New Driver&#8221; then navigate to your CD-Rom. Find name of something that end in a .inf, double-click it and you are done. On the left side of that dialogue box you should see the installed driver.
From the same small dialogue box with &#8220;Install New Driver&#8221;, click on &#8220;Configure Network&#8221;. A new dialogue box will appear with a list of your hardware, the first one is your wireless card activate it and deactivate the Ethernet card (for faster boot).
Highlight your wireless card again and click property. Put a check mark on &#8220;Enable this connection&#8221;, type in your ESSID, type in your WEP key.


From this thread:

[http://ubuntuforums.org/showthread.php?t=99490&highlight=ndisgtk](http://ubuntuforums.org/showthread.php?t=99490&highlight=ndisgtk)

I hope that works for you. Sorry its so hard- we are honestly lucky that any solution exists. Windows sure can't use Linux's drivers.

Have a nice day.

---

