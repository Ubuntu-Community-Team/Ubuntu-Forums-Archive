---
title: "Lost my user name and password"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by henthorn on 2007-06-14
I posted a couple of weeks ago because I lost my sound, cd burners and floppy after installing Ubuntu.  Couldn't seem to get it resolved so I took the computer to a shop.  They kept it for eight days, charged me $106  and then said it was fixed. The sound is back but the burners still don't recognize there is a disk in them.   I am using Windows because Ubuntu no longer recognizes my user name and password.  How can I again boot up Linux? Will I have to uninstall Linux and reinstall with my user name and password?  I hate having to log in everytime I boot up Linux.

---

### Post by FleetAdmiral74 on 2007-06-14
Well, its ok to hate it, but I think it is important you understand why it makes you log in every time. There is a whole plethora or security stuff with linux, i don't have time to explain now...

---

### Post by mattze on 2007-06-14
hey,
do you still have root-access to Ubuntu? Then we probably could figure something out. If not you will probably have to install it again, which isn't so bad when you use the same user name as before (if i remember it correctly, your configuration should be kept).
FleetAdmiral74 is correct, but in Feisty (maybe earlier versions too) there is an option to log in automatically.
System->Administration->Anmeldefenster[log-in screen?]->Sicherheit[safety?]->Automatische Anmeldung aktivieren[activate automatic log-in?]
As you can see I can only tell you the German names. The parts in brackets are (rough) translations that should help you figure it out.
If you decide to give Ubuntu an other try, post your dmesg output and we can see if we can try to figure out whats wrong with your burners.
so long,
mattze

---

### Post by bone43 on 2007-06-14
> **henthorn said:**
> I posted a couple of weeks ago because I lost my sound, cd burners and floppy after installing Ubuntu.  Couldn't seem to get it resolved so I took the computer to a shop.  They kept it for eight days, charged me $106  and then said it was fixed. The sound is back but the burners still don't recognize there is a disk in them.   I am using Windows because Ubuntu no longer recognizes my user name and password.  How can I again boot up Linux? Will I have to uninstall Linux and reinstall with my user name and password?  I hate having to log in everytime I boot up Linux.

Are you taking about windows and your CD burner not working or Ubuntu?

Have you lost your user name and password or do you just not like to type them in
when you boot into Ubuntu?

If its the the first one try this..

When Ubuntu boots, select Esc for the boot menu (Grub) and select recovery mode. Ubuntu will then boot w/o asking you for a password signed in as root. Type passwd USERNAME and it will reset your password.

---

### Post by henthorn on 2007-06-15
Thanks for the kind offers of help.  I am pretty ignorant about this.

Mattze: I don't have any access to Ubuntu.  It boots up and asks for my user name and password and refuses the ones I set up and there I am, no where to go. When I boot up with Xp I am greeted by a balloon in the tray with an attached message which says that I have files waiting to write to CD. The files are listed as being on my D drive which is a DVD/cd-rw drive, but there is no disk in the drive. That confuses the hell out of this computer illiterate.

Bone43: The burners did not work in either XP or Ubuntu before the shop worked on the computer.  They still don't work in Xp and I can't get into Ubuntu because of the user name/password foul up. I am using the user name and password I used when I intalled Ubuntu.  I will reboot and try your suggestion for resetting the user name and password.  I suspect that the shop somehow changed the user name and password since I had no trouble with that before it worked on the computer.

---

### Post by henthorn on 2007-06-15
I tried the ESC route after Ubuntu booted up to the user name/password screen.  Nothing happens when I press the ESC key.  I must be doing it wrong.  At what point of the boot process do I press ESC?

---

### Post by lert on 2007-06-15
I am not very clear why you insist in using the same user name? If you only want to keep your original setting, you can login  as root, then delete your original user and recreate it with the same user id, name and any other settings: your user account comes back.

---

### Post by Bachstelze on 2007-06-15
> **henthorn said:**
> I tried the ESC route after Ubuntu booted up to the user name/password screen.  Nothing happens when I press the ESC key.  I must be doing it wrong.  At what point of the boot process do I press ESC?

You need to press ESC at the very beginning of the boot process, just after the BIOS screens ant before Ubuntu starts to load. It will show up a menu like [this](http://www.psychocats.net/ubuntu/images/sudo1.gif). Choose the "recovery" option and after a while, you'll have a command prompt. To find out what the username of your normal account is, do

```
cat /etc/passwd | grep 1000
```

Which should output something like :

```
mfb:*:1000:10::/data/mfb_openbsd:/usr/local/bin/bash
```

Here, my username is *mfb*. Then, you can set a new password for your account with the *passwd* command, for example, I would do :

```
passwd mfb
```

You'll have to enter the password twice. Don't worry if you don't see little stars or anything as you type, it's normal, just type your thing and press enter.

When you're done :

```
reboot
```

and voilà :)

---

### Post by henthorn on 2007-06-15
Lert:  I can't log on to anything. It won't take my username and password.

Hymn to Life:  Thanks, but I get an unrecognized command reply whe I type in "Cat /etc/passwd l grep 1000"

---

### Post by Bachstelze on 2007-06-15
cat, not Cat ;)

ThiS iS NoT WinDOwS, CaPItALizAtIOn doeS MaTteR HerE !

---

### Post by henthorn on 2007-06-15
Touche'!  Careless of me.  I'm the kind that makes excuses.  At 87 I suffer a little mild demntia. Sorry.  However I did get to the command prompt and found my old user name don.  Then at the prompt I typed in passwd/don.  Up came the unrecognized command again. How did I screw it up this time?

---

### Post by henthorn on 2007-06-15
Oops, I see it.  No slash is needed.  I'll try again.

---

### Post by henthorn on 2007-06-15
Tried again.  Got the prompt to enter password.  Entered password.  Next prompt saoid something about password must be authenticated.  I typed in the password again and it did not go in as *symbols but as text.  Then I got the unrecognized command response. Obviously I didn't know how to authenticate the passwd. What next?

---

### Post by henthorn on 2007-06-15
Now it just replies with the unrecognized command response to my typing in "passwd don".

---

### Post by Bachstelze on 2007-06-15
What does it respond, exactly ?

---

### Post by henthorn on 2007-06-16
It responds "Unrecognized response".

---

### Post by normworthy on 2007-06-16
I have a similar problem, password not working.

When I get to Grub>passwd name
is says error 27: unrecognized command

I tryed variations and typing Grub>password name  produced
Password>
I typed name and it gave dots for each letter  (my user name and password are the same to prevent mixups)

I figured I must have it, reboot got to log in screen and it still didn't work

Help II

Norm

---

### Post by carusoswi on 2007-06-16
I am so sorry to hear that you took your computer to a shop and paid $106 in good money for someone who likely knew no more about your computer than you to go poking around and really not address any of your problems.  Much simpler, I think would have been to re-install Unbuntu and start over.  User ID and password would not have presented a problem as you can reset them to anything you like during the install process.

For that matter, you could have re-installed Windows as well.

Do report back and let us know how you make out on your efforts to repair this system.  It sounds to me as though all the problems are somehow software related.  Repair shops generally will make matters worse because they either don't care to truly listen, are manned by "techs" who don't really know that much about computers, won't spend the time necessary to fully troubleshoot the problem, jump to expensive, destructive conclusions, and tend to explore the complicated rather than the simple solutions to problems.

I have little faith in those shops.  They trade on the ignorance of the general computer user.

Caruso

---

### Post by henthorn on 2007-06-16
I agree, carusoswi, but I am also old and forgetful so I relied on a shop. I have thought about re-formatting the hard drive and starting over, but that is what I did at the start.  I re-formatted, installed XP, then installed Ubuntu and then is when I lost my sound, cd burners and floppy.  I now have my sound and floppy, but the burners still won't burn and of course I can't get into Ubuntu.  It simply won't take the command "passwd don".  I get the "error 27, unrecognized command" response and am stuck. There appears to be something in Ubuntu that won't allow you to try it again if you mess up the first time.  I mess up frequently.(G)

---

### Post by henthorn on 2007-06-16
Since my last post I went back to recovery mode and went thorugh the "cat /etc/passwd l grep 10000" routine.  This time when I got to the end I typed in "password don" instead of "passwd don" and got the prompt for my password.  I typed it in, hit the enter key and got an "error 32, password authentication" message.  How do authorize the password? (Is this progress?)

---

### Post by hoges on 2007-06-16
> **henthorn said:**
> When I boot up with Xp I am greeted by a balloon in the tray with an attached message which says that I have files waiting to write to CD. The files are listed as being on my D drive which is a DVD/cd-rw drive, but there is no disk in the drive. That confuses the hell out of this computer illiterate.  *SNIP*


On a side note, when you copy files to be burnt to cd in xp, they sit in the drive folder until they are burnt, regardless of whether there's a disk in there or not. Simply copying the files across doesn't copy them to the cd, you have to click an option to do that.

If you delete the files from the cd drive folder (they will look transparent usually), the balloon reminder will go away.

As for the password, bit, I too have no idea. Hope it all works out for you...

Cheers
Hoges

---

### Post by carusoswi on 2007-06-17
> **henthorn said:**
> I agree, carusoswi, but I am also old and forgetful so I relied on a shop. I have thought about re-formatting the hard drive and starting over, but that is what I did at the start.  I re-formatted, installed XP, then installed Ubuntu and then is when I lost my sound, cd burners and floppy.  I now have my sound and floppy, but the burners still won't burn and of course I can't get into Ubuntu.  It simply won't take the command "passwd don".  I get the "error 27, unrecognised command" response and am stuck. There appears to be something in Ubuntu that won't allow you to try it again if you mess up the first time.  I mess up frequently.(G)

So, if nothing is working, then, why not scrap everything and start from scratch.  Did your computer come with any configuration disc for the motherboard and peripherals, or just a windows restoration disc?

You need the drivers on that disc to get all your peripherals working.  Also, if your bios has a setup (I press f2 early in the boot process to access mine), go in there and poke around to make certain that your sound card and CD ROM are enabled (I've done reinstalls where mine were not, and spent a day or two thinking I had "broken" those.

Hang in there.  The solution to your problems are probably very simple - certainly solvable.  If you are as old and forgetful as you make yourself sound, then my hat that I use to cover my long bald head is off to you.

Caruso

---

### Post by henthorn on 2007-06-17
Yes I have a disc that came with the ASUS P4800D-X motherboard.  It has some drivers on it.

I also have been into BIOS.  The CD-Roms are both shown in the boot segment, but I was surprised that there was no mention of the Onboard AC97 Audio Device or  any way to enable or disable it.  The user guide shows a screen for it, but that doesn't showup for me. 

 I am thinking about starting over.  Some posts seemed to indicate that one can reinstall Ubuntu by writing over the original and that way recover the user name and password. Will that work? I hate to think about  re-installing Windows and Ubuntu although I would like to partition a little differntly than I did the first time.

---

### Post by carusoswi on 2007-06-18
Reinstalling will give you the opportunity to reset your password and ID.  You can use whatever you like.

I must have reinstalled Ubuntu 50 times before I could manage to get everything working properly.  Cannot remember the last time I reinstalled, however. . . that's a good thing.

---

### Post by Fidelio on 2007-06-18
I can't help, except with sympathy.  It's bang out of order that they took your money like that without fixing it! You should complain, really.

---

