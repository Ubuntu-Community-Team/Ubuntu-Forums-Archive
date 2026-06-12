---
title: "Cannot Run Any Games on Ubuntu (Nothing to do with WINE)"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by signeddesign on 2008-01-27
Hi, I've been using Ubuntu 7.10 for the past few months on my laptop and finally just summed up the courage to move my XP Pro Desktop PC to Ubuntu 7.10 too.

Everything went well except for the usual (in my case) graphic card issues, however managed to find Envy and installed my ATI Radeon X700 Pro driver. Running Compiz-Fusion, with effects and plugins enabled.

However now each time I go to 

Application>Games

and select any game such as Tremulous, Trigger, Flightgear etc my screen instantly turns to the light brown colour background you get when entering your username and password.

I've had to manually reboot, nothing seems to work. I also tried switching compiz off and running the games doesn't work either.

I can play games on my laptop but as the screen is only 12" whereas my PC has a 19" and 256MB graphics card I would prefer to be able to play games on it instead or at least have the option.

I'm sure I need to give some output here of exactly my system spec, and what may be causing the issue, please let me know and I'll oblige as soon as possible.

---

### Post by jan quark on 2008-01-28
when you run the game via the terminal
what is the error message if you get one
just try to type the name of the game into the terminal

---

### Post by signeddesign on 2008-01-28
Hi Jan, thanks for helping out:

I do not get an error message at all, just a big massive golden-brown wallpaper - 

This is what happens when I click and run them through terminal:

**Click:**                                                             
AisleRiot Solitaire (Works)                                     
Blackjack (Works)                                                  
Cannon Smash (Works)                                         
Chess (Works)                                                       
Five Or More (Works)                                             
Flightgear (Crash - Force Reboot)                          
Four in A Row (Works)                                          
Neverput (Crash - Force Reboot)
Torcs (Crash - Manual Reboot)                          

**Terminal:**
"AisleRiot Solitaire" (Command Not Found)
"Blackjack" (Works)
"Cannon Smash" (Command Not Found)
"Chess" (Command Not Found)
"five or more" (Command Not Found)
"flightgear" (Command Not Found)
"four in a row" (Command Not Found)


Whenever I try and run OpenArena the window just closes immediately as if it's unable to run. Without crashing the PC thankfully (I guess).

I've gone through half the installed games, having to save this off line, force reboot, log back in and start again is taking a lot of time. I think it's something to do with my ATI Card or Configuration because when I run simple games such as Blackjack, 4 in a Row they're fine.

But as soon as I run something like FlightGear, Neverput, Trigger, Tremulous my PC Crashes. Maybe I can remove all the games and re-install them? I doubt that'll work, or maybe I should remove drivers for my ATI Card and re-install them?

Final point how do I find out how to run programs through terminal, in Windows it's just a matter of  launching the run dialogue and typing in winword, mspaint, photoshop, iexplore etc how do I found out commands to run programs in terminal without getting Commond Not Found.

Thanks for the help so far, I'll be back from Uni this evening so will attempt any suggestions within the next 6-8 hours.

 Otherwise I'm going to:
 
Remove  my ATI Drivers totally
Run on VESA
Uninstall 3D Games
Re-install 3D Games
Run them - If they work, then it's the driver
IF not then I'll have to .....

---

### Post by TMpBG on 2008-01-28
> Whenever I try and run OpenArena the window just closes immediately as if it's unable to run.

I have this problem with a 3d tank game(don't remember the name...)my desktop was 800X600(not shure) when I type game name in the terminal with man command...and there was a manual and i think other resolution (1024X 768?)...

MY POINT IS when i change my screen resolution  game run fine...

---

### Post by chewit on 2008-01-28
I have a problem with games, where the screen loses signal cause I think the game makes the resultion to high.

---

### Post by signeddesign on 2008-01-28
> **TMpBG said:**
> I have this problem with a 3d tank game(don't remember the name...)my desktop was 800X600(not shure) when I type game name in the terminal with man command...and there was a manual and i think other resolution (1024X 768?)...

MY POINT IS when i change my screen resolution  game run fine...

I changed the resolution from 1280*1024 (Refresh Rate 75) down to 800x600 (Refresh Rate 60)

There's been some sort of improvement that when I open games such as Flighgear I screen goes blank and within a few seconds I'm back in the log-in screen. I don't have to manually reboot. This makes me think further that it's a graphic card issue. 

OpenArena still shuts down as previously.

I've got an exam tomorrow so shall try and re-install drivers etc around Thursday if I don't get a solution here and will post an update for anyone who has a similar problem in the future, but I'm sure I'll have more questions when I get down to it.

Kind Regards

---

### Post by kesman on 2008-01-29
First download the latest version of envy and with it, install the latest version of fglrx!

Try this:
First disable all visual effects ( system -> preferences -> appearance -> visual effects tab ->NONE )
Then add this line to your /etc/X11/xorg.conf AFTER MAKING A BACKUP OF IT:
```

Section "ServerFlags"
        Option          "AIGLX" "false"
EndSection

```
To the very bottom of the file. Now restart your xorg with ctrl+alt+backspace. Now try to run a game.
You could also check your xorg log with
```

cat /var/log/Xorg.0.log | more

```
to see if there's any errors from the crashes from the games.
Do you have the latest fglrx driver? Download the latest version of envy and install the latest fglrx berfore trying anything mentioned above.

---

### Post by signeddesign on 2008-01-30
Thanks Kesman:

I tried your ideas out but they didn't work most likely because before initially posting this issue I had tried other ideas on the forums some of which involved altering the xorg file.I didn't make an original back-up (lesson learnt).

But this did point me in the right direction in terms on Envy and ATI (thank you)

1) Clean Install (Surpisingly good and crisp resolution based on previous 2 clean install before)
    This leads me to think that somehow during the install this time it picked up on something? 

2) My basic resolution was around 800x600 

3) Did NOT install ENVY

4) [http://www.hotubuntunews.com/blog_3.shtml]("http://www.hotubuntunews.com/blog_3.shtml") (Chewit, have a look at this article, this should solve your Out of Range/Sync Issue)

(After taking a backup of the Xorg file Kesman mentioned)

5) I went to Medium settings instead of Advanced at the end if you are prompted to over-wright any files type in 'startx' (without quotes and press enter)

6) This took me to a bad display informing me that I was a 'privilidge' user, hence I clicked on Quit

7) Auto Reboot and Login 

I have only fired up Tremulous, no other game, have not even played it, thought I'd put this up before I forget about this thread.

If I have any snags or issues and resolutions I shall update them hear.

Finally my advice if you are new to Ubuntu make sure all your hardware, drivers etc work fine before migrating data to your ubuntu box because this is my 3rd install.


Thanks to all who contributed to this issue. :)

Fully moved from Windows to Ubuntu after year of trying. :guitar:

---

