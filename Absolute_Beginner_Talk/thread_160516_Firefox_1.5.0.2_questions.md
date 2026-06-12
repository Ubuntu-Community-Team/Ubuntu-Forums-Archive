---
title: "Firefox 1.5.0.2 questions"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by BarFly on 2006-04-15
Okay, when I was using Windows, I never waited for the auto update for a new version of ff.  I decided I would wait this time using Ubuntu.  It never updated.  Is that because 5.1 comes with 1.07?  Then I went to manually get the update under "Help," only to find "Check for Updates..." is greyed out!  WTF?  Why is that?

On another thread, I found that you can type this into the terminal:
> gksudo firefox
That allows you to check for updates, but when you restart, you still cannot check for updates.

Now I have the current version of Firefox, but I am still puzzled why on Earth "Check for Updates..." is greyed out.  Is there something I can do to rectify this?  If it matters, I installed 1.5 using the Automatix script.

This is not a real problem, as I found an easy work-around, but I am curious and trying to learn this strange OS.

---

### Post by jason.b.c on 2006-04-15
[QUOTE=BarFly]Okay, when I was using Windows, I never waited for the auto update for a new version of ff.  I decided I would wait this time using Ubuntu.  It never updated.  Is that because 5.1 comes with 1.07?  Then I went to manually get the update under "Help," only to find "Check for Updates..." is greyed out!  WTF?  Why is that?

On another thread, I found that you can type this into the terminal:

That allows you to check for updates, but when you restart, you still cannot check for updates.

Now I have the current version of Firefox, but I am still puzzled why on Earth "Check for Updates..." is greyed out.  Is there something I can do to rectify this?  If it matters, I installed 1.5 using the Automatix script.

This is not a real problem, as I found an easy work-around, but I am curious and trying to learn this strange OS.[/QUOTE]


I don't know, thats a really good question you have there.   I've wondered that one myself .!    " Why in the hell is firefox so differant in linux?????? " :confused: ](*,) 

I dun know.?:confused:

---

### Post by brainfry on 2006-04-15
Hi people
don't know if this helps but I don't use the version of FF that comes with Ubuntu, instead I download it from the Mozilla website and it updated itself a couple of days ago.

---

### Post by akudewan on 2006-04-15
[QUOTE=brainfry]Hi people
don't know if this helps but I don't use the version of FF that comes with Ubuntu, instead I download it from the Mozilla website and it updated itself a couple of days ago.[/QUOTE]

Same here. Just use the method to install firefox 1.5 in the HOWTO forum. It tells you to install firefox in the /opt directory, and it gives write access to the directory, so you can install for updates.

---

### Post by darrenrxm on 2006-04-15
sudo firefox 

and then goto help and update in firefox itself.

Works perfectly with firefox automatix version.

And I can't tell the difference between the windows version and linux version. Unless you go to certain websites. mtv.ca for example, then you realize that you are not running windows. That is as long as you use the cntl + L shortcut for focus in the address bar in both windows and linux.

---

### Post by BarFly on 2006-04-15
Yeah, darrenrxm, I did gksudo firefox and it worked swimmingly as stated above.

akudewan, I had FF 1.5.0.1.  I wanted to update from .1 to .2.  I don't understand what you want me to do so that the check for updates option is not greyed out.  I have FF in the opt directory.  Forgive me if I am slow, but this is the absolute beginners section.

---

### Post by akudewan on 2006-04-15
[QUOTE=BarFly]Yeah, darrenrxm, I did gksudo firefox and it worked swimmingly as stated above.

akudewan, I had FF 1.5.0.1.  I wanted to update from .1 to .2.  I don't understand what you want me to do so that the check for updates option is not greyed out.  I have FF in the opt directory.  Forgive me if I am slow, but this is the absolute beginners section.[/QUOTE]

Well, to be honest, I'm not sure myself why the option is grayed out, while it works fine for me.

The only reason I can think of is that you don't have _write access_ the to your /opt/firefox (or similar) directory.

To make sure you have write access, you can use this command:
```

chmod -R a+rwx /opt/firefox

```

(Use the command with sudo if it says "permission denied").

Lets hope it works.

---

### Post by darrenrxm on 2006-04-15
If you have guest account in windows xp the firefox update will also be greyed out. But if you are using a administrator account it will not be. 

Hope this helps.

---

### Post by OffHand on 2006-04-15
Make sure you set the permissions back after upgrading with gksudo firefox.
Check this thread: [http://ubuntuforums.org/showthread.php?t=160128](http://ubuntuforums.org/showthread.php?t=160128)

Check if it is owned by the root with ```
ls -l /opt/firefox
```

---

### Post by siminone on 2006-04-15
The reason why updates in Linux Firefox is greyed out is because the system files are set to 'read only access' and therefore unable to be updated.

This is a wise precaution as these files can not be corrupted with viruses or rootkits by online hackers. 

Maybe I am being paranoid but by typing gksudo firefox is unsafe as firefox is being run by 'root' and could by used as a backdoor by hackers to gain entry to the system. 

I'm no expert on security issues but I always play safe it safe and download firefox from their site and install.

---

### Post by steve.horsley on 2006-04-15
[QUOTE=siminone]The reason why updates in Linux Firefox is greyed out is because the system files are set to 'read only access' and therefore unable to be updated.

This is a wise precaution as these files can not be corrupted with viruses or rootkits by online hackers. 
[/QUOTE]
Absolutely right.
> 
Maybe I am being paranoid but by typing gksudo firefox is unsafe as firefox is being run by 'root' and could by used as a backdoor by hackers to gain entry to the system. 

I'm no expert on security issues but I always play safe it safe and download firefox from their site and install.
I think that is perhaps being a little over-paranoid. Provided all you do is the update while root, and you don't visit all those dodgy sites, you should be OK. Just quit the root browser as soon as possible.

EDIT: I'll leave the paragraph below in, bit it is WRONG! I tried it, and gksudo does set the home directory properly.

However, I am unhappy with the idea of doing gksudo firefox because I don't think it corrects the HOME environment variable, which means that the root firefox might write to the user's firefox settings, rendering them un-writeable by the user any more.

---

### Post by BarFly on 2006-04-15
Ok, that makes sense!  Thanks to all for clearing this up for me.  I don't see why you cannot check for updates without installing, though.  Installing a new version could just ask for the root password.  To me, that seems like the most intuitive route that does not compromise security, but I am new to Linux.

If you take the paranoid route by downloading FF from Mozilla for updates, does that mess with your FF profile?  I assume not.  Just curious.  I will continue to use gksudo firefox as it is easier and not much of a security risk.

---

### Post by OffHand on 2006-04-15
[QUOTE=BarFly]
If you take the paranoid route by downloading FF from Mozilla for updates, does that mess with your FF profile?  I assume not.  Just curious.  I will continue to use gksudo firefox as it is easier and not much of a security risk.[/QUOTE]
I used gksudo and still have all my bookmarks, settings and extensions.

---

### Post by Unicast on 2006-04-15
Thank you very much for the "sudo firefox" update method. You learn something new everyday with Ubuntu! :-D

---

### Post by NoWhereMan on 2006-04-15
an image is worth a thousand words :)
ubuntu dapper

[[IMG]http://img114.imageshack.us/img114/6208/sshot5ih.th.png[/IMG]](http://img114.imageshack.us/my.php?image=sshot5ih.png)

---

### Post by steve.horsley on 2006-04-15
[QUOTE=Unicast]Thank you very much for the "sudo firefox" update method. You learn something new everyday with Ubuntu! :-D[/QUOTE]

No. Sudo firefox does NOT set the home directory properly. gksudo firefox does, though.

---

### Post by joshrobinson on 2006-04-15
i just tried sudo firefox, gksudo firefox and even logged in as root

my firefox isnt installed in the /opt/firefox directory so i couldnt use the chmod command
so i found it in /usr/lib/firefox and did the chmod on that DIR
but update is still blacked out.. should i uninstall firefox and manually install it?


edit: ok i got it

i deleted /usr/lib/firefox
downloaded the source from getfirefox.com and put it where the old folder was.. all bookmarks still intact

---

### Post by Sef on 2006-04-15
> deleted /usr/lib/firefox
downloaded the source from getfirefox.com and put it where the old folder was.. all bookmarks still intact

Could you give some instructions on how you deleted the directory and then installed firefox. Thank you.

---

### Post by darrenrxm on 2006-04-15
> No. Sudo firefox does NOT set the home directory properly. gksudo firefox does, though.

I don't understand what is wrong with doing it with this method. My firefox seems to be working perfectly. Could you please expand on what you posted about? 

And thank god we won't have these problems when dapper drake comes out.

---

### Post by towsonu2003 on 2006-04-15
Anyone updating firefox should check out the wiki page on how to do it "properly". The wiki page had three options to update at one point, and those options were eliminated to only one after we had problems with one or the other option. right now, the proper way to do it seems to be changing permissions of /opt/firefox **temporarily**. It is easy (use chown twice) and less risky (running firefox as root is risky: firefox shouldn't have root privileges at any time, a small bug in it can easily screw your system). 

to check if your (and mine, because I used it accidentally as well ;) ) sudo/gksudo firefox way of updating worked (or screwed your profile), do
```
chown -R username:username ~/.mozilla/firefox
```
notice there is no "sudo" use. if this outputs errors (example: you do not have permissions to blabla), than your profile isn't good to go. fix it with
```
sudo chown -R username:username ~/.mozilla/firefox
```

using sudo firefox (and most probably gksudo firefox) launches firefox as root being the launcher of firefox, while firefox is still using your profile. This, to me, is most probably a bug or confusion. The logical way would be firefox creating a profile under /root/.mozilla/firefox (/root is the home of root). But you can't really file a bug report either ;) Anyway, when you launch firefox as root, if firefox changes any files (it does), they got owned by root instead of you.

---

### Post by 5-HT on 2006-04-15
[quote= towsonu2003]...Using sudo firefox (and most probably gksudo firefox) launches firefox as root being the launcher of firefox, while firefox is still using your profile. This, to me, is most probably a bug or confusion. The logical way would be firefox creating a profile under /root/.mozilla/firefox (/root is the home of root)...[/quote]

Hey, not sure if I know what I'm talking about here, but for me, firefox uses a root profile (/root/.mozilla/...) when launched using gksudo. 

When launched with sudo, it does use my user profile (and can therfore cause some issues when updating), but I've never had that problem with gksudo.

---

### Post by towsonu2003 on 2006-04-15
[QUOTE=5-HT]Hey, not sure if I know what I'm talking about here[/quote]not sure if I know what I'm talking about here either
[QUOTE=5-HT]
When launched with sudo, it does use my user profile (and can therfore cause some issues when updating), but I've never had that problem with gksudo.[/QUOTE]
I guess that means gksudo isn't just a gui frontend to sudo... time for me to read the man page :PpP

edit: just read man page, and it says it's a frontend to sudo (?which means there should be no difference between them?). --> is this a bug or a feature? :confused:

---

### Post by 5-HT on 2006-04-15
[quote= towsonu2003]
edit: just read man page, and it says it's a frontend to sudo (?which means there should be no difference between them?). --> is this a bug or a feature? :confused:[/quote] 
From the sudo man page, sudo does not modify the HOME env variable by default (can be done though).

I'm grasping for straws here, but maybe gksudo is setting HOME to /root? :confused:

---

### Post by Angry penguin on 2006-04-15
I have version 1.0.7, when I go to help in Firefox, there is no "update" option. 

I followed the sudo options posted earlier in this thread but all that did was open up a new window of firefox....

How do I install version 1.5 I downloaded it and there is no configuration or makefile.

---

### Post by towsonu2003 on 2006-04-16
[QUOTE=Angry penguin]I have version 1.0.7, when I go to help in Firefox, there is no "update" option. 

I followed the sudo options posted earlier in this thread but all that did was open up a new window of firefox....

How do I install version 1.5 I downloaded it and there is no configuration or makefile.[/QUOTE]
I'm confused. You seem to be using Dapper (says so left to your post). Dapper has 1.5 and self-updates thru synaptic. 

Anyway, check wiki.ubuntu.com/FirefoxNewVersion on how to get firefox 1.5(.0.2). It has instructions on how to update firefoxes from 1.5.0 on there as well.

---

### Post by siminone on 2006-04-16
[QUOTE=steve.horsley]

I think that is perhaps being a little over-paranoid. Provided all you do is the update while root, and you don't visit all those dodgy sites, you should be OK. Just quit the root browser as soon as possible.
[/QUOTE]

Thanks Steve for the reply. I am paranoid when it comes to being online. It has to be remembered though that these fixes for Firefox are for vulnerabilities in the code that can be exploited. This would be disastrous if Firefox was run by root and these were exploited and besides no amount of software is 100% bug free.

Given the increasing sophistication of hackers and interest that organised crime has in cyberspace especially the Russian Mafia, it is unknown what type of tools they have. I'd rather be safe than sorry :-D 

[http://it.slashdot.org/article.pl?sid=06/04/10/1451201](http://it.slashdot.org/article.pl?sid=06/04/10/1451201)

---

### Post by OffHand on 2006-04-16
[QUOTE=siminone]Thanks Steve for the reply. I am paranoid when it comes to being online. It has to be remembered though that these fixes for Firefox are for vulnerabilities in the code that can be exploited. This would be disastrous if Firefox was run by root and these were exploited and besides no amount of software is 100% bug free.

Given the increasing sophistication of hackers and interest that organised crime has in cyberspace especially the Russian Mafia, it is unknown what type of tools they have. I'd rather be safe than sorry :-D 

[http://it.slashdot.org/article.pl?sid=06/04/10/1451201](http://it.slashdot.org/article.pl?sid=06/04/10/1451201)[/QUOTE]If you do gksudo firefox, update and close firefox again the chances you are getting hacked are very very small. If you keep browsing in gksudo mode it will be a different story.

---

### Post by siminone on 2006-04-17
[QUOTE=subsonic_shadow]If you do gksudo firefox, update and close firefox again the chances you are getting hacked are very very small. If you keep browsing in gksudo mode it will be a different story.[/QUOTE]

Agreed.

---

