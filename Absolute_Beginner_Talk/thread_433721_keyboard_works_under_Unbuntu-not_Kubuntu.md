---
title: "keyboard works under Unbuntu-not Kubuntu"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Pistolla on 2007-05-05
This a rehash...i may have put it under post Here it is:

I have a question more than a reply. My keyboard works fine and dandy...under Ubuntu (i have just upgraded to Feisty)
Before i upgraded to Feisty i had Edgy (of course, of course) i also run from time to time (in the past-under Drake, at least) Kubuntu. and i dual-boot with windoze XP (Pro)
Some time after Edgy was up running and doing it's thing (maybe2-5 months) the keyboard wouldn't work anymore (Kubuntu). So i was stuck (i thought) for two days with a "dead Linux." i could go under windoze and it'll work. i can go to Splash screen and type my name/p-word not a problem go to Kubuntu, stops working. I thought i'd try it under Ubuntu and everything works fine!! So basically i didn't use Kubuntu after that. After all, i can use KDE stuff under Gnome. The problem's still there even after upgrading to Feisty! It just gets under my craw that something's not working, and like a little kid who closes his/her eyes and thinks no one can see them, i try to do that and cannot.
i don't know if the BIOS thing is the culprit or not. I don't know how to get into it or anything.
On an aside, i was having difficulties with runnin' ClamAV (sayin things like it could see this type or that type of file) i couldn't update it. iit would say i am not under Root. So i went to Synaptic and looked through there and saw i needed a coupla those 'wares and since i did that i have had no problems and can, now, check for viruses. i am not one of those who thinks we will never get a virus under Linux plus i also dual-boot. I am now that much closer to chunkin the Whole windoze OS. i love Linux (had it since Dapper). The people who actually catered to us "wienies" who would not "jump ship" b/c it don't run like windoze (in my case it was fear of a new thing but wanted to try it badly-glad i did). I can say it works better. the only difference is that we have to "rework our brains" a little bit to run (X)(K)Ubuntu and Linux in general
Anyhoo, 'nuff "butterin the bread" (of which i wasn't lying) i just need help with keyboard issue and it would be GREATLY appreciated
Thanx a lot
Pistolla

---

### Post by starcraft.man on 2007-05-05
This is a very weird problem, can't say that I have ever heard of it. I am fairly sure that Ubuntu and Kubuntu use the same drivers/files to implement your keyboard. I am not sure if you have tried this, but do you have a spare keyboard or a friends? Can you plug that in and see if it works in both? If so it may just be your keyboard... Another thing to try, is this a USB keyboard, if so, get a PS/2 converter and try the that old plug, see if it changes. Do the reverse if its an old PS/2 plugin and try a USB one.

If this problem persists, you may even wanna report it to launchpad for bug fixing.

---

### Post by Slackpacker on 2007-05-05
Maybe reconfigure the X server to make sure its keyboard settings are correct?

---

### Post by Imamoomoocow on 2007-05-05
:popcorn: By no means am i a Linux expert I have only been using it for about 3 weeks.  I had a problem to this on my machine.  If you are using a Logitech wireless keyboard or mouse you sometimes have to re-connect it wirelessly by pressing the connect button on the bottom of your keyboard.  I think it's a bug caused because these keyboards are designed to work on Windows only.  Damn logitech!

Anyway, hope this was of use to someone.  If not then disregard.

---

### Post by Pistolla on 2007-05-06
Sorry for the long delay but by USB is that basically your plug it in type of keyboard? If so i will try another's Keyboard (once i gets a chance). I forgots to say it's not wireless but it is a cheap keyboard. Mouse works fine by the way. I thought that maybe it was the keyboard but it works under Ubuntu and windoze.
In regards to reconfiguring the X server i am not familiar with it or what commands or whatever to do. Thanx a lot for ya'll's input
Pistolla

---

### Post by starcraft.man on 2007-05-06
> **Pistolla said:**
> Sorry for the long delay but by USB is that basically your plug it in type of keyboard? If so i will try another's Keyboard (once i gets a chance). I forgots to say it's not wireless but it is a cheap keyboard. Mouse works fine by the way. I thought that maybe it was the keyboard but it works under Ubuntu and windoze.
In regards to reconfiguring the X server i am not familiar with it or what commands or whatever to do. Thanx a lot for ya'll's input
Pistolla

Ya, USB is the flat, rectangular plug. PS/2 is the old circular plug that had pins, it was the old way :) You may wanna try one of those, ya never know.

As for how to reconfigure the xserver, just type this into terminal and follow the questions and dialogs by carefully reading them and if you don't know what to enter just click ok and keep going, pay careful attention to the keyboard section. Run it when your in Ubuntu if you can...

```
sudo dpkg-reconfigure xserver-xorg
```

Hope that helps.

---

### Post by Pistolla on 2007-05-06
Thank you very much for your reply and i have the PS/2 type, then. Hopefully i can either find a friend who has that type. In the meantime, i shall try the reconfigure part.
Again thanx for your patience
Pistolla

---

### Post by Pistolla on 2007-05-06
Starcraft i just did the reconfigure thing and it didn't work.
On an aside, it seems to have made my computer "look" a little better. Go figure.
i guess what i can do is just uninstall KDE (complete Kubuntu uninstall). my concern, then, is how much would it "bork" my settings and things since i have used some KDE stuff on Gnome
Pistolla

---

### Post by Pistolla on 2007-05-06
For the record, i went ahead and removed Kubuntu form my settings and such. Everything's fine and dandy. As it has always been, actually. i just wanted to know why my kbd didn't work under Kubuntu but methinks it has to do with a cheap kbd. It works elsewhere, so i'm fine with it. I am getting so much closer to purging windoze that it is exciting. i still have a few "bugs" to work out, some files that i may need, and work i want to keep so that's why i still keep it. i almost solely use Ubuntu because it works so well, better run, and the like. 
i definitely want to thank ya'll for your help and continue help for people that it ain't funny. Hopefully i can also contribute in the future to help further Linux's (Ubuntu in particular) cause of a better system:guitar: 
Pistolla

---

