---
title: "Argh! gdesklet issue"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by Rumor on 2005-12-04
Greetings:
I *finally* had my desktop the way I wanted it. A few nice little desklets running, telling me the forecast and what was in my pop inbox and one of the RSS news grabbers. I don't recall which it was, because I think it hosed my system. :mad: 

I changed the URL for the rss, but put in the wrong one . . . the one I put in caused the desklet to lock up hard. I can't open the main control for gdesklets anymore as it freezes as soon as the GUI window comes up. 

Is there *any* way i can remove this one desklet from the ones that open when I start the main control window? Or do I have to reformat my HD and reinstall ubuntu yet again? Is there a conf file somewhere that I can edit? 

I'd love to have the desklets back, even the rss one, just with the right URL in it.

I really hope someone in this community knows how to fix this.

---

### Post by Iandefor on 2005-12-04
I don't know how to help you, but I can most certainly say that it's not necessary to reinstall Ubuntu over a few broken desklets... At worst, it could mean logging in to a failsafe terminal and typing in ```
sudo aptitude purge gdesklets
``` and then```
sudo aptitude install gdesklets
``` to reinstall gdesklets. I'll look around a little more and see what I can see about manually removing gdesklets.

---

### Post by Rumor on 2005-12-04
Ah! Found it! Never mind, I've resolved the issue and got it working again!
:D

---

### Post by Iandefor on 2005-12-04
Huzzah! Tell us all how you managed to kill that nasty gdesklet :).

---

### Post by Rumor on 2005-12-04
[QUOTE=Iandefor]Huzzah! Tell us all how you managed to kill that nasty gdesklet :).[/QUOTE]

I edited the /home/.gdesklets/display file and deleted the line that read:

id1133743652465828 %2Fusr%2Fshare%2Fgdesklets%2FDisplays%2Frss-grab%2FRDGrssgrab.display default

the desklet app pnel restarted fine and I was able to put the rss feed with the right url back in place.

---

### Post by Iandefor on 2005-12-04
cool! Now I know about that option for when gdesklets begin to misbehave. Thanks :-D

---

### Post by loeb on 2005-12-15
I think I've done something very similair and am struggling to get it sorted.

I installed ubuntu yesterday, with help from the how to's managed to get opera installed, my soundblaster card working using the digital out and got mail/messenger etc all up and running.

Then I thought I'd be clever and mess about with the desklets.

I managed to get gdesklets installed and set up a couple, but when I came to add one of the rssfeed readers the gdesklets completely froze as described by the op.

I used synaptic to remove gdesklets completely (including config files) rebooted and then reinstalled the two packages. However now whenever I open gdesklets (apps-accesories-gdesklets) the gdesklets shell opens but is empty and eventually when I go to close the shell it reports it has crashed and I have to force quit.

Any advice for a complete noob would be very welcome.

edit: I dont appear to have a /home/gdesklets folder to edit anything in, is that normal?

---

### Post by Iandefor on 2005-12-16
Try "/home/[user name]/.gdesklets"

---

