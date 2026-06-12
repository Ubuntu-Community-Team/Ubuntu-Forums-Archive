---
title: "Ubuntu Beginner's Question"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by Simon Berry on 2006-07-12
Ubuntu looks interesting and I am thinking of giving it a go but I have a couple of concerns : my current windows laptop and cable broadband set-up is working fine (it hasn't always) and I have a few devices attached to it (digital camera, mobile phones) and I am wary of downloading Ubuntu in case it (i) stops my PC or broadband connection working fine, (ii) will Ubuntu support added devices such as mobile phones, PDAs, digital camera and all of their relevant software ? and (iii) is Ubuntu ok for watching all media files and web sites or are there some it doesn't like ?

I'm happy to spend some time learning a new o/s, am all for ditching MS if something else viable is there, am fairly IT literate (should hope so I work in IT) and like a challenge but have limited time for investigative problem solving work as when I'm out of work I want to get straight onto my PC, emails or the web (hence this maybe cheeky question hoping for answers quicker than I might be able to find them trawling FAQs, forums or the web.  I've also ordered the CDs as I'm thinking of installing on a spare laptop (it's got windows on it but I could format it) to give me some experience of it and how it interacts with any devices or software I'd want to use.  I just don't want to spend hours and hours re-building my main PC unless I have to.  Also, what does one do about security software with Ubuntu - firewalls, AVS, spyware/adware software, etc ?

Any advice gratefully accepted.

---

### Post by Sonic Alpha on 2006-07-12
If you download the latest CD (6.06), it gives you the option of trying out Ubuntu without installing it.  Which is perfect if you want to see if you'll like it, and if it will work with your current hardware setup.

Like I said, you can try it without installing, you just pop the CD into your drive and reboot.  When you're done, reboot the machine (the CD should pop out on its own) and you'll go back to windows.

---

### Post by Brunellus on 2006-07-12
To answer all your conerns, more or less.

Third-party hardware compatibility is pretty good with Ubuntu...but don't expect *everything* to work.  Notorious problems:  webcams, wireless cards, some specialized hardware.  You will have to tread more carefully, selecting your devices for compatibility.  

That said, there shouldn't be anything that Ubuntu will do to "stop" your setup from running fine under Windows.  If you're curious, simply run the LiveCD and see what works.  The LiveCD has no local state, and changes nothing on your hard drive.  Don't fear a LiveCD.

Security:  this is your lucky day.  Linux viruses have existed, but there are almost none "in the wild."  The only Linux machines that I know actively running AV software are those which are cleaning e-mail traffic headed to Windows machines.  Spyware/adware likewise nonexistent.  Firewalling is possible and desireable, but the system ships with ports closed by default and a minimum of services listening on them.  The truly paranoid can configure their own firewalling rules using IPTABLES and the "Firestarter" frontend for that....but in practice, if you're sitting behind a NAT router, you're pretty well covered.

Finally: Do NOT assume that merely because you work in IT that you automatically have a better chance of knowing/understanding Linux.  You will discover that there are many things you will have to learn as well as UN-learn.  Linux is NOT Windows.  Don't expect it to be.

---

### Post by DarkOx on 2006-07-12
Ubuntu 6.06 comes as a "live cd", which basically means that the entire operating system can be booted from the cd, and loads onto your computer without touching anything on your hard drive (stuff like your windows system). This allows you to take Ubuntu for a test drive first, to see if you like it. If you do, you can easily install it to your hard drive.

You also don't have to uninstall windows to install Ubuntu to your hard drive. You can have both, and simply select which operating system you want to use after you boot up.

As for security: Linux doesn't really get spyware/adware, as the market is too small for people to even bother to write Linux spyware. Assuming they did, Linux's use of a root password for security means that it's unlikely people can install software to your computer without you specifically supplying your password. The same goes for viruses. There are firewall programs out there - I've heard the [Firestarter]("http://www.fs-security.com/") program is good, but I haven't used it myself.

---

### Post by Simon Berry on 2006-07-12
Thanks for your answers so far, most helpful and very happy and grateful to see a few more.  I guess I'm still a tad worried about my devices and software they use but I'll have to try, security is a big concern of mine (maybe I am truly paranoid) and I would like to use AVS, firewall and something to stop adware/spyware - just because it's a small shop and nobody much may be writing stuff for it this could well change. As for what I do in IT I would be under no illusions about it's difference and the learning curve. My mention of formatting my spare is just my preference for starting with a 'clean' PC when either re-building or particularly for trying a new o/s as in this case.

---

### Post by Sonic Alpha on 2006-07-12
You don't have to worry about viruses, they're mostly written for Windows.  The ones for Linux are not "in the wild", which means you have nothing to worry about.  The only need to use virus software, would be if you were setting up a mail server.

Spyware/Adware also doesn't affect Linux (from what I understand).

However there are programs out there.  If you're just running Ubuntu as a desktop, you may wish to try [AVG]("http://free.grisoft.com/doc/1"), as your virus scanner.

---

### Post by Brunellus on 2006-07-12
For some discussions on Linux viruses and the difficulty of making them:

A brief treatment:

The Short, Hard Life of a Linux Virus
[http://librenix.com/?inode=21](http://librenix.com/?inode=21)

A more systematic treatment:

[http://linuxmafia.com/~rick/faq/index.php?page=virus](http://linuxmafia.com/~rick/faq/index.php?page=virus)

---

