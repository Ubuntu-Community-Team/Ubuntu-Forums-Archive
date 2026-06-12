---
title: "Straight to terminal after logon"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-09-21
New day New issue...
Somehow messed Xp regisry up with regisrty software on "tuneup" some nice person gave me on a utility cd`s(:-$ ;) :D )lol.....Although i can still get into it.Used system retsore couple of times but never mind XP..

When i now boot ubunto,as soon as i have hit enter after entering my logon details i get taken straight to a box with the following massage

"i could not atart your session and so i have started the failsafe xterm session.Windows now have focus only if you have your cursor above them.
 To get out of this mode type"exit" in the upper left of the window.
 
Tried the the " sudo dpkg-reconfigure xserver-xorg" but nothing happens?
All ive got is this white terminal and if i type "exit" i just goes back through the logon and back to the above mentioned error message.

PROBABL looks like i`d be as well starting over YET again...BUT.i can still get into one and the other probably only needs some commands that i cant suss out right now...I AMM RTFM`s and GOOGLING as always:D 

Not sure if XP issue is conected to Ubunto issue but it was ALL fine until "Tuneup" UNtuned it 

Of course i dont have an XP cd so it`s a bit of a pain in the a** to re-install from the data cd i have but i will IF i must..
As long as this still works i, not too fussed but would RATHER i did`nt have to do Ubu again too.

Great fun as ever but not sure what to do next....with Ubu.....(easy about XP)...nothing but trouble!

Read some stuff about uninstalling then reinstalling the desktop but...??
sorry folks:oops: :D

EDIT:CAN get into the previous kernal on the "grub screen" now...The kernal was just updated in the last couple of days so i reckon it`s more likely to be Ubunto`s OWN issues that are making it have it`s hissy fits as apose to any of the calamities XP is currently having being a cause of them...Xp`s now just rebooting before it even gets to it`s logo screen.No matter WHAT mode i try...Last good config,safemode etc etc...
Will persist.......(with Ubu anyway)

OH.......XP decide to go PAST it`s logo screen this time before rebooting back to grub......(i KNOW where i`ll BOOT it!!!)

---

### Post by bodhi.zazen on 2006-09-21
LOL xpod, now you have done it. :lol:

You just forgot who you are, just log in as you other self and see if that works.

If not:

1. Lets make sure X is stopped:
Ctrl-Alt-F1 to go to tty1.
Log in if needed.
sudo /etc/init.d/gdm stop

2. Now enter the command X.
you should see a gray screen with a black X that moves with the mouse.
Cool :cool:
Well, not that cool. Ctrl-Alt-Backspace to exit.

Error messages? If so post.

3. Now try startx.

Error messages?

Please advise.

---

### Post by gn2 on 2006-09-21
Xpod, you should ask Santa for one of these: [http://www.software.co.uk/Products/Acronis-True-Image-9.html](http://www.software.co.uk/Products/Acronis-True-Image-9.html)

and one of these: [http://www.planetmicro.co.uk/product_info.asp?stockcode=M004852](http://www.planetmicro.co.uk/product_info.asp?stockcode=M004852)
(or similar)
and a spare HDD helps.

Then when you want to have a good fiddle about;) , you can clone your hard drive first.
After fiddling you can simply put back a duplicate drive and any problems created while fiddling  :redface:  will be spirited away.

Now that's magic!\\:D/

---

### Post by bodhi.zazen on 2006-09-21
Exorcism may help.

---

### Post by bodhi.zazen on 2006-09-21
Looks like I'll get a lot of posts in before xpod today. :lol:

---

### Post by xpod on 2006-09-21
DONT be toooo sure about that,,,:D 
Well firstly i dont need no "back up" software as i got my "iso`s" AND i got a copy of my XP "i386" which although a pain in the butt to install from does do the job...

IF i dont get them working then those are all the "backup" i need ..
I dont keep dirty pic`s,important docs OR anything else on my pc`s to back up....IT`s ALL just a bit o fun and THIS is invaluable knowlage EVEN if i do forget half o it before i can apply it.:confused: 

Anyway:D ..I wish i could have taken a screenshot of the screen Ubunto ends up at now...royal blue with big grey box in center surrounded by strange looking characters...and within it say`s.....

The display server has been shut down 6 times in the last 90 seconds.It is very likely something bad is going on.Waiting for 2 minutes before trying again on display:0....

CAN still get in via the previous kernal version ...
OH...and "sods law" yet again NOW it`s booted back ok to the dodgy one...

THAT pi**es me OFF even more.......Happens everytime i start a thread..
Well i could delete ALL this now but might as well give you`se a laugh at my expense.....I find it ALL quite funny so thats all that matters eh:D 

XP is still the same BUT that will give me something to keep me occupied and amused for a while i suppose....I got a "good cd" there with a load of useful utilities on it SO you never know!!!:D ..LOL:-$

EDIT:i got spare hd`s tooo:D

EDIT2...LOL...now upon reboot to the first kernal again i get to

Sysloogd: Cannot grow log structure.:Cannot allocate memory....mmmm
Got some dodgy memory of a guy with a dodgy memory which i put in the other day BUT it`s been fine in here & xp so cant see THATS an issue as well?........:-({|=

---

### Post by Brunellus on 2006-09-21
I know there's a limit (8 total) on smilies per post, but must you treat it as a *target*?  Maybe my eyes aren't what they should be, but I'm having a hard time reading and understanding what's going on through all the smilies.

---

### Post by nickpaton on 2006-09-21
> **Brunellus said:**
> I know there's a limit (8 total) on smilies per post, but must you treat it as a *target*?  Maybe my eyes aren't what they should be, but I'm having a hard time reading and understanding what's going on through all the smilies.

I may be wrong, but I think he's trying to say he has a small problem somewhere, but I could be wrong......:p ;) :D :o :) :( :confused: :mad: 

and the 9th....Oh you ARE limited to 8

---

### Post by xpod on 2006-09-21
:-$ [-X :-...({|= :tongue: :shock: 

Sorry mate..I did`nt realise MYSELF how many where there,
I apoligise for your confusion:D .......oop`s

Anyway.Ubunto now stops at

SYSLOG:cannot grow log structure.Cannot allocate memory.
It halts there for about 4 minutes then carries on but each reboot seems to be halting at the least now.
I really dont think the 2 OS probs are related now but it just seemed awfully strange it happening to both at the same time...

At least THIS is comming ON which is more than that thing is:confused: lol

Again sorry if the wee pictures threw you..merely expressing myself within the limits you set...PLUS,my wee one here loves them so what can i do????If im told to "DO another one daddy...THEN i DO another one!

Ive sent her to bed now so you wont need to suffer no more!!:D

---

### Post by bodhi.zazen on 2006-09-21
xpod, you've been awfully quite. You up and running yet?

---

### Post by xpod on 2006-09-22
LOL.....Got ubunto working fine again but THAT damned XP just prayed on my mind..I would`nt have slept just leaving it even though we dont use it really.
Used "fdisk\mbr" just to check to see if it was a messed up mbr that was now stopping xp but it was still the same .So i restored grub with the help of the cd only then to end up just wiping XP partition with fdisk and left it copying the "i386" over to c: from my copy on cd.
Then i went to bed.

Was going to send it on it`s way(winnt.exe) this morning before e i went out but decided to leave it in case of corrupt files(it sometimes stops if ones not burnt right).

So im back now and have sent it on it`s way and it`s currently copying files to hard disk.......
And at least i did`nt need to ask the missus to change "i386" cd`s over IF it started being arkward.......Now THAT would have been trouble!!

I really dont know why im bothering but it will just pray on my mind:evil: ....
RIGHT.....NOW i can go get showered..lol.It takes a while this way anyway

EDIT:As corrupt as xp files and reg seemed to be,I could access them all fine via ubunto.......great eh!!!

EDIT":...and if your still curious i seemingly used my wrong "i386" cd as ive used the one with the "eula" missing and had to find the good one..
It`s nearly done so i`ll be getting Ubunto back on very soon.....
And i aint touching XP this time....lol

---

### Post by nickpaton on 2006-09-22
If I were you M8, I'd kill the person who gave you that Registry Cleaner program....LOL!!:mad:

---

### Post by xpod on 2006-09-22
NAAA...i`ll just wait till the next time he visit`s Scotland and have some o my friends pay him a visit.....LOL
89%   .......(wish i`d put "smartdrive" ON that floppy....lol)

EDIT:....And at last we have the 39 minutes remaining screen telling me about all the wonders ox XP`s multimedia and the amazing windows media player,,,,,,,,,ARRHHHHHHH...LOL

39 minutes till i get to the good part.....PUTTING UBUNTO BACK ON

---

