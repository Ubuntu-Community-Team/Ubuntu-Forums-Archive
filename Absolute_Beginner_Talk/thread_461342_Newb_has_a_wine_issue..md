---
title: "Newb has a wine issue."
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by chad386 on 2007-06-01
Hello All.

I am trying to convert our office to Ubuntu from Windows XP.  So far, things are looking very good.     With Feisty, I've got all computers with wireless cards working, printers working.  I really can't believe how much faster Ubuntu is on our hardware than XP was.  

One fairly big issue is the office software we use.  It's called Medisoft, version 6.  It's an older version of the program, circa 2001.  It runs great on our XP machines.  

So I used Automatix to install Wine on a couple of our machines.  Got Medisoft installed and it worked perfectly!  (even though it's nowhere on the approved application list, probably cuz it's pretty obscure).  

The one dilemma is that the program prompts you to register the software everytime you boot it.  It expires after 90 days.  I have all the information needed to get the software registered.  (It's actually an offline registration tied to information you give them when you place your order; must just verify parameters with data burned on the disc on a per customer basis)

The one thing wine has trouble running is this registration window.  It locks the program up instantly when I select "register."  I can make out some type of window resize error, but the program becomes non functional after that.  

I've tried messing with winecfg to change versions of windows, graphics handling, libraries, etc.  But nothing seems to work to get past this one little bug.  It's aggravating because it seems I'm so close to getting everyone transitioned over to ubuntu, but a software registration bug is keeping me from it.  

I've tried to do as much research into wine as I can, like trying to get it to do a debug log; but have so far been unsuccessful.  

I'm thinking I can just keep the machines on dual boot for now, realizing Ubuntu will never get used due to the Medisoft incompatibility.  Does anyone have any ideas on this at all?  is VM Ware an option in this case?

---

### Post by harek on 2007-06-01
vmware would probably be your best bet. especially if you have uninstalled xp.

---

### Post by chad386 on 2007-06-01
is vmware difficult to use?  I'm a bit confused about the different versions and if it's actually free or not.

---

