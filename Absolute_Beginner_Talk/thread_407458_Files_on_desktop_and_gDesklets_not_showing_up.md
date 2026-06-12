---
title: "Files on desktop and gDesklets not showing up"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by Gleep on 2007-04-12
Hi sorry if this is a stupid post, but I've tried googling various things and nothing matching my problem has come up.

I'm running Ubuntu Edgy, with Beryl although I don't think Beryl is the problem since all was working fine up until yesterday, and I can't put my finger on exactly what triggered this.

I've been using Linux in general for about 2 weeks, and I love it, I'm learning bit by bit and although I'm dual booting with Windows XP home, I can't see myself going back, I only use it for things like to sync with my mobile phone etc.

But my problem is that suddenly nothing on my desktop will show up, no files, folders or my gdesklets. Everything is still there in Places > Desktop so I know it's there, but I can't see it on my actual desktop, only the background.

Sorry for being a n00b, I just hope someone will be able to tell me what's happened, since generally I've been able to google past problems and find a solution, but I'm having no luck this time.

Thanks in advance.

---

### Post by justleen on 2007-04-12
what are the rights on the files?
do a ls -la in your Desktop- dir, and see wether the ownership is correct..

---

### Post by Gleep on 2007-04-12
> **justleen said:**
> what are the rights on the files?
do a ls -la in your Desktop- dir, and see wether the ownership is correct..I don't know how to do that :$

I know it's probably dumb to make the jump from windows to linux before I know exactly what I'm doing, but having never so much as touched command line in windows or anything I'm basically learning as I go along :$

---

### Post by Gleep on 2007-04-12
For some reason, it now seems to have fixed itself, after days of not showing, I restarted and suddenly everything is back... everything that is except my gdesklets.

Not sure what's up there.

---

### Post by jrandolph on 2007-04-12
I dont know if I may be of any help -- but i have beyrl installed and when i am using it -- my gDesklets dont show up -- but if i return to the other windows manager they do 

Maybe it has something to do with that 

Just thought I might put in my two cents

---

### Post by TURNER on 2007-04-12
Hi Gleep,

In order to load gdesklets on boot you will need to enter them as a startup entry....

System tab ---> Preferences ---> Sessions

click "Startup" followed by the add button, now simply write gdesklets and ok it all.

Gdesklets should now be there on startup..

---

### Post by Gleep on 2007-04-12
I do already have them loading at startup, and it's always worked fine, they just seem to have gone on a journey lately and I'm not sure why...

Also in regards to jrandolph's post, they've always worked in beryl before, and even if i switch to metacity they still don't appear. Thanks for replying though.

---

### Post by jrandolph on 2007-04-12
Well then I guess that makes me kinda wonder why mine dont show up with Beryl.

Thanks for that -- now I have some detective work to do

---

### Post by packjamNL on 2007-04-12
I got the same problem, maybe my HWare in the signature makes it more clear. 
This config ran well @edgy(X86_64), now I am using Feisty Fawn, one week old version, I tried every setting in the beryl-manager, but gdesklets dies after 2 seconds, gdesklets wich I got from synaptic worked fine with beryl on 6.10 Edgy (x86_64) again. Straaaaange?!
:KS

---

### Post by Gleep on 2007-04-12
Yet again, a reboot later and they're magically fine again... now all I have are little bugs like when I try and restore a window it will quickly minimise again straight away and things. Also my bookmark's toolbar in FF doesn't work, when I click on my bookmarks nothing happens.
I went on my winblows a minute ago to see if I was having that problem there but I'm not. Otherwise I would have put it down to my mouse or something.

I guess these are the sorts of bugs I'll just have to live with.

---

### Post by NikoC on 2007-04-12
Perhaps [this]("http://ubuntuforums.org/showthread.php?t=369961") can help out and to be more specific the third and forth reply in the thread. You might also want to change the delay time to e.g. 4 or 5 seconds.

Good luck!

---

