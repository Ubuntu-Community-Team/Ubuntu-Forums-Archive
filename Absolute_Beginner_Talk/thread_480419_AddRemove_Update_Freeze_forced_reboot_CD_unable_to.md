---
title: "Add/Remove Update Freeze forced reboot CD unable to mount"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by DesiArnez6 on 2007-06-21
Hey everyone ;) Basically, I have notice a problem recently and am not sure if it is because of an update (I have done 2 updates, one with about 5 files, and another one recently of about 40MB).

I'm running a Sytem 76 system Gazelle, 1GB Memory, with a CD/DVD, and Celeron M440 1.86Ghz, Ubuntu 7.04
I thing to note, EVERY freeze has taken place with either Add/Remove Synaptic or the System Update Running. Most occured with Firefox opn, althoug one freeze occured with it closed. Also, several of the freezes have occured whilo updateing and trying to access a CD to play music.

Upon using Ctrl-Backspace, the usual terminal login sows up, except all o a sudden I get a continuous response on each line of code of anumber inside brackets with gradualy increasing numbers , plus the message "hdb drive not ready" on each line beside the number and brackets. Every second a new line appears, and a hard reboot is required.

(For what its worth, not sure if related) but Ive noticed that when I enter a music CD into my drive, Soundjuicer opens, and will play it, HOWEVER, when I try to open the drive, by clicking using a file manager, I receive the message that its unable to mount ?!?!? So I'm unable to find it to play with anythng else such as XMMS, Nope, ONLY "SoundJuicer" strange. 

Many of these "lockups" have occured while trying to play music, BUT, EVERY lockup has happened while downloading or upating from one of the repositories.

When it happens, th download is able to finish till completion, yet the cursor dots move around in the circle but every few seconds only, in a choppy sort of way. mouse wont move but every 5 seconds and only for 1 second, and then eventually nothing responds, including keyboard if you wait too long. The one time I was able to slowly get the mouse over to close Firefox, upon close, system was still frozen (well you know actually 99%frozen if you count the ability that the computer is on 1% speed).

Anothe side note, this recent update disabled my sound, so I reloaded System76 drivers and seems to be back to where I was before the update download (still trying to analyse a minor sound issue but that a Whole post ;) )

Anyones help would be appreciated, this freezing thing has got to stop :)
Thx.

Anyone with help would be appreciated.

---

### Post by Happy_Man on 2007-06-21
Have you checked for what is eating processor? Try this: Open a terminal (Applications--.Accessories -- Terminal) and enter the command ```
top
```. Leave that open so you can see it, and then  try to freeze it again. Whatever is taking up processor will shoot to the top of that list, and then you can diagnose from there.

---

### Post by DesiArnez6 on 2007-06-21
THats a great command to know. The next time it locks up, I guess ill try to get to terminal with Ctrl-Alt-F1 and then "top" as you say to check the CPU , for now everythings fine nothing takes up more than 2% (although if system freezes that could change) right now Xorg is on top with metacity and gnome-panel opera hald addon stor every once and awhile, mostly each around .3%   I'll definitely post here again after next freeze to keep you updated.

---

### Post by DesiArnez6 on 2007-06-21
well THAT was quick, I didn't expect to be back here so soon :p Geez. Well It just froze on me again.

Programs that were open: Opera Browser, GNOME PPP, Firefox Browser, terminal (with "top"running) and VLC Media PLayer (PLaying stream at [http://84.54.69.58:1060/](http://84.54.69.58:1060/) ) Than all of a sudden it froze SO...

In panic, I quickly pressed Ctrl-Alt-F1, Now Im at the terminal and I see:

[5246.696000] hdb: drive not ready for command
[5251.728000] hdb: drive not ready for command

Basically this continues on each line every second, assuming that the system won't respond I hit Ctrl-Alt-F2 (now I realize it probably wasn't necessary) to enter virtual 2 terminal, so same thing (but with different numbers in the brackets, frustrated, I type my username anyways, and despite all these weird messages it seems that the terminal is still listening to me?? Hmm ok, so with all these annoying "hdb" errors in the background, I type my password, It logs me in (still repetetive errors), At the prompt I type "top"

Well. BIG changes it seems. Now, "hald-addon-stor" is taking up 99.1% of my CPU??????? Why? Hmm everything else (xorg, metacity, gnome-panel, top, etc 0.2 to 0 % )  (BTW while in "top" I dont get those annoying "hdb drive" errors :)

so I quit top, back (the "hdb" errors return still every second) I type "sudo killall hald-addon-stor" and...

The music from my stream returns , STILL getting these annoying errors "hdb drivenot ready " with all those numbers in the brackets. But since I hear music, I decide to hit Ctrl-Alt-F7 to return to the GUI, well ..

It seems everything is Perfect. unfrozen, with all programs intact.

So... Anyone know whats goin on? Will it freeze up again? And what is  "hald-addon-stor" and what is it doing to my CPU?

Also, whats up with all these [5246.696000} hdb:drive not ready for command , errors I kept gettig when in the terminal? (I DONT get them when i access terminal from Applications>Accesories>Terminal)

Btw, thanks for responding so quickly, this community is amazing. :) Ive learned so much (This is my first week ever on linux, just dumped windows so its scary, and i really dont know much about linux, Ive basically learned everything so far here at the site, I didnt even know what a terminal was last week if youd asked me :p )

---

### Post by Happy_Man on 2007-06-21
Drive not ready for command.... that sounds like somethings shoving data at your "hdb" drive faster than it can process it..... And since of course the drive is constantly swapping stuff.... that would be a problem. Never heard about this before.... perhaps some hoary old lag trolling these forums has a better solution?

---

