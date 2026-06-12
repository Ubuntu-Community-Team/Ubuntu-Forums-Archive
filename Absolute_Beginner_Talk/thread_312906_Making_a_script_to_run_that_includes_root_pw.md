---
title: "Making a script to run that includes root pw"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by linuxbun on 2006-12-05
When I start up my computer, the first thing I want to run is firestarter. I've set this to start up, but it gives me that annoying prompt for password and if I don't enter it in time, it seems to crash my computer.

Is there a way that I can make a script that i can set to run? But a script that has my cmd (firestarter) and somewhere that has the password too?

Theres a few things that I want to run, but it's only firestarter that requires me to enter a root pw.

Any help would be most appreciated!! :)

---

### Post by pandu.rs on 2006-12-05
[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

Q: How can I get Firestarter to load automatically when I log in as a regular user?

In order for a regular user to be able to launch Firestarter, the user must be given additional privileges. Edit your /etc/sudoers file in your favorite text editor and add the following line at the end:
username ALL= NOPASSWD: /usr/sbin/firestarter

Simply replace username with whatever your login is. The specified user is now able to launch Firestarter without being prompted for a password using the command sudo firestarter.

---

### Post by linuxbun on 2006-12-05
Ahh brilliant, only 1 problem - I can't save the change :confused: 

gksudo gedit /etc/sudoers

add my line but when I click save, it says that i'm trying to save to a read only area :o :confused: :confused: :confused:

---

### Post by hyper_ch on 2006-12-05
Have a look at how it's chmodded and change it to rw for the user (e.g. sudo chmod 0755 /path/to/file)

---

### Post by geek_Man on 2006-12-05
Try sudo nautilus (or konqurer), whatever you open in that will be root.

---

### Post by compwiz18 on 2006-12-05
> **geek_Man said:**
> Try sudo nautilus (or konqurer), whatever you open in that will be root.
But be careful, you can delete or modify any file on the computer this way.

---

### Post by linuxbun on 2006-12-05
Nautilus didn't work so I did:

 sudo chmod 0755 /etc/sudoers



then:

gksudo gedit sudoers

**sudo: /etc/sudoers is mode 0755, should be 0440**

So that don't work (that's the error I got back).

So I tried to put it back:

sudo chmod 0440 /etc/sudoers

and got this: sudo: /etc/sudoers is mode 0755, should be 0440

Can't even put it back! :confused: :confused:

---

### Post by compwiz18 on 2006-12-05
oops.  you screwed up.

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

that should get you fixed.  good luck.  log in using recovery mode, reset file permissions to 0440, then log back in NOT in recovery mode.  aysiu's page explains it well, so you should be able to do it.  good luck.

also:

[QUOTE=the Ubuntu wiki]NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. If this happens and at login an error message reports: "Unable to read ICE authority file", log in using the failsafe terminal and execute the command below substituting user for your username.[/QUOTE]

I'm not sure why they say this - it always works for me, but don't say we didn't warn you about that now :P

---

### Post by linuxbun on 2006-12-05
I screwed up? I'm a noob following advice :rolleyes: :confused: 

Thanks for the article, I'll print it out and follow it.. :)

---

### Post by CatKiller on 2006-12-05
That was all quite quick - breaking it and fixing it in half an hour. For reference the sudoers file is deliberately read-only, even for root. The appropriate way to edit it is with the command ```
sudo visudo
```

In fact, it says this in the file itself.

---

### Post by bodhi.zazen on 2006-12-05
> **CatKiller said:**
> That was all quite quick - breaking it and fixing it in half an hour. For reference the sudoers file is deliberately read-only, even for root. The appropriate way to edit it is with the command ```
sudo visudo
```

In fact, it says this in the file itself.

LOL :lol: Hi catkiller !

I agree 100 % re visudo, however I was recently re-educated !

sudoers is NOT read-only for root. You can access and edit the file as root (without visudo). I was in shock and had to check it myself, and yes sudo vim /etc/sudoers allows access with rw. :(

IMO this is a "bug".

You should use visudo because it confirms the syntax of sudo.

> visudo edits the sudoers file in a safe fashion, analogous to vipw( 8 ). visudo locks the sudoers file against multiple simultaneous edits, provides basic sanity checks, and checks for parse errors. If the sudoers file is currently being edited you will receive a message to try again later.

---

### Post by CatKiller on 2006-12-05
> **bodhi.zazen said:**
> Hi catkiller !

:waves:

> I agree 100 % re visudo, however I was recently re-educated !

sudoers is NOT read-only for root. You can access and edit the file as root (without visudo). I was in shock and had to check it myself, and yes sudo vim /etc/sudoers allows access with rw. :(

IMO this is a "bug".

I think yours is broken :-k 

My limited sample size of two has both having /etc/sudoers read only for root. And through your dastardly plan of making me check, I had to struggle to remember how to exit out of vi. Fiend. [-( 

:biggrin:

---

### Post by bodhi.zazen on 2006-12-05
> **CatKiller said:**
> :waves:



I think yours is broken :-k 

My limited sample size of two has both having /etc/sudoers read only for root. And through your dastardly plan of making me check, I had to struggle to remember how to exit out of vi. Fiend. [-( 

:biggrin:

LOL mine is broken then. How did that happen ?

---

### Post by CatKiller on 2006-12-05
> **bodhi.zazen said:**
> LOL mine is broken then. How did that happen ?

:-k ... :-\" ... :-k ... :???: 

I have no idea. I've not managed to do that to mine yet. Even on the two occasions I did manage to break the user authentication mechanisms.

I am surprised that it still works, though.

---

### Post by linuxbun on 2006-12-05
> **compwiz18 said:**
> oops.  you screwed up.

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

that should get you fixed.  good luck.  log in using recovery mode, reset file permissions to 0440, then log back in NOT in recovery mode.  aysiu's page explains it well, so you should be able to do it.  good luck.

also:



I'm not sure why they say this - it always works for me, but don't say we didn't warn you about that now :P


Just done it, that worked, thanks for your help, would have been in a right fix otherwise :mrgreen:

---

### Post by linuxbun on 2006-12-05
> **compwiz18 said:**
> oops.  you screwed up.

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

that should get you fixed.  good luck.  log in using recovery mode, reset file permissions to 0440, then log back in NOT in recovery mode.  aysiu's page explains it well, so you should be able to do it.  good luck.

also:



I'm not sure why they say this - it always works for me, but don't say we didn't warn you about that now :P

> **pandu.rs said:**
> [http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

Q: How can I get Firestarter to load automatically when I log in as a regular user?

In order for a regular user to be able to launch Firestarter, the user must be given additional privileges. Edit your /etc/sudoers file in your favorite text editor and add the following line at the end:
username ALL= NOPASSWD: /usr/sbin/firestarter

Simply replace username with whatever your login is. The specified user is now able to launch Firestarter without being prompted for a password using the command sudo firestarter.

Gonna attempt to add that now, but anyideas how I can add this root command too?

sudo modprobe 18k force=1


I need to do that everytime I boot up to get my fans to work with gkrellm on my dell.

Cheers

---

### Post by compmodder26 on 2006-12-05
> **CatKiller said:**
> :-k ... :-\" ... :-k ... :???: 

I have no idea. I've not managed to do that to mine yet. Even on the two occasions I did manage to break the user authentication mechanisms.

I am surprised that it still works, though.

I'm pretty sure that no matter what the permissions say, root will still be able to write to anything.  For instance, my sudoers file has the permissions of read only for root, but I am still able to edit it in nano/vi/etc. The same goes for any other file as well.

---

### Post by compmodder26 on 2006-12-05
> **linuxbun said:**
> Gonna attempt to add that now, but anyideas how I can add this root command too?

sudo modprobe 18k force=1


I need to do that everytime I boot up to get my fans to work with gkrellm on my dell.

Cheers

Just save that command in a file and make it executable then you can just use the aforementioned method of the sudoers file to call that script.

EDIT:

I can't believe I led you in that direction.  The appropriate action would be to edit the /etc/modules file and add "18k force=1" in that file.

---

### Post by CatKiller on 2006-12-05
> **compmodder26 said:**
> I'm pretty sure that no matter what the permissions say, root will still be able to write to anything.  For instance, my sudoers file has the permissions of read only for root, but I am still able to edit it in nano/vi/etc.

Well mine definitely says [readonly] in vi, and wouldn't let me save with nano. Maybe everyone's is broken except mine? :D

---

### Post by compmodder26 on 2006-12-05
> **CatKiller said:**
> Well mine definitely says [readonly] in vi, and wouldn't let me save with nano. Maybe everyone's is broken except mine? :D

Yeah with vi it complains to me that it is readonly, but I can override that by using :wq! to exit.

---

### Post by CatKiller on 2006-12-05
> **compmodder26 said:**
> Yeah with vi it complains to me that it is readonly, but I can override that by using :wq! to exit.

Man, I really don't know enough about vi.

---

### Post by bodhi.zazen on 2006-12-05
> **CatKiller said:**
> Man, I really don't know enough about vi.

LOL CatKiller. That's vim (if you like color) :p

I understand, but once you get the hang of it, well I find it easier then nano....

[http://www.vim.org/index.php](http://www.vim.org/index.php)
	[http://ubuntuforums.org/showthread.php?t=265392](http://ubuntuforums.org/showthread.php?t=265392)

	Tips:
	[http://www.vim.org/tips/tip.php?tip_id=305](http://www.vim.org/tips/tip.php?tip_id=305)

	Cheet Sheets:
	[http://www.worldtimzone.com/res/vi.html](http://www.worldtimzone.com/res/vi.html)
	[http://www.digilife.be/quickreferences/QRC/VIM%20Quick%20Reference%20Card.pdf#search=%22vim%20cheatsheet%20pdf%22](http://www.digilife.be/quickreferences/QRC/VIM%20Quick%20Reference%20Card.pdf#search=%22vim%20cheatsheet%20pdf%22)

---

### Post by linuxbun on 2006-12-06
After destroying my sudoers file again (whoops!) got it restored and working.

However, after a lot of combinations, I've yet to get this successfully working with firestarter :confused: I put it in the file and saved it, sudo still works but when I kick up firestarter, it just pretends to loads then quits :confused: 

Has anyone else got this working successfully?

---

### Post by compmodder26 on 2006-12-06
Not to distract from the current problem at hand, but is there a particular reason you want firestarter to run at startup?  It is simply just a frontend for iptables.  Meaning that even if you don't make firestarter run at startup, your firewall is still active.  Really, the only reason to open firestarter is to make edits to your firewall settings.

---

### Post by linuxbun on 2006-12-06
> **compmodder26 said:**
> Not to distract from the current problem at hand, but is there a particular reason you want firestarter to run at startup?  It is simply just a frontend for iptables.  Meaning that even if you don't make firestarter run at startup, your firewall is still active.  Really, the only reason to open firestarter is to make edits to your firewall settings.

My firestarter firewall is active even though if I don't start it?

I thought that ubuntu had no firewall installed as default? That's why I went and downloaded firestarter and started it everytime at bootup :confused: :confused:

---

### Post by compmodder26 on 2006-12-06
> **linuxbun said:**
> My firestarter firewall is active even though if I don't start it?

I thought that ubuntu had no firewall installed as default? That's why I went and downloaded firestarter and started it everytime at bootup :confused: :confused:

IPTables is the firewall of linux.  It is on Ubuntu and is running by default.  Firestarter is simply a gui frontend to configure iptables.  The first time you started and set up firestarter, in the background, it changed the configuration of iptables.

Long story short, you do not need to start firestarter every time.

---

### Post by linuxbun on 2006-12-06
I needn't be wasting my time trying to get this to work then, thanks!!! :mrgreen: :mrgreen: :mrgreen: :mrgreen:

---

### Post by compmodder26 on 2006-12-06
To further drive it home, here is a excerpt from the firestarter web site:

> Quitting the program

A frequently asked is question is, what happens when you quit the program. The answer is that the firewall will keep functioning. If you are running Firestarter as a system service, which is automatically set up for you when installing Firestarter from a binary package, the firewall is in many cases even running before you start the program.  

[http://www.fs-security.com/docs/tutorial.php]("http://www.fs-security.com/docs/tutorial.php")

---

### Post by linuxbun on 2006-12-06
Thanks :)

Just making a script now, hopefully I can get my modprobe to work without sudo prompt :-k :D

---

### Post by burek on 2006-12-06
> **linuxbun said:**
> When I start up my computer, the first thing I want to run is firestarter. I've set this to start up, but it gives me that annoying prompt for password and if I don't enter it in time, it seems to crash my computer.

Is there a way that I can make a script that i can set to run? But a script that has my cmd (firestarter) and somewhere that has the password too?

Theres a few things that I want to run, but it's only firestarter that requires me to enter a root pw.

Any help would be most appreciated!! :)

sudo su
gedit /etc/init.d/myscriptiliketostartup.sh 
ln -s /etc/init.d/myscriptiliketostartup.sh /etc/rc2.d/S99myscriptiliketostartup.sh

---

### Post by compmodder26 on 2006-12-06
> **linuxbun said:**
> Thanks :)

Just making a script now, hopefully I can get my modprobe to work without sudo prompt :-k :D

Any modules that need to be loaded into the kernel should go into your /etc/modules file.

So if you were doing "sudo modprobe *modulename arguments*" from the command line.

In /etc/modules you would place "*modulename arguments*" on its own separate line.

IIRC you were modprobing 18k force=1.  So you would place "18k force=1" on its own line in /etc/modules

---

### Post by linuxbun on 2006-12-06
> **compmodder26 said:**
> Any modules that need to be loaded into the kernel should go into your /etc/modules file.

So if you were doing "sudo modprobe *modulename arguments*" from the command line.

In /etc/modules you would place "*modulename arguments*" on its own separate line.

IIRC you were modprobing 18k force=1.  So you would place "18k force=1" on its own line in /etc/modules

Just done that and restarted > working perfectly. Thank you so much :D It's nice to have a system that I can boot up without having to do anything immediately to ensure it doesn't over heat/ is protected etc..:D

---

### Post by compmodder26 on 2006-12-06
Always glad to help :D

---

### Post by linuxbun on 2006-12-06
mwah :D

---

