---
title: "How secure is ubuntu"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by uraliss on 2006-06-22
Hi folks
I have spent a few days playing with ubuntu on my laptop and i'm very impressed with it - i don't think I will be going back to XP in any case.
One question though... how secure is ubuntu? Can I be confident in storing personal documents on my laptop without fear of the system getting hacked into if my laptop gets stolen?

---

### Post by aysiu on 2006-06-22
If your laptop gets stolen and the thief knows what she's doing, your data is compromised if it's not encrypted.

---

### Post by Brunellus on 2006-06-22
if somone has physical access to your computer, you're pretty much shafted, no matter what OS you're using.

Your first line of defense is to keep your computer from being stolen.  Then, a proper, strong password.  a BIOS bootup password might also work, but don't forget this, as it will render the machine totally unbootable if you can't remember the password.

There might even be the option of encrypting one or more partitions, but I've never had to do this myself.

---

### Post by jrattner on 2006-06-22
Ubuntu by default is FAR more secure then windows will ever be.  You should take a look at tutrotials about hardening linux, and or encrypting file systems if your very paranoid.  

Honestly though, considering you just migrated from Windows I believe that the default settings will be more then enough security for you.

---

### Post by Brunellus on 2006-06-22
"hardening" Linux tends to focus more on remote attacks.  

It just occurred to me that making your Ubuntu as un-Windows-like as possible would probably cause the thief to freak out.  Nontechies flee at the sight of a command line.  Even Fluxbox scares them.

---

### Post by aysiu on 2006-06-22
[QUOTE=jrattner]Ubuntu by default is FAR more secure then windows will ever be.  You should take a look at tutrotials about hardening linux, and or encrypting file systems if your very paranoid.  

Honestly though, considering you just migrated from Windows I believe that the default settings will be more then enough security for you.[/QUOTE]
We're talking about a physically stolen laptop, though, right?

---

### Post by Solver on 2006-06-22
One of the basic rules of security is that, if someone has physical access to your computer, and enough time, you're screwed. Basically, if a laptop is stolen, the thief may have access to all your data within some 5 minutes, unless the file system is encrypted.

The question is, what kind of a situation are you facing? If you have some highly sensitive data on your computer, then you might want to look into filesystem encryption. For a random thief who steals the laptop, though, it might be possible that the thief would freak out and not know what to do in the first place.

A good option is to password-protect separate sensitive files. Or, if they can't be protected by themselves (such as plaintext files), you can store them in password-protected archives.

---

### Post by nalmeth on 2006-06-22
Someone with enough expertise and intention could easily get your documents, but for a random thief who jacked your laptop, a BIOS password would probably stop them dead in their tracks. Set the laptop to boot ONLY to harddrive, remove floppy/usb/cdrom booting in BIOS.

Encryption might be a good idea, you could create a seperate data partition and leave it unmounted on boot-up, encrypted.

---

### Post by joe_lace on 2006-06-22
Most people who steal your laptop just want to reformat it and resell it anyway.  If someone really wants your data encryption is the only way.  Bios passwords can be reset without too much difficulty if I'm not mistaken.

---

### Post by Brunellus on 2006-06-22
[QUOTE=joe_lace]Most people who steal your laptop just want to reformat it and resell it anyway.  If someone really wants your data encryption is the only way.  Bios passwords can be reset without too much difficulty if I'm not mistaken.[/QUOTE]
usually requires opening the case & changing a battery as I recall.  I do know, though, that used laptops with BIOS passwords sell at a tremendous discount on the market, because doing this is a pain in the ***

---

### Post by Solver on 2006-06-22
Resetting a BIOS password still takes some knowledge. Again, potential thieves are most likely in one of the two categories. First category, the technically clueless ones. If so, a BIOS password will stop them. Second category, the tech-savvy - and nothing except encryption will prevent them from getting your data.

I wonder if there are any Ubuntu utilities that could be used to encrypt separate files. Encrypting a whole filesystem is a bit of a pain, but making folders or files encrypted could sure be handy.

---

### Post by tbunreal on 2006-06-24
well i was watching call for help and marcel gagne was on and he was talking about how safe linux was but every linux user should have a firewall. most distro's come with one. ubuntu doesnt however.. he recomended this firewall, its  very easy to use. 

[read this and  link at bottum of page is where you get firestarter the firewall]("http://www.callforhelptv.com/callforhelp/shownotes/0326.shtml?guests")

---

### Post by tbunreal on 2006-06-24
i think this firewall should be stickied  cuz it is a security threat

---

### Post by falcon15500 on 2006-06-24
[QUOTE=tbunreal]well i was watching call for help and marcel gagne was on and he was talking about how safe linux was but every linux user should have a firewall. most distro's come with one. ubuntu doesnt however.. he recomended this firewall, its  very easy to use. [/QUOTE]

  This isn't quite true... Ubuntu comes with iptables by default, which is a great firewall.  It generally isn't preconfigured, as I guess that's what most users want.  Understand that firestarter isn't a firewall by itself, it is a configuration tool for iptables.

falc

---

### Post by az on 2006-06-24
[QUOTE=tbunreal]i think this firewall should be stickied  cuz it is a security threat[/QUOTE]
If you run an OS that doesn't allow you to know what your computer is doing, you may need to use a firewall to keep tabs of what you box is saying to others.  Since this is open source software, it is highly unlikely that anything in the repos would phone home without your permission.

There is no need for a firewall to be installed by default.

---

### Post by lotusleaf on 2006-06-24
One could always install and setup [Bastille](http://www.bastille-linux.org/), as one of many tools available.

["This page provides a preview of Bastille's Reporting / Audit functionality."](http://www.bastille-linux.org/Reporting/)

---

### Post by nealklomp on 2006-06-25
Any linux distro is about 100s or times more secure than Windows. 
Why? 
90%+ of comps run windows, so nearly all hackers focus on that OS, the rest think of Mac or Appache servers, not each of the 100s of Linux distros. 
Linux is configured for multiple users with specified access, thus no loopholes for hackers to exploit.
Linux alway requires a password to do anything, unlike windows which constantly does things without asking or even explaining; with XP my box's hard drive would just go off, for no reason, no explanation, this never happens with linux, ever.
You can be hacked, unless you harden the system up, then I would doubt it.

A standard Linux install, is at least 10 times more secure than a Norton or Mcaffee protect PC.

as for laptop being stolen, well... what ya going to do?

---

### Post by MaximB on 2006-06-25
I know that for windows users you have a bootcd that you can reset the password without knowing it.
what about linux users ? does it have aboot cd like this one ? that could reset your password ?

---

### Post by tbunreal on 2006-06-25
well, im a newbie so when i tried to do anything as root i got wrong password, but ubuntu has it disabled :P . so while i was looking for ways to get root password back there are many ways, but you need phsycal access to the computer.

---

### Post by wombat20 on 2006-06-25
[QUOTE=MAXDDARK]I know that for windows users you have a bootcd that you can reset the password without knowing it.
what about linux users ? does it have aboot cd like this one ? that could reset your password ?[/QUOTE]

I think booting from the install/live CD allows you to do this.  That's why you should always set a BIOS password and change the BIOS to boot ONLY from HD.

---

### Post by MaximB on 2006-06-25
what we have come to know that is if your computer get stolen - there is nothing you can do to stop them from stealing you data..
the BIOS won't help heather - there is a small chip that resets it...
and after that bootcd...
not very hard.

---

### Post by Born_Again on 2006-06-25
I've got Dapper set up on my laptop and just a assumed the root pwd was set to match that of the main account by default.

Howver, I got a bit of a rude shock the other day when I had to boot into the recovery mode and realised I was automatically logged directly into the root account without being prompted for a pwd.

~$sudo passwd root

---

### Post by raptros-v76 on 2006-06-25
well, the answer to getting your computer stolen is not letting it get stolen. most laptops these days have a little thing on the side for a locking cable, which are like 10 (us) bucks apiece.  and those are nearly impossible to break.

---

### Post by az on 2006-06-25
[QUOTE=Born_Again]I've got Dapper set up on my laptop and just a assumed the root pwd was set to match that of the main account by default.

Howver, I got a bit of a rude shock the other day when I had to boot into the recovery mode and realised I was automatically logged directly into the root account without being prompted for a pwd.

~$sudo passwd root[/QUOTE]
Yes.  That's the point about getting your laptop (or desktop) stolen - if you have physical access, you can be root.

However, can you become root remotely?  That's what we are talking about when we talk about security.

---

