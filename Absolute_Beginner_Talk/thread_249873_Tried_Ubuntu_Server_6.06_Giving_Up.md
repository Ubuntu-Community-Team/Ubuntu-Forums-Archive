---
title: "Tried Ubuntu Server 6.06 Giving Up"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Sulaco on 2006-09-03
New to Linux, have ubuntu desktop on one box, tried server on another.   Got command prompt on server.  Tried get-apt update, get-apt upgrade, get-apt install ubuntu-desktop, got package not found error.  Tried a few different tactics, no success.  Going Back to Windows server, much easier

---

### Post by Klaidas on 2006-09-03
If you can't do a > sudo **apt-get** install something  (more likely, you can't bother to google it/wiki it/ask about it) then linux is not for you.
Have a good day.

---

### Post by Sulaco on 2006-09-03
I have googled and other things for 5 hours trying to get around this, no luck.  I dont whinge on first error message

---

### Post by Tomosaur on 2006-09-03
Well, a server is a server. If you need a GUI, download the desktop version, or just do:
sudo apt-get install ubuntu-desktop

---

### Post by seshomaru samma on 2006-09-03
This forum is for support. If you need help ,many people are willing to help you. if you want to inform us that you are moving back to windows then you should probably post in a different section - Ubuntu Cafe , for example.

---

### Post by Klaidas on 2006-09-03
> **Sulaco said:**
> I have googled and other things for 5 hours trying to get around this, no luck.  I dont whinge on first error message

Who told you that you can learn Linux in 5 hours?
Anyway, I don't want to start flaming/trolling/etc.

---

### Post by Sulaco on 2006-09-03
As I said, I tried that, apt-get install ubuntu-desktop, got package not found.  That is the point.  Seems ubuntu is a throwback

---

### Post by PingunZ on 2006-09-03
Dude, try this :

**sudo aptitude** update
**sudo aptitude** upgrade
**sudo aptitude** install ubuntu-desktop

---

### Post by PingunZ on 2006-09-03
And btw, enable your universe/multiverse sources.

**sudo nano /etc/apt/sources.list**

and remove the ' # ' before the rules saying 'deb ' or ' deb-src '

---

### Post by Tomosaur on 2006-09-03
Either way - If you're serious about being a sysadmin or whatever, you may as well take the time to learn how linux works via the terminal. It really is a lot more powerful and fast than the GUI. You could also try an alternative desktop like Fluxbox. For any GUI, you will need to have the X-Server running, so download that too. Lynx is a terminal-based web browser, but I've heard there are better ones available, so you can do some researching without switching to a different OS.

---

### Post by Sulaco on 2006-09-03
Thanks for the tip, unfortunately, it didnt help.  got the same error, package not found after letting it update, upgrade, etc

---

### Post by Sulaco on 2006-09-03
Thanks Ping ofr the, tip, unfortunately it didnt do the trick

---

### Post by Klaidas on 2006-09-03
NoX guide to the rescue - [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by Aristotle3 on 2006-09-03
I'm having trouble getting a GUI to work too.  I installed 6.06 server, and did "sudo apt-get install ubuntu-desktop," but something seemed to install.  I reboot, and type "startx," and get a "snowy" screen with a black x in the middle...totally frozen.  What am I doing wrong?

I tried the guide above ([http://www.psychocats.net/ubuntu/nox)](http://www.psychocats.net/ubuntu/nox)), and when I type "sudo /etc/init.d/gdm start" I get "command not found" (after installung ubuntu desktop).  Startx goes to "snow."  I try to reinstall ubuntu-desktop, but it says "dpkg was interrpupted" and I need to manually run something (which I guess means its already installed). 


PS- I tried installing the desktop version, but it installs an empty, useless GRUB that doesn't boot even though I do the same install procedure as the server (see my other post).  So either way I can't load a GUI.

---

### Post by seshomaru samma on 2006-09-03
> **Aristotle3 said:**
> I'm having trouble getting a GUI to work too.  I installed 6.06 server, and did "sudo apt-get install ubuntu-desktop," but something seemed to install.  I reboot, and type "startx," and get a "snowy" screen with a black x in the middle...totally frozen.  What am I doing wrong?

PS- I tried installing the desktop version, but it installs an empty, useless GRUB that doesn't boot even though I do the same install procedure as the server (see my other post).  So either way I can't load a GUI.

What is your hardware?
Perhaps you need to reconfigure X 
run this:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by az on 2006-09-03
> **Sulaco said:**
> Thanks for the tip, unfortunately, it didnt help.  got the same error, package not found after letting it update, upgrade, etc

If you are not on the net, it can not fetch the packages for you.

I guess all the tutorials regarding Ubuntu server expect that your box is connected to the net.


You need to enable the online repositories in your /etc/apt/sources.list

These repos are turned on by default when you install.  But they are dissabled if you are not on the net when you install. You need at least the main repo to install ubuntu-desktop and universe to install xubuntu-desktop.

Yes, windows server will be easier for you.  

Don't call Ubuntu a throwback just because it doesn't suit you.  It seems that it is much too powerful for you.  If you absolutely expect your server OS to provide a graphical environment, you are not ready for linux.

---

### Post by az on 2006-09-03
> **Aristotle3 said:**
> I'm having trouble getting a GUI to work too.  I installed 6.06 server, and did "sudo apt-get install ubuntu-desktop," but something seemed to install.  I reboot, and type "startx," and get a "snowy" screen with a black x in the middle...totally frozen.  What am I doing wrong?

PS- I tried installing the desktop version, but it installs an empty, useless GRUB that doesn't boot even though I do the same install procedure as the server (see my other post).  So either way I can't load a GUI.

The server kernel does not play well with a lot of desktop hardware.

Try installing linux-386 and that will install the desktop kernel.  Perhaps that will fix your display problems.

As to why you get a borked grub using the desktop install, I don't know.  The installer backend is exacly the same - did you do anythig different?  Did you reformat your partitions, for example or did you keep the existing data?

---

### Post by gary4gar on 2006-09-03
> **Klaidas said:**
> If you can't do a  (more likely, you can't bother to google it/wiki it/ask about it) then linux is not for you.
Have a good day.
+1 totally agree with you

---

### Post by Aristotle3 on 2006-09-03
I'm connected to the internet, and it downloads stuff when I installed the desktop, and I tried sudo dpkg-reconfigure xserver-xorg.  It goes through a lot of stuff, and then stops.  

"sudo /etc/init.d/gdm start" gives "command not found".  startx gives snow.

I have a standard, unaltered gateway2000 desktop with a NVidia MX2 400, 512 ram, 1.8GHz Intel CPU, intel MOBO...should work.  I ran Suse 10.1 on it for a while and it worked fine.  I left SUSE 10.1 because the support forums were much less active than those on ubuntu.

So a server install fails to give a GUI, and a desktop install fails to go past the word "GRUB" (GRUB seems empty).  I did the same reformat of the second partition with both the server and desktop installs, and used the exact same settings on the partition manager (OSX on 1st partition, clarkconnect on the 3rd, and ubuntu on the 2nd).  

Ironically, OSX is the most stable install on any of my machines, and its on an old Gateway2000.  I wonder if it can be used as a SAMBA/FTP server.

---

### Post by CurlyBlue on 2006-09-03
Pretty amazed at this

I have been playing with Ubuntu for about a week now and I have persevered with some bloody annoying problems but all the time I have had help & support from the people here.

Still havent solved my Nvidia card issue yet (see thres called "xserver crashed") but I am halfway there.

Also my sound card isnt working yet.

These are just challenges and by working the issue and getting the help of people who have far more Linux knowledge than I do the problems are always workable.

Thought "workng the problem" might have been a primary tenet of a sysadmin.

Anyway - what the hell do I know - only been in IT 25 years!

Good Luck

CurlyBlue

---

### Post by CurlyBlue on 2006-09-03
PS

Cant wait for the day when I click the word UNINSTALL on my windows box!

CurlyBlue

---

### Post by apiper on 2006-09-03
> **Aristotle3 said:**
> I'm connected to the internet, and it downloads stuff when I installed the desktop, and I tried sudo dpkg-reconfigure xserver-xorg.  It goes through a lot of stuff, and then stops.  

"sudo /etc/init.d/gdm start" gives "command not found".  startx gives snow.

I have a standard, unaltered gateway2000 desktop with a NVidia MX2 400, 512 ram, 1.8GHz Intel CPU, intel MOBO...should work.  I ran Suse 10.1 on it for a while and it worked fine.  I left SUSE 10.1 because the support forums were much less active than those on ubuntu.

So a server install fails to give a GUI, and a desktop install fails to go past the word "GRUB" (GRUB seems empty).  I did the same reformat of the second partition with both the server and desktop installs, and used the exact same settings on the partition manager (OSX on 1st partition, clarkconnect on the 3rd, and ubuntu on the 2nd).  

Ironically, OSX is the most stable install on any of my machines, and its on an old Gateway2000.  I wonder if it can be used as a SAMBA/FTP server.

When you get the "command not found" message when trying to start gdm, what is the name of the command that's not found? If the message is

[INDENT][FONT="Courier New"]sudo: /etc/init.d/gdm: command not found[/FONT][/INDENT]

Then gdm isn't installed. To install it:

[INDENT][FONT="Courier New"]sudo apt-get install gdm[/FONT][/INDENT]

And then try starting gdm again. Let us know how it goes...

---

### Post by az on 2006-09-03
> **Aristotle3 said:**
> I'm connected to the internet, and it downloads stuff when I installed the desktop, and I tried sudo dpkg-reconfigure xserver-xorg.  It goes through a lot of stuff, and then stops.  

"sudo /etc/init.d/gdm start" gives "command not found".  startx gives snow.


If the command is not found, ubuntu-desktop is not properly installed.  Try to fix broken packages with

sudo apt-get -f install

---

