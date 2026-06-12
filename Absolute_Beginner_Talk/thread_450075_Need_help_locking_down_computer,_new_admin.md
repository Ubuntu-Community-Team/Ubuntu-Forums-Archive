---
title: "Need help locking down computer, new admin"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Funk Phenomena on 2007-05-20
Hello, I am a new 'admin' for a computer I put in the employee breakroom to help others learn about how to use a computer.  Ubuntu is new to me.  I originally put it as a dual boot with Windows ME.  Some clown decided to erase everything they could in ME.  No biggy, I didn't like ME anyway.  I reinstalled Ubuntu to get rid of the dual-boot screen... and because I couldn't figure out how to merge the old ME partition.

Long story short, I've created a limited user account and would like any other pointers how I can keep the clown from doing more damage. Currently I have the user account restricted to floppy, cd drive and audio permissions.  I just read in another thread to change the permissions of the admin home folder.  I think I created a password for root... is it safe to get rid of root?  The computer does not have internet access.

I tried deciphering the syslog... yeah,  lol, I can't translate what it's telling me.  A keylogger seems a bit extreme... is there some way to track if a clown probes around?  All I need is the timestamp, there are about 15 people that could get on the computer 24/7 so that should help me narrow it down.  I'm not looking to lynch anyone, but geez, I'd like this computer to be a good educational tool for others.  

I've never been in this position where I've had to be an 'admin' for others.  Any help would be appreciated.

---

### Post by starcraft.man on 2007-05-20
Ummm... no, you don't want to get rid of root, you can't really. You need root to administrate the PC. Since you limited their user accounts, they can't do anything on the machine really. Do make sure your root password is around 12-15 characters and random in nature (mine is 15 with caps, lowercase, numbers and 3 punctuation).

As for tracking them, I dunno. I don't really see how they could do any harm without having admin powers... worse they can do is delete a file in their home folder or change preferences >.>. Then you can just make a new account..... 

I wouldn't be too worried anyway, if they don't know much about Ubuntu/Linux I assume they will be somewhat puzzled :p

If you wanna be really mean... get a Vista/XP skin/theme and make it only one panel on the bottom, Then watch em squirm :p

---

### Post by irish_flu on 2007-05-20
YEah, I'd leave root alone (just make sure that you're the only one with the root password).  They won't be able to change anything horribly without an administrative password.

---

### Post by starcraft.man on 2007-05-20
> **irish_flu said:**
> YEah, I'd leave root alone (just make sure that you're the only one with the root password).  They won't be able to change anything horribly without an administrative password.

I can just imagine the shock of them going from default administrator account in windows ME to neutered can't do jack account in Ubuntu :p

Oh and Funk, don't worry, being admin isn't hard, and feel free to mess with their public account every once and a while its fun (yes, I am somewhat cruel but only humorously so) :D

---

### Post by esoterica on 2007-05-20
Your best bet is to just pull the hard drive out of the computer and let Ubuntu run by booting and running off the CD, then no matter what someone does to it a simple reboot will put everything right back to where it was every single time. 

This also makes for a 100% guaranteed hacker and virus proof even dumb user proof system.

There are also other options that are well documented you could look into, but none are better than just running off a read only CD.

Try searching Google for "Running Linux as a Kiosk"

---

### Post by jiminycricket on 2007-05-20
/var/syslog or System->Administration->System Logs should have logs of attempted logins and privelege escalations and such.

Remove the user from /etc/sudoers using visudo so they can't use sudo to escalate privs, or if using su, remove them from the wheel group.

[Sabayon]("http://www.gnome.org/projects/sabayon/") ([tour]("http://www.gnome.org/~seth/blog/sabayon")) is supposed to be good for locking down applications.

---

### Post by freebird54 on 2007-05-20
You might want to remove some of the boot options from grub on boot up - the recovery console is a bit TOO powerful to let an a__hole into...

There are a number of things of that knid you can do - including booting straight in (unless escape is pressed) or putting a pwd on Grub (and on the computer BIOS for that matter).  Oh - and make sure that the account that has sudo rights is VERY WELL passworded :)

---

### Post by irish_flu on 2007-05-20
> **esoterica said:**
> Your best bet is to just pull the hard drive out of the computer and let Ubuntu run by booting and running off the CD, then no matter what someone does to it a simple reboot will put everything right back to where it was every single time. 

That's a darn good call, but IMHO performance suffers HEAVILY running off of a CD.

---

### Post by esoterica on 2007-05-20
There's also nothing more fun then to set up a web server that runs off the read only CD and leave it publicly accessible on the internet so you can watch people squirm and pull their hair out trying to hack it.

---

### Post by esoterica on 2007-05-20
> 
That's a darn good call, but IMHO performance suffers HEAVILY running off of a CD.


That depends on how much memory you have on the system, it doesn't take much, he said it was a Windows ME box so it probably has at least 256mb which would work just fine. He also said they are new users so I doubt they need much on the end of Cray performance out of it.

If he looks up how to set up a Linux kiosk he'll find plenty of good information on how to completely lock down a system even if an actual kiosk is a bit more extreme than what he had in mind.

Running off the CD with no hard drive even installed also prevents people from installing root kits.

---

### Post by Funk Phenomena on 2007-05-21
Wow, hey thanks for the responses.  I like the funny XP skin idea, lol. Yeah it's an old P3 with 256 ram.  I replaced the thumb screws and put a suitcase lock on the case.  Superficial I guess.  I added several games and educational tools, as well a few hundred mp3s to entice people.

I'll definitely upgrade the passwords and implement some of the other suggestions.  Thanks again, community.  :smile:

---

### Post by shen-an-doah on 2007-05-21
One of the simplest things would be to have it log in to the unprivileged account by default, so that they don't have to know the password to log in. Then there's definitely no way they could use sudo, etc...

---

