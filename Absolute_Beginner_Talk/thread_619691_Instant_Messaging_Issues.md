---
title: "Instant Messaging Issues"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by TWO on 2007-11-21
Hello.

I've have tried several IM programs on Ubuntu ranging from KDE Kopete to Gaim/ Pidgin, aMSNand on each I have had no luck in having a program that works completely. In fact, I don't ever remember having ever had one working in the few months I've been using Ubuntu.

I know that Pidgin works fine for me on Gutsy Gibbon, however for other incompatibility issues, I'm holding back from updating again for a little while at least.

The problem is that none of the IM programs are able to read my account. Most display my MSN Messenger groups but then stop and display that there is a "Reading Error."

I know that there is nothing wrong with my account, as I occasionally access it via Windows. I'm wondering whether this is a problem to do with Feisty Fawn, or whether there is just some thing that I seem to keep missing. I have read a fair few forums to try and resolve the issue but to no avail.

Any suggestions would be greatly appreciated. :KS

---

### Post by bluepowder7 on 2007-11-21
when i was using Feisty, i would see GAIM cutting off my connections to yahoo and msn on a regularly sporadic basis.  it would drop, and then a few moments later would be able to reconnect to each service.  it seemed to do it more with msn than yahoo, though.  i haven't had it happen more than once in Gutsy, though...

---

### Post by Junk_head on 2007-11-21
Have you tried the latest build of pidgin? i had some connection problems myself in the first 2.0 release.

---

### Post by 1337455 10534 on 2007-11-21
Yeah, try compiling that one for yourself. That way you can see if any errors come up that you might not have by just getting a deb.

---

### Post by TWO on 2007-11-25
OK. I attempted to install pidgin according to instructions from the following link: [http://neoaddict.wordpress.com/2007/10/01/compile-pidgin-221-from-source-in-ubuntu/](http://neoaddict.wordpress.com/2007/10/01/compile-pidgin-221-from-source-in-ubuntu/)

I managed to get Pidgin up and running however I was still faced with the same error problem as before, even though I had success with the program on Gutsy

(I haven't kept the Gutsy version because of other issues.)

The problem now is trying to remove the compiled package.

When I type "sudo apt-get remove --purge pidgin" the terminal goes through the motions and tells me that nothing has been removed because the package wasn't installed. 

This is what is displayed:

[PHP]~$ sudo apt-get remove --purge pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package pidgin is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/PHP]

Does anyone know how I go about finding and removing the packages? Contrary to the terminal message, Pidgin IS installed, and is accessible via my applications menu.

Any suggestions would be greatly appreciated.

---

### Post by philinux on 2007-11-25
How did you install pidgin in the first place? If you didnt use apt then this may be why it knows nothing of it.

By the way i use Kopete for msn with yahoo and have had no probs with feisty or gutsy.

---

### Post by TWO on 2007-11-25
> **philinux said:**
> How did you install pidgin in the first place? If you didnt use apt then this may be why it knows nothing of it.

By the way i use Kopete for msn with yahoo and have had no probs with feisty or gutsy.

I compiled it according to instructions from a site.

I too have tried Kopete and yet still have been plagued by the same error. It just doesn't seem to be able to read my account for some reason, and I know that the account is accessible too...

---

### Post by 1337455 10534 on 2007-11-25
cd 
sudo make uninstall

---

### Post by linux noooob on 2007-11-25
upgrade to gutsy and use amsn you get offline messages nudge and dual display pic and even drawing plugin!!

*note oddly enough when i installed it on strait debain with gnome it had a wink plugin!!

---

### Post by TWO on 2007-12-11
> **linux noooob said:**
> upgrade to gutsy and use amsn you get offline messages nudge and dual display pic and even drawing plugin!!

*note oddly enough when i installed it on strait debain with gnome it had a wink plugin!!

I am still having no look with the programs at all. aMSN and Pidgin fail to access my account. Pidgin reporting a "reading error" whilst aMSN says that there is a server error, or that it "fails to connect to server."

Very annoying, as I have had Pidgin working on a previous install of Gutsy and now it just doesn't want to work. aMSN is giving me no signs of hope either.

---

### Post by grim192 on 2007-12-11
i'm having problems with [amsn](http://ubuntuforums.org/showthread.php?t=635913) too since the system locked up and i had to do a hard reboot

grim

---

### Post by TWO on 2007-12-13
I'm still having a really hard time with this!!

I seem to have come a step forward in that I came across an article which mentioned something about switching to HTTP method in the messaging program. The writer of the particular thread that I read, said he switched to the method because his firewall was blocking "Microsoft Server Ports" and I'm quite certain that something else mentioned switching methods on account of an overly restrictive network. 

Having switched to HTTP method myself I can at least now access my account for a time, but I have the problem of being unable to see my contacts online. They appear online for a short time but the status of the lot changes to offline, as does my own.

It appears that I am actually still online, as a contact managed to start a conversation with me, purely to ask why I kept signing in and out! 

It's a really annoying problem, and it has stopped me from using msn for several weeks now, and I really would like to avoid reverting to Windows as much as possible.

If there is anyone out there with similar problems or any advice, I would really appreciate it!

Thanks 

TWO

---

### Post by seventhc on 2007-12-13
try this

sudo apt-get remove &#8211;purge pidgin pidgin-data

---

### Post by spiderbatdad on 2007-12-13
have you looked at mercury messenger? is that the same as amsn? I thought mm was once dmsn. Anyway it worked pretty well for me when i used an msn account. Has video too

---

### Post by TWO on 2007-12-14
> **seventhc said:**
> try this

sudo apt-get remove –purge pidgin pidgin-data

Heh =D>

I have already removed Pidgin! Have you also had problems with it, or could you not resist an opportunity for sarcasm?

:lolflag:

---

### Post by seventhc on 2007-12-14
oh, sorry, maybe I misread an earlier post. I thought you got an error trying to remove it first.
wasn't be sarcastic, my pidgin is working fine v 2.2.1

but I has seen this...

> [COLOR=#000000][COLOR=#007700]~$ [/COLOR][COLOR=#0000BB]sudo apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]get remove [/COLOR][COLOR=#007700]--[/COLOR][COLOR=#0000BB]purge pidgin 
Reading package lists[/COLOR][COLOR=#007700]... [/COLOR][COLOR=#0000BB]Done 
Building dependency tree        
Reading state information[/COLOR][COLOR=#007700]... [/COLOR][COLOR=#0000BB]Done 
Package pidgin is not installed[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]so not removed 
0 upgraded[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]0 newly installed[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]0 to remove [/COLOR][COLOR=#007700]and [/COLOR][COLOR=#0000BB]0 not upgraded[/COLOR][COLOR=#007700].[/COLOR][/COLOR]

---

### Post by TWO on 2007-12-15
> **seventhc said:**
> oh, sorry, maybe I misread an earlier post. I thought you got an error trying to remove it first.
wasn't be sarcastic, my pidgin is working fine v 2.2.1

but I has seen this...

Ah, my apologies too. That was the case a little while ago, but I think I mentioned after that I had removed it. I beginning to think the network I access the internet by (for the moment) might be part of the problem, however using the HTTP method though more successful, is still giving me problems. It doesn't seem to maintain the connection and sometimes [on kopete] says that I am offline when I am actually online but all my contacts also appear offline...

Rather annoying. :confused:

---

### Post by TWO on 2007-12-27
Update.

I seem to be having more success with aMSN with regards to accessing my account.

HTTP method seems to be giving me less grief for now. When I access the internet from behind a less over-protective network like this, maybe I'll be able to have more success...

I do sometimes still get problems with messages not being delivered during conversations though.

---

### Post by seventhc on 2007-12-27
I havent had any probs to speak of. I have had 1 prob with amsn so far which was when I created an away msg for christmas ( Merry freakin' Christmas), then deleted it, but for some reason it still shows up. No idea why, but it isn't something to make me quit using it just yet lol. I use msn b/c i have a lot of people that open their cams which works flawlessly, and I still use pidgin for my yahoo account. I don't particularly care for kopete, but if I need cam funcionality in yahoo, that is what I use.
What do you mean when you say some mesgs arent delivered??
If it's what I am thinking, then that isn't amsn, it is actually on their end. I have had that happen, but It seems to only happen with certain people, and they usually verify the fact that they have issues.

---

### Post by tibellus on 2007-12-27
I think I have the most annoying issue ever :)) Pidgin gets stuck from time to time, and I can't do anything. I can talk for a few minutes with my contacts and then the "miracle" happens: Pidgin won't respond to anything and I have to use the forced quitting technique (if I might say so...). This thing happens on Ubuntu Gutsy, I never had this problem with Feisty.

Also, I've uninstalled the older version of pidgin, and installed the latest .deb package, which is 2.3.0. The same thing happens, nothing changes... What could be the reason behind this?

---

### Post by TWO on 2007-12-28
> **seventhc said:**
> 
What do you mean when you say some mesgs arent delivered??
If it's what I am thinking, then that isn't amsn, it is actually on their end. I have had that happen, but It seems to only happen with certain people, and they usually verify the fact that they have issues.

You may be right that it only happens with certain people as I do remember not having a problem with everyone's messages. 

(In fact, I think I might be confusing that with an issue I had with Pidgin.)

Yeah come to think of it, that's been a rare problem for me in aMSN recently.

However, how well does your aMSN deal with offline messages? I remember logging in and being notified that I had 11 offline messages. On clicking it, the program froze then displayed a bug error. 
Leaving offline messages for other people doesn't seem particularly fluid either...

---

