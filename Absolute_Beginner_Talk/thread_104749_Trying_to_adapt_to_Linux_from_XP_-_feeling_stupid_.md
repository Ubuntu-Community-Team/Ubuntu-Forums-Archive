---
title: "Trying to adapt to Linux from XP - feeling stupid  :)"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by dwasifar on 2005-12-16
I just installed Ubuntu as a dual-boot on an XP machine.  I've been working in the Microsoft world since MS-DOS 3.0 and I know my way around Windows pretty well, but now with this new structure to learn I feel like a moron.

Here are the first two things I'm trying to figure out how to do:

1) Update Firefox to v1.5
2) Import my Gaim settings from Windows

For Firefox: I've downloaded the tarball and unpacked it to a folder on the desktop, but double-clicking the installer does nothing.  When I try to copy the files manually instead, Ubuntu tells me I don't have write access to the folder.

For Gaim: I brought the .gaim folder over from my Windows box on a thumb drive.  Ubuntu does not show me that folder on the thumb drive unless I rename it to remove the leading dot.  I have found a gaim folder in /etc/ but when I try to copy the files from the thumb drive I get the same write access error.

Obviously I need permissions, but I don't recall being prompted to set up a root password at any point in the Ubuntu install.

Is there a good noob-level primer somewhere on what kinds of Linux files go where and how to access them, aimed at the Windows user?

---

### Post by teaker1s on 2005-12-16
root is accessed by 'sudo' or 'gk sudo' or 'sudo su'
example 'gksudo nautilus' will give you a file browser as root in a launcher command
in terminal use 'sudo mycommand'
or 'sudo su' will give you root

[https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29](https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29)
[http://www.ubuntuforums.org/showthread.php?t=104701&highlight=firefox](http://www.ubuntuforums.org/showthread.php?t=104701&highlight=firefox)

---

### Post by Zimmer on 2005-12-16
[QUOTE=teaker1s]root is accessed by 'sudo' or 'gk sudo' or 'sudo su'
example 'gksudo nautilus' will give you a file browser as root
in terminal use 'sudo mycommand'
or 'sudo su' will give you root[/QUOTE]

Just a note...
the password you will be prompted for when invoking   sudo     is YOUR user password...

eg.  your username= fred    and password = flintstone

when you    sudo  <anyoldcommand etc...>
it will prompt for password and expect 'flintstone' .
further sudo commands will not prompt for password in that Terminal session, until a certain time limit is reached (I forget how long...)...
For general Linux stuff..try here..
[http://www.tuxfiles.org/](http://www.tuxfiles.org/)
But for Ubuntu specifics...
I used this a lot to get started and as a resource for most problems encountered.
[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)
and this is a reasonable quick read...
[http://www.psychocats.net/essays/linuxguide.php](http://www.psychocats.net/essays/linuxguide.php)

and I used some of this to save time installing 'essential' software (packages they seem to call 'em over here)
[http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23](http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23)

There is also AUTOMATIX which is more comprehensive, 
[http://www.ubuntuforums.org/showthread.php?t=66563](http://www.ubuntuforums.org/showthread.php?t=66563)
..but I have not used it, so cannot comment on it...
Have fun...
Zimmer

---

### Post by kwaanens on 2005-12-16
When it comes to Gaim settings, you want to put your personal settings in /home/yourusername

In Nautilus (file browser): Tools > Preferences > Make sure the "hidden files" stuff is shown.
Now, you will be able to view directories that begin with "."

Put your .gaim directory in /home/yourusername. Start Gaim, and see what happens.

Don't play around with sudo and stuff unless you (more or less) know what you're doing. Ask questions here, and people will probably answer you pretty fast.

- Ketil

Edited because of stupid typo

---

### Post by kwaanens on 2005-12-16
It's weird that you guys don't tell the newbie to use his home folder, instead of screwing up his/her system with playing away with sudo...
Just my opinion...

- Ketil

---

### Post by teaker1s on 2005-12-16
think  that comment is a little strong, 
1)This isn't paid support
2)I assume very basic's are known and if there not then most people will question more and get an answer
3) why not help this person instead of finding fault

---

### Post by kwaanens on 2005-12-16
Firefox 1.5: Read all posts in [this]("http://ubuntuforums.org/showthread.php?t=96595") thread before deciding to use 1.5. I'm personally addicted to upgrading my software, but this time I'll wait. The difference isn't that huge...

---

### Post by teaker1s on 2005-12-16
As stated your home folder is for all your programs etc

---

### Post by teaker1s on 2005-12-16
when you feel the need for commands

[http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)

---

### Post by kwaanens on 2005-12-16
[QUOTE=teaker1s]think that that comment is a little strong, 
1)This isn't paid support[/QUOTE]

I saw a disaster warning in this thread, because this could complicate things very much for OP. It was not my intention to offend anyone.

[QUOTE=teaker1s]2)I assume very basic's are known and if there not then most people will question more and get an answer[/QUOTE]

I got the distinct impression that OP didn't know the basics. Otherwise the use of /home for user settings would be how he/she solved the gaim question. Implying that one should put user settings in the program folder is a bit much...

[QUOTE=teaker1s]3) why not help this person instead of finding fault[/QUOTE]

That's what I did in my first post in this thread :)

Again, not my intention to offend anyone!

- Ketil

---

### Post by teaker1s on 2005-12-16
okay, I've just had one of those days, my appologies if i was chewy

I dragged myself off xp and I'd recommend take it slowly remember the forum search and wilki are good-If you can't find a thread someone will always help so don't be shy:KS

---

### Post by 23meg on 2005-12-16
I'll have to do some off topic chipping in, apologies to the OP.

> **teaker1s]1)This isn't paid support[/QUOTE]That doesn't mean it has to be bad support. You can cause damage and confusion by giving substandard help, and instead of doing so it's better not to give help about things you don't know well about said:**
> 2)I assume very basic's are known and if there not then most people will question more and get an answerYou should read posts more carefully; the OP is stating that they don't know the very basics.
[QUOTE=teaker1s]3) why not help this person instead of finding fault[/QUOTE]If there's fault in the help given, it has to be pointed at. Not doing so will result in people giving worse, less useful help over time. Once again, you don't absolutely have to help people; it's better to stand back in areas where you're not quite knowledgeable. I don't intend to help anyone about KDE problems aside from the very basic facts because I simply don't use KDE and don't know its inner workings as well as I know those of Gnome.

---

### Post by 23meg on 2005-12-16
[QUOTE=dwasifar]
Is there a good noob-level primer somewhere on what kinds of Linux files go where and how to access them, aimed at the Windows user?[/QUOTE]
I can add this to what's already been suggested: [http://www.builderau.com.au/program/work/soa/10_things_you_should_know_about_every_Linux_installation/0,39024650,39219801,00.htm](http://www.builderau.com.au/program/work/soa/10_things_you_should_know_about_every_Linux_installation/0,39024650,39219801,00.htm)

---

### Post by mistergq on 2005-12-16
[QUOTE=23meg]I can add this to what's already been suggested: [http://www.builderau.com.au/program/work/soa/10_things_you_should_know_about_every_Linux_installation/0,39024650,39219801,00.htm](http://www.builderau.com.au/program/work/soa/10_things_you_should_know_about_every_Linux_installation/0,39024650,39219801,00.htm)[/QUOTE]

That is a great article.  Thanks for posting it! :)

---

### Post by TeeAhr1 on 2005-12-16
[QUOTE=kwaanens]Firefox 1.5: Read all posts in [this]("http://ubuntuforums.org/showthread.php?t=96595") thread before deciding to use 1.5. I'm personally addicted to upgrading my software, but this time I'll wait. The difference isn't that huge...[/QUOTE]

On a freshly installed system it *shouldn't* be a problem, AFAIK.  The issues in backporting (from what I read) seem to be things like breaking installed plugins, wrecking user settings, and such.  I installed it manually, following the steps in [this]("https://wiki.ubuntu.com/FirefoxNewVersion") wiki.  The only problem I've had: I get some "chrome registration error" nonsense every time I install a new extension and restart Firefox, but then it loads up normally, the new extension's there, and everything seems to work fine.

Disclaimer: I don't know about anyone else's problems with it, I'm just reporting on my own experience.

---

### Post by dwasifar on 2005-12-16
Thanks, guys, for all your help.  I have successfully passed both hurdles - Gaim settings are in place, and Firefox 1.5 is installed.  

I feel a little less moronic now.  :)

---

