---
title: "Shifting Thunderbird mail and settings from XP to Ubuntu"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by Stephen_A on 2006-12-26
I'm moving from Windows XP on an IBM Thinkpad to a Dell 1150 that is running Ubuntu 6.06  fine.  I have copied the entire Thunderbirds directory containing the .ini and .js files onto a USB drive. Using the Thunderbird Import facility (Tools>import) I'm unable to even locate any relevant files using the Import function. For example address books are in .ldi or .ldif files. I don't have any of those. When I try to import mail, the dialogue box offers to import 'Communicator 4x.'

I would appreciate any suggestion or pointers in the right direction. I've Googled to no avail and someone on the Mozilla forums had the same problem. Unanswered. 

Cheers, 
Stephen.

---

### Post by marianom on 2006-12-26
There's no need to import. See [here]("http://www.ubuntuforums.org/showthread.php?t=291681&highlight=thunderbird") where once I answered a similar question. Of course, I assume you're trying to migrate from tb xp to tb ubuntu.
If you have any problems, just post them here.

---

### Post by marianom on 2006-12-26
By the way, tb's address book is the file named abook.mab inside the profile folder.

---

### Post by Stephen_A on 2006-12-26
Thanks, Marion. Yes I should have pointed out that I was going from TB on XP to Ubuntu. The problem is, that I don't appear to have Thunderbird on my home directory. On my home directory there is only: 

stephen@stephen-laptop:~$ ls
Desktop  DicOOo-1.6.2.sxw  downloads  Examples  rp-pppoe-3.8  Word
stephen@stephen-laptop:~$

Where should the Thunderbird directory be? Thanks. 

Stephen.

---

### Post by marianom on 2006-12-26
It's a hidden folder.
You should have it as .mozilla-thunderbird in your home.

---

### Post by Stephen_A on 2006-12-26
Whoops. Please disregard the above. 'Show hidden files...' (Sound of head banging on table....)

---

### Post by hyper_ch on 2006-12-26
Poor table....

If you have more questions just ask :)

You can just copy the files over, all I needed to do afterwards is setting correct ownership :)

sudo chown -R user:user .mozilla-thunderbird

---

### Post by Stephen_A on 2007-01-01
Thanks for your replies everyone. Great help. I'm late replying as out here in Hong Kong we couldn't access many sites because of damage to cables caused by the Taiwan earthquake.

---

### Post by marianom on 2007-01-01
Hey, Stephen.. I'm too migrating to a Dell Inspiron 1150. Let me know how it was for you, just to be ahead of problems.

Ps: Does anyone know why they're soooo heavy?

---

