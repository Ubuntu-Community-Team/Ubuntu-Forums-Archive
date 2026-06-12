---
title: "fiesty or gusty???"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by satelight 7430 on 2007-11-21
hello to all reading this.
I'm new or a semi new ubuntu user. been running since about half way threw fiesty(about 6 months or so) and i have a few questions hopefully some one can help.I loved fiesty and am still running it on a work machine,dont want to upgrade and just ignore the update symbol.
my first question is this,do what can i do to keep the fiesty that i'm running,is there or could there be any securty flaws that need to be patched??(old habits die hard). i guess my main question is,the update sign on the task bar. is there anyway to kill it so i dont update??
is there any disadvantage to doing this??
second and posibly an easyer question,i know I'm not going to use the right termanoligy. when i updated my home computer to gusty,the terminal lanugage seemed to change?? is this simply cause of not using fiestys code(interface) anymore?? is gustys better?? but it seems more diffacult to follow & understand??been reading as much about linux/unix as i can absorb and doesent seem to be enough,this forum is fantastic & I'm searching everyday.
thanks for listing to me and thanks for any responces.

---

### Post by bluepowder7 on 2007-11-21
is there a "Software Sources" menu item in 7.04 Feisty?  if so, then one of the tabs is about updates, and you might be able to turn off update checking there.  in 7.10 Gutsy, it's under System - Admin

---

### Post by Inxsible on 2007-11-21
Switching off updates is not recommended because you will not get update notification for any of your software which is not a good thing, since those updates may fix some important bugs/flaws for your software.

---

### Post by Dr Small on 2007-11-21
> **Inxsible said:**
> Switching off updates is not recommended because you will not get update notification for any of your software which is not a good thing, since those updates may fix some important bugs/flaws for your software.
I always turn mine off because I don't want the updates, and plus, I have about 200 MBs of updates, and that wouldn't fly too well with my parents :p

---

### Post by Pevichaey5 on 2007-11-21
i believe each version of ubuntu is supported with full update for 2 years

---

### Post by gn2 on 2007-11-21
Synaptic Package Manager>Settings>Repositories>Updates and untick the "Check for updates" box.

You can still (and should) check for updates manually,  just accept the updates offered for 7.04, you don't have to click on the upgrade to 7.10 button.

---

### Post by shae on 2007-11-21
Actually each version of ubuntu is supported for at least 1.5 years, LTS releases are supported for 3 years for the desktop, 5 years for servers.  If you want to continue using feisty, you can either ignore it or remove the update notifier from the list of programs to start with the session and run
```

sudo apt-get update
sudo apt-get upgrade

```
once every few days to fetch updates to feisty.

---

### Post by SunnyRabbiera on 2007-11-21
really its up to you, if you feel fiesty works stay with it, if you want to see if gutsy is better go for it...
it really doesnt matter as long as it works in my mind

---

### Post by mikewhatever on 2007-11-21
Feisty is supported untill Oct 2008, so that you can keep using it for almost another year. I am not sure what you mean by 'terminal language ... changed'. There are minor differences between the two releases, so it should not matter.

---

### Post by satelight 7430 on 2007-11-21
thanks to all that have replyed.Its just as i thought,just did'nt know where to look to uncheck. should have known it was in synaptics. love to work my way into and then out of problems.thanks to you all of corse. when i refer to terminal langague i mean the difference as apt to apitude?? also i think gnome to kde??? also i,ve tryed on my home machine(gusty)to install beryl and low and behold its joined with compiz. so now i,ve removed and installed but doesent realy work but my machine still works. so not alls lost. one last question if i may??
to all you whom have been using unix/ubuntu , have most of you been to some schooling for this or is your knowlage from usage time and time again?? are you folks IT professionals(professionals) or just the average user thats grown to your pressent place??
thanks again 
pbs

---

### Post by anjilslaire on 2007-11-21
Well, I'm an IT professional who uses MS at work, but prefers linux when I can, so my home lan is linux-based.

---

### Post by satelight 7430 on 2007-11-21
so your a college grad that persude that profession?? in your experance did the schooling help teach you everything or is the continueing usage the best thing?? from your experance of corse.

---

### Post by anjilslaire on 2007-11-21
My college degree & work experience give me a grounded fundamental understanding of networking & systems in a general sense. As noted, I use Microsoft products professionally; I use Linux as a preference when not working. 

Having said that, moving from Windows to Linux hasn't been difficult for me, and I can see some advantages to both depending on the circumstances. But, my linux knowledge has primarily been self-taught.

Bottom line, an education gets you opportunities. Learning on your own everyday teaches you more in order to use those opportunities best.

---

### Post by rundee_f on 2007-11-22
yup i agree..

i also use both XP and Ubuntu, depends on the situation,, but after i found the "fun" of using Ubuntu, i spent more of my time under Linux..

For the thread starter, u probably might check [http://ubuntuforums.org/showthread.php?t=612504](http://ubuntuforums.org/showthread.php?t=612504) and its poll result.. This may help u..

---

