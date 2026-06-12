---
title: "Juno Internet Access"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by Harold P on 2005-09-21
Hello everyone,

I just received the Ubuntu DVD's in the mail today, and I was wondering, where can I get Juno software compatible with Linux? Or does the start-up CD come with a Linux installation.


If you need to contact me, please email me at [email]fowlance@gmail.com[/email]

Thanks in advance,

hp

---

### Post by KingBahamut on 2005-09-21
[http://www.juno.com/support/faq/fgtg04.html](http://www.juno.com/support/faq/fgtg04.html)

Appears for all intents and purposes that Linspire is supported. 

However, I assume that you can get the direct dial info from Juno , or any of its affailiates such as Netzero and Blue light (United Online is the actual company).

---

### Post by Harold P on 2005-09-21
As you can tell, I am completely new to Linux, what is Linspire?

Also, the support page directed me towards some page to select my icon. 


All I need to know basically, is if the CD I was provided with has the Linux installation for Juno internet access.

Thanks,

hp


Edit: You do not have to answer immediately, for I live in Houston, and I am evacuating to get away from Rita. I will be on later tomorrow when I set up my computer there.

---

### Post by Workinman57 on 2007-02-15
No the Ubuntu CD doesn't have a Juno install you need to get the Linspire Juno.deb from juno at

[http://my.juno.com/s/download](http://my.juno.com/s/download)

Install it with the debian package installer whitch you can get from the package installer in ubuntu.
you also need java it is a 3rd party app and can be install via add and remove programs

must be run as root. to connect unless you can change permissions.

---

### Post by Workinman57 on 2007-02-25
Update: Juno CD also does not have Juno.deb  :>(

---

### Post by psyguy92 on 2007-05-16
> **KingBahamut said:**
> [http://www.juno.com/support/faq/fgtg04.html](http://www.juno.com/support/faq/fgtg04.html)

Appears for all intents and purposes that Linspire is supported. 

However, I assume that you can get the direct dial info from Juno , or any of its affailiates such as Netzero and Blue light (United Online is the actual company).

Hey guys/gals. I realize this thread is old, but thought I'd add my two cents that I have found out. 
A friend has/had Juno (same as netzero) and I tried to get dialup juno access working on his new feisty installation, with no luck.  KingBahamut's assumption about direct dial info from Juno isn't right.  

What I have found out:
1. Juno DOES have a .deb file available, tailored for Linspire, that you can download, but you may need to be logged in as a paying customer first. (I ended up finding it by the google query *site:juno.com linux*)
2. The .deb file installs with no problem, but puts what I assume to be the connect launcher on the desktop of root.  This file is also owned by root. 
(note: I couldn't change the owner of the file; sudo chown said not permitted).  
3. Creating a real root account and enabling gnome login (I know, a bad Idea, but I was testing) allowed me to login to root with gnome, but I couldn't get the launcher to do anything. Looking at the command invoked by the launcher and issuing the command in a terminal as root gave a cryptic message and got nowhere.
4. You are able, using gnome-ppp, to get a valid internet connection using your id/pass/phonenumber from Juno, HOWEVER, it will redirect any browsing activity to a juno/netzero page stating that the account is limited/blocked/restricted.  It would seem that Juno wants you to use their program to connect, and if you try to make a direct connection without their program, you cannot go to any webpages. *grr*

In summary, Juno does not play nicely with Ubuntu. It may be possible to get their .deb file to work, but I couldn't find any documentation from Juno or anywhere else to do this (maybe linspire's site?). Connecting directly did not work. Note: I had the same restricted access error trying to do a direct connect with Juno (not using their software) under WinXP.

What I did to fix the problem:
1. Downloaded gnome-ppp ([http://packages.ubuntu.com/feisty/net/gnome-ppp]("http://packages.ubuntu.com/feisty/net/gnome-ppp")) using another computer that had net access.
2. Got an account at [http://www.basicisp.net]("http://www.basicisp.net") ($6.95/month)
3. Entered the correct info in gnome-ppp, connected with no problems, and promptly canceled Juno's service :)

Caveat: I purposely got a PCI full hardware modem from eBay so that there would be no winmodem issues. If you don't have a hardware modem, you will need to do some further searching for that.

Just hoping this info helps someone out and saves a couple of hours messing with it, like I did.

Cheers!

---

### Post by Bartender on 2007-05-22
My experience with Juno closely parallels psyguy's.  We're using the old Juno 5 software, not Juno 6.  When I log in to the Juno download site there is no Linspire download, so maybe that's for Juno 6?
Anyway, I can dial Juno with KPPP and an external USR serial modem, but I promptly get dumped to a Juno page saying my account has been blocked or restricted.  I'm connected to the web but all I can do from there is go to help pages and/or write a Support ticket.  

Then I go back to Windows and my Juno account works fine.  A day or so later I get a response to the Support Ticket.  The response goes like this - "We don't support Linux."  No kidding.

Sooner or later I'll be doing what psyguy suggests - drop Juno for an ISP that doesn't force you to use their proprietary software.

---

### Post by Workinman57 on 2007-07-04
[http://my.juno.com/s/download?cf=acctindex](http://my.juno.com/s/download?cf=acctindex) is the linspire download location. Note you must have a Juno account to log in to this site. The standard Juno Netzero download area doesnt have the .deb for linspire. I am at the site now to re download to this Inspiron 8200 I am working on :p

---

### Post by kevinmedina on 2007-07-28
I too have had precisely the same problem with Juno.  They made it clear in an email response to me that you can only log on to the Juno servers using their proprietary software.  I'm going to migrate to basicisp now too, and save me another few dollars :-)

Thanks for the tip!

---

### Post by Bartender on 2007-07-29
I wish I knew the lowdown on this "Linspire dialer".  I log in to the Juno website as a Juno 5 user, and the alleged Linspire dialer is nowhere to be found.  
There might be some tweaking on the Linspire dialer (if one could just get ahold of it) to make it functional on anything but Linspire.
Unless someone can tell me different I'm of the opinion that switching to a different ISP is probably the final solution to the Juno problem.

---

### Post by armandh on 2007-07-29
I suppose linux is not supported because one could block the ads

---

