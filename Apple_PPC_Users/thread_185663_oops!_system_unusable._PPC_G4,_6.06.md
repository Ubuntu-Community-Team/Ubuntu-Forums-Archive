---
title: "oops! system unusable. PPC G4, 6.06"
date: 2006-06-01
forum: Apple PPC Users
---

### Post by hotani on 2006-06-01
And I'm not reinstalling AGAIN! ](*,) 

I booted up and went into synaptic to look for some software. Clicked on search, entered some text, hit the search button and synaptic vanished *crash!* Tried it again, same thing. 

So I thought I'd run the system updater... started it up and then opened firefox to see if my synaptic problem was out there anywhere. Firefox froze the entire UI. Awesome, lets try again. Restarted GDM, ran update manager. Opened firefox - freeze. Opened synaptic, same search/crash problem. Restarted. Same deal. 

And my sound card has never worked. ug.

Fortunately I've experienced Ubuntu Dapper on a PC laptop and desktop and both work fine - mostly. Plus I'm building a PC soon to replace the Mac (which will be running OS X from now on!). I'm frustrated, but my PPC install has had severe problems from Day 1, so I guess I expected it to die gloriously in battle eventually.

That's all, carry on. :-|

---

### Post by autocrosser on 2006-06-01
Yes-I feel your pain---there were times that I wondered if it was worth it--Right now I'm in my Breezy install (a real clean, simple one) doing the Dapper update--I figure that I'll use the "old" -smp kernel from Breezy until I can get a new, shiny one that "works"--I have toyed with building a PC box--just have ran Macs for too many years & find the idea a bit on the "ugh" side still--but Flash & some of the goodies that call to me from the Dark-side have a great amount of appeal:???:

---

### Post by pauljwells on 2006-06-01
I had lots of random crashes/freezes on my powerbook G4. Turned out to be powernowd (frequency scaling)

this command disables it

sudo update-rc.d -f powernowd remove

Now my mac install is absolutely rock solid never crashed, whereas my pc build still does hang occasionaly.

you can restore powernowd by

sudo update-rc.d  powernowd defaults

edit:
Just an update. As of the last two days powernowd seems to be behaving itself. I have it re-activated and my PB now runs 5C cooler!

---

