---
title: "Help! My panels are broken! o.O"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by Raavea on 2006-06-18
I was making a new panel, when the panel Add Stuff thing hung, and I had to Force Quit. Now, my hidden panel won't un-hide (not important) but my main panel, with my EVERYTHING in it, don't work!

 I can't right click to fix it or alter it, non of my icons, launchers, or my main menu or wastebasket even, work. You know how they usually light up when you hover? They aren't even doing THAT. (My memory graph is still working, and my geyes still follow my cursor, but I can't interact with anything on the panel.)

 I tried ctrl+alt+backspace, but that hasn't helped. I can't access anything now, the only way I managed to open firefox is because I'm a webdesigner, and haven't cleaned my desktop up recently, so I have a few folders with .html docs in them, which auto-open in FF.

 Please, can anyone help?

THINGS I DID SHORTLY BEFORE CRASH:
 Right-clicked my main panel, made new panel.
 Set new panel's attributes (black, mostly transparent, auto-hide, no expand)
 Right-clicked new panel, added Lunar Clock.
 Right-clicked Lunar clock, altered my latitude and longitude information.
 Right-clicked new panel, added weather forecast.
 In the add applets panel, there was a new part 'amusements' with penguins in it. So I clicked it, to see what it did to my new panel. Nothing happened. Then, I got the crash. (Note that I have a memory-gauge thingy in constant sight on my main panel, there was no 'IAMLOADINGSOMETHING' spikes. It was just the usual small, 2% peaks for cursor movement etc. Then a big peak for the crash.
 Then, my panels went manic, the new one hid, they stopped being transparent, no interaction.

I cannot click anything in the panel, though I can click my system memory gauge thing, my trashcan, and when it appeared earlier my update notification icon in the systray.

---

### Post by user1397 on 2006-06-18
have you tried making a new panel (with all your same stuff as before) and deleting the old one?

---

### Post by Raavea on 2006-06-18
How do I do that?

 The only way I know of creating and deleting panels is by right-clicking on an existing panel. Which I can't do...

 :?

 I tried several things so far - opening terminal (right click on a folder, open in terminal, lifesaver so far!) and typing 'gnome-panel' but it says something about one running, and exits.

 I tried ctrl+alt+delete (opens system thingy..) and stopping/killing/ending gnome-panel, but it just keeps reloading again, exactly the same. :?

---

### Post by user1397 on 2006-06-18
how about : ```
killall gnome-panel
```

---

### Post by user1397 on 2006-06-18
have you also tried just restarting?

---

### Post by Raavea on 2006-06-18
Nah, it reappeared again, still no interaction.

 Might I add, I'm still rather new to the terminal commands. I only remember a handful of DOS commands from when I was little, such as cd and dir... I have been guessing at commands! :lol:
 I took a look at help but it wasn't really... Helpful.. o.O

 Is there a terminal command to delete both panels and create one new one?

ETA: And yeah, I've restarted a dozen times, with different Gnome sessions, including an e-gnome sesh, and the default, no startup scripts gnome.

---

### Post by user1397 on 2006-06-18
im also guessing at the terminal commands...so just be patient! :D

---

### Post by Raavea on 2006-06-18
>.>

<.<

Even though my computer is kinda ******, and I can't do much...

 ...This is kinda fun. :lol:

EDIT: Okay, so. Second killall displayed an update notification! WHICH I CAN CLICK! (But I still cannae click anything else...) So I'm gonna go try that...

EDIT2: It was just a WINE update. No change. ;____;

---

### Post by Raavea on 2006-06-18
So.. I am now running my enlightened gnome session. The panels are still there, still broken.. I have tried countless methods of getting rid of them, and am still stuck.. *blinks*

 What in the four hells has gone wrong? I'm going to go edit my top post with the few things I did prior to said nasty-crashy-muh-whatsit...

---

### Post by uzi09 on 2006-06-18
[QUOTE=erik1397]have you also tried just restarting?[/QUOTE]

i second this...have you tried it yet or not? you didn't mention.....

---

### Post by user1397 on 2006-06-18
i really dont know how to help you any longer.  i would just wait till tomorrow when more people are logged on to get some help from them.  sorry!

---

### Post by Raavea on 2006-06-18
[QUOTE=uzi09]i second this...have you tried it yet or not? you didn't mention.....[/QUOTE]
[QUOTE=Raavea]Nah, it reappeared again, still no interaction.

 Might I add, I'm still rather new to the terminal commands. I only remember a handful of DOS commands from when I was little, such as cd and dir... I have been guessing at commands! :lol:
 I took a look at help but it wasn't really... Helpful.. o.O

 Is there a terminal command to delete both panels and create one new one?

**ETA: And yeah, I've restarted a dozen times, with different Gnome sessions, including an e-gnome sesh, and the default, no startup scripts gnome.**[/QUOTE]

Thanks for trying to help, everybody.

---

### Post by uzi09 on 2006-06-18
oh my bad, didn't catch that.

perhaps you can try to fix broken packages or something (sorry, venturing to the unknown here):
```

sudo aptitude update
sudo aptitude upgrade -f

```

---

### Post by Raavea on 2006-06-18
Danke, it didn't make a difference.

Though the second command removed an unused lib, I killall'd the panels again via terminal and still nuffink different.

I need more coffee... *[SIZE="1"]Where's my IV...[/SIZE]*

OW.. I had an idea.
 Perhaps there's a terminal command to re-install gnome-panel...?
(Off to hunt.)

---

### Post by user1397 on 2006-06-19
[quote=Raavea]Danke, it didn't make a difference.

Though the second command removed an unused lib, I killall'd the panels again via terminal and still nuffink different.

I need more coffee... *[SIZE=1]Where's my IV...[/SIZE]*

OW.. I had an idea.
 Perhaps there's a terminal command to re-install gnome-panel...?
(Off to hunt.)[/quote]ah yes! try reinstalling gnome-panel in synaptic.  post back your results.

---

### Post by Raavea on 2006-06-19
:cry: Absolutely no change. :cry:

---

### Post by user1397 on 2006-06-19
try uninstalling it, and then go to /usr/bin and see if gnome-panel is still there.  if its still there, try one line at a time:```
cd /usr/bin
sudo cp gnome-panel gnome-panel_backup
sudo rm gnome-panel
```

*EDIT: then try installing it again

---

### Post by Raavea on 2006-06-19
If I try to uninstall it, it insists on uninstalling the ubuntu-desktop as well.

 0-0 Should I go ahead, or will it kill my system?

---

### Post by user1397 on 2006-06-19
[quote=Raavea]If I try to uninstall it, it insists on uninstalling the ubuntu-desktop as well.

 0-0 Should I go ahead, or will it kill my system?[/quote]no go ahead, it wont do anything.  ubuntu-desktop is just a metapackage that links a whole bunch of dependencies together.  you can reinstall it later anyway.

---

### Post by Raavea on 2006-06-19
Augh, three errors and they won't go away!!!

I uninstalled great, reinstalled, killall'd to get 'em to refresh. Then I got errors about applets. I'd give the exact error, but all three messages went blank on me, not even buttons.

 I can't get rid of them! D:

EDIT: Thank the four hells I'm in enlightened gnome. I had to annihilate the three errors. I went and checked, and gnome-applets was uninstalled. I reinstalled and killall'd again... No errors, but still no interaction! o.O

---

### Post by user1397 on 2006-06-19
[quote=Raavea]Augh, three errors and they won't go away!!!

I uninstalled great, reinstalled, killall's to get em to refresh. Then I got errors about applets. I'd give the exact error, but all three messages went blank on me, not eve buttons.

 I can't get rid of them! D:[/quote]can you post a screenshot of what all of this looks like?

---

### Post by Raavea on 2006-06-19
I got rid of them now, thanks to Enlightened Gnome's anihillation function... Sorry. (Edited the post..)

EDIT: *snickers evilly* I uninstalled gnome-panel, gnome-applets. Killall'd the panel.
 It didn't try to re-appear, because it has been uninstalled.
 So, no more panel to annoy me by not working. :)
 I'll figure out something to get a menu accessing thingy. Likely a gdesklet.

---

### Post by user1397 on 2006-06-19
[quote=Raavea]I got rid of them now, thanks to Enlightened Gnome's anihillation function... Sorry. (Edited the post..)

EDIT: *snickers evilly* I uninstalled gnome-panel, gnome-applets. Killall'd the panel.
 It didn't try to re-appear, because it has been uninstalled.
 So, no more panel to annoy me by not working. :)
 I'll figure out something to get a menu accessing thingy. Likely a gdesklet.[/quote]well then, do what pleases you.

---

### Post by Raavea on 2006-06-19
Thank you so very much for all your help, Erik.

---

### Post by user1397 on 2006-06-19
[quote=Raavea]Thank you so very much for all your help, Erik.[/quote]you are very much welcome

---

### Post by uzi09 on 2006-06-19
sorry to get back so late (sleeping :D)...

if you would still like to give it another go, you could try to reinstall ubuntu-desktop again.

```

sudo aptitude reinstall ubuntu-desktop

```

sorry, i'm not on my buntu box right now, so double check if you can use the "reinstall" command or not. if you cant, just try to uninstall then install again.

uzi

---

### Post by Haegin on 2006-06-19
Or 
```

sudo apt-get install gnome-panel

```
to get it back again (im not crazy) then
```

sudo apt-get remove --purge gnome-panel

```
to remove it again with all its configs before
```

sudo apt-get install gnome-panel

```
again just to get back the default panel.
I hope it helps...

---

### Post by Raavea on 2006-06-20
Ahh, thanks peeps.

 Sadly I'm boarding a plane to go far, far from my PC for a week in about six hours. And at the moment I'm using my mother's XP-Pro (*shudder*) alienware (*drrrrooooooolllll*).

 However, I'll try these new things when I get back to good old Bernard.

---

### Post by Raavea on 2006-06-29
Ehh, tried it yesterday evening, didn't work.

 Now when I enter GNOME, it gives me an error message saying something about gnome-panels detecting another gnome-panels running so it will now exit.

 The broken panels are gone, but there aren't any panels left at all! :?

---

