---
title: "Regressing from 64 Bit to 32 Bit"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by muffiee on 2007-06-08
I am taking the advice of a few fine folks here on the forums and I have decided to replace the 64 bit version of Ubuntu I installed on my machine with the 32 bit version--in order to get better supported drivers/plugins/etc.  

However, I want to be sure that  I keep my emails, documents, bookmarks, contacts, user information etc.  I spent a lot of time fixing everything the way I wanted - importing contacts and setting up programs.  It would be a shame to lose it.

Is all of that in the /home directory?  Do I have to do anything special to copy the "/.*****" files [I think they call these hidden files -- the ones that show up when you use the 'ls -la' command].  I can make a tar, but I just want to be sure.

Also, I read somewhere that the /home directory was 'preserved' if you did a re-install.  Is that true if you 're-install' a different version, like I'm going to?  Will the data work if saved in the 64 bit version but then tried to make work with the 32 bit version?

I did a pretty complete search of the forums and found lots of information on upgrading, re-installing, and installing, but did not find anything on going backwards from 64 bit to 32 bit.  Everyone is so helpful here and I appreciate their patience with my bunches of questions.  So if this is already answered in a FAQ or Sticky someplace, I won't take offense if you tell me to RT*M -- please just point me in the correct direction!

A one week old Linux student.

---

### Post by Traceur-UK on 2007-06-08
This is relevant to my interests. I'm also thinking of 'regressing', as it were, due to compatibility and such. Depends on how many more setbacks I have, think I've got enough workarounds at the moment.

Anyway...ignore me, this is his thread.

---

### Post by ryanVickers on 2007-06-08
I've never heard that it keeps the /home files before, but although I've been using Linux for years, in some areas, I know nothing like that!

In some cases, the 64 bit does make a significant difference in speed, but for the most part, you probably won't notice it at all, although I'm no expert on this either.  But if you need full compatibility with everything, I would say this is a good idea.  If I were you, I would just *keep* everything in your /home/xxxx, like copy it somewhere else when you re-install.  Also, WARNING!!!  some compression formats like tar tend to corrupt themselves, or so it seems, when they contain massive amounts of data!  Unless completely necessary, I would not compress anything, or maybe compress individual folders or groups of them if they're small.

---

### Post by 5-HT on 2007-06-08
> **muffiee said:**
> 
Is all of that in the /home directory? 

Yup. Also may be a good idea to save anything in /etc that you have modified, as well as your menu.lst, xorg.conf, fstab, etc...

> **muffiee said:**
> 
 Do I have to do anything special to copy the "/.*****" files [I think they call these hidden files -- the ones that show up when you use the 'ls -la' command].  I can make a tar, but I just want to be sure. 

Nothing special, just make sure that they are contained in the tar or in whichever backup method you choose.


> **muffiee said:**
> 
Also, I read somewhere that the /home directory was 'preserved' if you did a re-install.  Is that true if you 're-install' a different version, like I'm going to?  

If /home is on your root partition, it will not be 'preserved' if you do a clean install. A great way to go is to have your /home on a separate partition. That way you can reinstall your OS without having to worry about your personal data.

---

### Post by muffiee on 2007-06-09
Thank you everyone who responded.  I gone ahead and installed the 32bit version, but I messed up the tarball --it was corrupted somehow:(.  Anyway, I'm real good at setting everything up now, since I have so much practice.  

Its on to the VMware Setup.

---

### Post by ryanVickers on 2007-06-09
Oo! Oo!  Make sure you get VMTools, and go [here]("http://www.easyvmx.com/"), it's good! :p

---

### Post by starcraft.man on 2007-06-09
Just to provide options. You may want to look at [Virtual Box]("http://www.virtualbox.org/"). If your not paying for a Workstation version of VMware with all the features, Virtual Box will provide more versatility than the regular player/server and its partly open source :).

---

