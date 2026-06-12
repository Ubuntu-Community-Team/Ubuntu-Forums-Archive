---
title: "Uninstalled Firefox!!"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Joeb454 on 2007-12-06
Ok, so I wanted to install firefox 3 beta 1...which is fine, I could run it from a folder, but I wanted it in place of Ff2.

So I replaced the folder (stupid I know), and then neither would load, now Ff3 loads, but won't actually do anthing. I can't connect to the net here because I need to log in (I'm at Uni) and I can't do that without being in Ff :(

Is there anyway to do this? Or should I just reinstall (installation's like 1 day old :p) I'm running off the LiveCD now :)

---

### Post by KhaaL on 2007-12-06
I think you need to remove your /home/yourusername/.mozilla folder... which I guess is the folder you've messed with?

If you've messed with another folder (you don't mention which folder was replaced), then a purge / reinstallation would be wise.

---

### Post by Joeb454 on 2007-12-06
lol, reinstall it is then, because I replaced the whole /usr/lib/firefox folder :p

Never mind, if anybody knows how I can install Firefox 3 Beta over Ff2 then that'd be great, if not no worries I'll just run it from a separate folder :)

---

### Post by KhaaL on 2007-12-06
:shock:

Why did you do that? though I must say that I admire your courage to mess around with system files... 

I think a simple "apt-get remove firefox" is enough, followed by a installation of granparadiso...

---

### Post by Joeb454 on 2007-12-06
I don't know, I found out that's where the Firefox files where, and figured I'd just replace them, lol.

And I tried uninstalling etc. I believe I ran: ```
 sudo apt-get remove firefox
```

then

```
 sudo apt-get install firefox 
```

And it still didn't work lol

---

### Post by KhaaL on 2007-12-06
Try:

sudo aptitude purge firefox

And tell me if it returns any errors.

---

### Post by Joeb454 on 2007-12-06
If I'd noticed that the 10 hours ago before I reinstalled ubuntu I would've let you know, but given that I've now reinstalled I can't...and I really can't be bothered to try it again, lol.

But thanks for letting me know about that in case I decided to fiddle with any more system files :p

---

### Post by rsambuca on 2007-12-06
You probably don't want to totally remove the standard Firefox, since it will remove the ubuntu-desktop metapackage, and it is also tied into the Ubuntu help system.  If you want to sample 3.0 though, you can install it along side and then run either/or.  I don't believe you can actually have both running at the same time, though.

It is in the repos, so to install it you can run:

sudo apt-get install firefox-granparadiso

It probably isn't the latest build, but it will give you an idea of what it is about.

---

