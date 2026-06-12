---
title: "Auto Running Firestarter on Startup"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by Omnios on 2006-05-10
The firestarter help file for auto starting firestarter --minimized is on the faq section. I thought is do a little how to for gnome. I do not have KDE installed this release so if someone want to clarify how to do in in KDE go right ahead.

 Anyways the link to the faq is here.
[[COLOR="Blue"]Firestarter Frequently asked questions/[/COLOR]]("http://www.fs-security.com/docs/faq.php#trayicon")

 Anyways to get started the faq is pretty self explanitory and this set up allows for FIrestarter to auto start on boot up without inputting the password.

 First you need to mod the /etc/sudoers file by typing 
```
sudo gedit /etc/sudoers
```
sudo does it as root, gedit launches the text editor in root with the sudo command. /etc/sudoers is the file you are launching in the gedit text editor.

 Now in the text editor add the following line to the bottom.
```
username ALL= NOPASSWD: /usr/sbin/firestarter
```
for User name use your user name, the name you log in with. Dont forget to save and exit.

 [QUOTE][Note: Debian users should replace /usr/bin/firestarter with /usr/sbin/firestarter in the above line./QUOTE] "which we did above."

 Now for the start up.
First open sessions.
[IMG]http://ubuntuforums.org/gallery/files/1/4/1/2/6/firestarter.jpg[/IMG]

 Now you want to click start up programs.
[IMG]http://www.fs-security.com/docs/pics/sessions-small.png[/IMG]

click add and add the following to start up
[QUOTE][sudo firestarter --start-hidden/QUOTE]
click ok and your all set.

 Now there are a few notes about auto starting firestarter. If you save your current set up with firestarter runnign it will try to run two instances of firestarter on start up. The way to solve this is close firestarter then exit saving your current set up. This will but it back to the way it should be.

---

### Post by louis_nichols on 2006-05-10
nice howto! you should also specify, though, that firewall rules are active even when firestarter is not... well, started.

---

### Post by adssse on 2006-05-10
I just installed firestarter without doing anything extra. After restarting I typed
"sudo /etc/init.d/firestarter status"
and it tells me that it is running.
"Firestarter is running..."
Am I correct in assuming that it loads firestarter, but just doesnt load the gui?

---

### Post by louis_nichols on 2006-05-10
[QUOTE=adssse]I just installed firestarter without doing anything extra. After restarting I typed
"sudo /etc/init.d/firestarter status"
and it tells me that it is running.
"Firestarter is running..."
Am I correct in assuming that it loads firestarter, but just doesnt load the gui?[/QUOTE]

Yes, that is correct. Firestarter is always there, and the GUI is only for changing firewall settings.

In fact, Firestarter is not even the firewall. This is included in the Linux kernel and is called iptables. It's very powerful, and firestarter only gives access to a small percentage of its capabilities (you don't need more, as a desktop pc user - the rest is for advanced networking, servers etc). For more info, read [this]("https://wiki.ubuntu.com/IptablesHowTo"). So you can use it without having firestarter installed, if you want.

---

### Post by adssse on 2006-05-10
Thanks for clearing that up. Even though I had knew that iptables existed I always thought that firestarter was a firewall in its own right. Glad I know whats really going on now.

---

### Post by Sam Lars on 2006-06-27
Thanks for the info!  I think all I really needed was the command to start it, but I'm glad I know about sudoers now, too.

---

### Post by gbinal on 2006-07-19
> **Omnios said:**
> 

 First you need to mod the /etc/sudoers file by typing 
```
sudo gedit /etc/sudoers
```
sudo does it as root, gedit launches the text editor in root with the sudo command. /etc/sudoers is the file you are launching in the gedit text editor.


Thanks a bunch for putting this oiut there.  The only problem I had was being told that sudoers was on a read-only part of the disk and that I couldn't save the file.  I believe I just made it work by using visudo instead.  I entered

> sudo visudo

instead of using text editor.  Hopefully, that will work on reboot.  Peace

---

### Post by redicqlus on 2006-07-29
> **gbinal said:**
> Thanks a bunch for putting this oiut there.  The only problem I had was being told that sudoers was on a read-only part of the disk and that I couldn't save the file.  I believe I just made it work by using visudo instead.  I entered



instead of using text editor.  Hopefully, that will work on reboot.  Peace



Hi guys, and thanks for looking at this message.   Seems I've run into a bit of a snag trying to implement the run on startup protocal for firestarter.  I used visudo and made the edits, and went to  System -> Prefrences -> Sessions ->Startup Programs, and typed what was asked.  I also made sure I had stopped my current session of firestarter before saving.   

When I restarted, firestarter was running in the background > redgobuty@redgobuty-laptop:~$ sudo /etc/init.d/firestarter status
Password:
 * Firestarter is running...

But there was no nifty minimized icon for the program telling me the status or when things were being hit.  My screenshot didn't show any firestarter program. [ATTACH]13399[/ATTACH]

I even went back to sessions and tried again with just sudo firestarter (without --start-hidden) and still I couldn't see the icon.

I am curious if my current sessions has anything to do with the problem (if this is one) because it gives me a "?" for the state of firestarter.   [ATTACH]13400[/ATTACH]

Moreover, when I go to Applications->Internet->Firestarter now, it doesn't come up at all in GUI form.

I know the program is running, but I'd like to see the graphical representation of when I'm getting hit.  If I get rid of the sudoers line I created, then I can open up firestarter with Applications->Internet->Firestarter (but I have to enter my password) and then I have the GUI working.  So it's probably something to do with sudoers.   Maybe it's /usr/bin and not /usr/sbin????

-red-

---

### Post by awilki01 on 2008-06-07
Wonderful!  I edit my sudoers file and now I get this when trying to redit it:

```

adam@adam-ubuntu:~$ sudo visudo -f /etc/sudoers
>>> sudoers file: syntax error, line 24 <<<
sudo: parse error in /etc/sudoers near line 24


```

Edit: I fixed it by rebooting and choosing the recovery option in the GRUB menu.  I then did the "visudo /etc/sudoers" to take out what I did.  I rebooted and now all is good.


Edit 2:  Ok, after my aforementioned woes, I was able to configure everything as indicated in the how-to.  However, it is not working for me.  a 'ps -ef | grep firestarter' indicates no firestarter process is running.  Also quite odd is that after doing all this, I cannot launch firestarter from command line.  It states it cannot connect to the XServer.  After I take the line out of the sudoers file, I am able to execute it once more.  Any suggestions?

---

