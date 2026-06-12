---
title: "how to get the &quot;rhythm box music player&quot; and the printer working?!"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by signore.rossi on 2007-07-16
Completely new on board - just installed the OS...

Anybody out there who knows how to get the "rhythmbox music player" and the printer working?

---

### Post by Chonnawonga on 2007-07-16
Hi Rossi,

Depending on your printer, printer setup can be quite easy (or not). Start by trying System->Administration->Printing, and double-click "New Printer".

Rhythmbox should work out of the box: just find it under Applications->Sound & Video. If you want mp3 support, that's slightly more complicated: you have to go into Add/Remove, and install some restricted packages. Try this: [http://psychocats.net/ubuntu/mp3]("http://psychocats.net/ubuntu/mp3")

Good luck!

---

### Post by signore.rossi on 2007-07-18
Hi Chonnawonga,

Thanks for the reply! Much appreciated!!!

I think I know where to find all the relevant functions (music box and printer install dialogue). The problem starts when it comes to - in relation to installing the printer - installing the drivers. The thing just does not do anything. Everything else before that is working fine..... As a printer I´ve got the HP Laser Jet 1020. The drivers are listed in that dropdown list provided by the dialogue.

A friend of mine told me that I would have to organize some plug-ins to get the music box working.  I think I know where and how to start it.

Any ideas?

Thanks again!

SR

---

### Post by Chonnawonga on 2007-07-18
Let me know if you can't get the mp3s working: there are about eight ways to do it, most of which are pretty straight-forward. There are lots of players for Linux, but my favourite is Amarok, which you can add very easily through the Add/Remove system. It beats the pants off most players, but that's just my opinion.

As for the printer, that's a little more tricky. You installed it through the dialogue, and it's on the printer menu, but it doesn't print? I'm no expert with this, but there are plenty on the forums. Usually the first thing to do is run a quick search to see what's out there. I found these:

[http://foo2zjs.rkkda.com/]("http://foo2zjs.rkkda.com/")



[http://ubuntuforums.org/showthread.php?t=429323&highlight=laserjet+1020&page=2]("http://ubuntuforums.org/showthread.php?t=429323&highlight=laserjet+1020&page=2")

My HP PSC 2110 worked pretty much out of the box. I hope you can get your LaserJet working quickly: those are good printers.

---

### Post by user1397 on 2007-07-18
Good thing you have an HP printer, because they are known to work particularly well in linux (thanks to the hplip project)

Have a look at the how to in my signature to try to install it, and ask about it in there if you have any trouble.

---

### Post by ubanchaos on 2007-07-18
well use amorock and get the mp3 plugins

---

### Post by coolen on 2007-07-18
What problems are you having with Rhythmbox?
Personally, I love Rhythmbox. It's simple, stylish, and fairly light. Amarok definitely wins for features, but I don't need them, and I'd gladly take the ease of Rhythmbox.
To enable plugins, go to Edit -> Plugins within Rhythmbox. Take your pick of what you want.
You'll need codecs for mp3s...I use ogg for all my music. It's served me well. I only have one copy of Windows in my house, and it's using Songbird. Either way, mp3 codecs are a cinch to install as of Feisty. Go to Application -> Add/Remove... and install Ubuntu restricted extras. i'm pretty sure it's in there, at least :)
You'll also need to tell it where you keep your music. Edit -> Preferences -> Library, set your path there.

---

