---
title: "Several questions--am floored with polish of Ubuntu"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by tall8 on 2006-06-17
I installed Ubuntu by accident, having downloaded the installation rather than the live CD and it then began installing itself (I obviously pressed the wrong key to try to stop it). In any case, to my surprise, it then perfectly partitioned the HD and I now have dual boot Windows XP and Ubuntu. I found it then rather simple to install several printers (Brother, HP) and download updates automatically, even to install another program (Thunderbird). I'm tremendously impressed with this program, it being far better than the other live discos I tried and, in addition, aesthetically beautiful. But several questions: do I need an anti-virus program or firewall to run with it and, if so, how do I get these. I use OpenOffice and Firebird with my Windows (this being about 99% of my activity with my pc's) and the Firebird with Ubuntu seems different as I can find no privacy section on it for the passwords (did I miss it?). It wouldn't play a DVD (I installed it on my laptop) but I learned from another posting that Linux isn't Windows and so doesn't have such commercial supports as codecs. To install Skype under Linux seems tremendously complicated compared to Windows so I'll use both OSs but not bother getting the VISTA Windows when it comes out. All in all,  Ubuntu is so polished that I'm floored. One more thing, is there an equivalent of the Windows Disc Clean or is this unnecessary with Linux? Also, it seems as if some of the instructions refer to a DOS like format but I'm leery of making changes there. It seems it would be like playing with the Windows registry settings with great potential to mess things up. Best.

---

### Post by Lord Illidan on 2006-06-17
Firebird is an ancient application. It is now called Mozilla Firefox, and is currently at version >1.5. You had better update your Firebird from [www.mozilla.com](www.mozilla.com).

Antivirus and firewall.. I don't think you need an antivirus. For a firewall, you could try firestarter.

Do ```
sudo apt-get install firestarter
```

DVD support : [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Skype : [https://wiki.ubuntu.com/Skype?highlight=%28Skype%29](https://wiki.ubuntu.com/Skype?highlight=%28Skype%29)

DiskClean : No, you don't need it.

DOS Like format. I assume you are referring to the command line, activated under Applications, Accesories, Terminal. This is perfectly safe to use as long as you know what you are doing, and is the preferred tool, in fact. Nothing to do with the registry:-({|=

---

### Post by user1397 on 2006-06-17
[quote=tall8]do I need an anti-virus program or firewall to run with it and, if so, how do I get these.[/quote]ubuntu already comes with a firewall, but there is a graphical GUI program to control it, called firestarter.  If you like your computer to be secure, just control it using firestarter.  You can install it via System > Administration > Synaptic Package Manager.  And no, you don't need an anti-virus, as linux doesn't really have any right now.  But, if you have windows computers in a network with an ubuntu computer, you can use the anti-virus if you have a mail-server, or as a filter of windows crap, to safe-keep your windows pc's.
[quote=tall8]I use OpenOffice and Firebird with my Windows (this being about 99% of my activity with my pc's) and the Firebird with Ubuntu seems different as I can find no privacy section on it for the passwords (did I miss it?). [/quote]I believe you can find it under Edit > Preferences > Privacy > Passwords.
[quote=tall8]It wouldn't play a DVD (I installed it on my laptop) but I learned from another posting that Linux isn't Windows and so doesn't have such commercial supports as codecs.[/quote]just follow this guide (look at the dapper part only, as i'm guessing you installed dapper, not breezy): [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)
[quote=tall8] To install Skype under Linux seems tremendously complicated compared to Windows so I'll use both OSs but not bother getting the VISTA Windows when it comes out. [/quote]actually, skype is a lot easier to install than you think.  Just follow this guide: [https://wiki.ubuntu.com/Skype](https://wiki.ubuntu.com/Skype)
[quote=tall8] One more thing, is there an equivalent of the Windows Disc Clean or is this unnecessary with Linux? [/quote] i'm not sure, but I do know that kubuntu has one, called kleansweep.
 [quote=tall8]Also, it seems as if some of the instructions refer to a DOS like format but I'm leery of making changes there. It seems it would be like playing with the Windows registry settings with great potential to mess things up. Best.[/quote]actually, the "DOS-like" format is the ever-friendly terminal.  It is used for many things in linux, such as changing system-wide settings and installing/removing programs, so start becoming unafraid of it.  Plus, it's very safe, since ubuntu uses sudo.  Read this for more info: [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by Sef on 2006-06-17
> Antivirus and firewall.. I don't think you need an antivirus. For a firewall, you could try firestarter.

Do
Code:

sudo apt-get install firestarter



Before doing that code do this one:

```
sudo apt-get update
```

then

> sudo aptitude install firestarter

aptitude is an updated apt-get.  Much easier to unstall with aptitude than apt-get.

As for an anti-virus, it is not needed, unless you use an email client.  For even though viruses will not harm your system, they can sit on top of it, and thus you could send them to your friends who have Windows.

---

### Post by user1397 on 2006-06-17
[quote=Sef]Before doing that code do this one:

```
sudo apt-get update
``` 
then ```
sudo aptitude install firestarter
```[/quote]actually, for aptitude to really work, you first need to do ```
sudo aptitude update
```not```
sudo apt-get update
```  to make it even easier, you can combine two commands like this: ```
sudo aptitude update && sudo aptitude install firestarter 
```

---

### Post by xael on 2006-06-17
Firefox includes a tab for Privacy, just click Edit > Preferences & you'll see it.

---

