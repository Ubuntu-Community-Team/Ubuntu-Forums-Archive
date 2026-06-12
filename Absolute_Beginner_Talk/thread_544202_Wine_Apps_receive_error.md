---
title: "Wine Apps receive error"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Zilphanael on 2007-09-06
Specifically, whenever I run an app with Wine that I haven't formally "installed" from a CD (i.e., apps I've downloaded from the net) I receive the following error:

fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
Stacktrace:

So, how do I get aforementioned DSCapture support?

---

### Post by loserboy on 2007-09-06
did you try switching to OSS just to see what it does

---

### Post by Zilphanael on 2007-09-06
> **loserboy said:**
> did you try switching to OSS just to see what it does

Uh.  Can you explain to me what "switching to OSS" entails?

The answer to your question, in case it wasn't obvious, is "no, I probably haven't, since I don't know what you mean."

---

### Post by loserboy on 2007-09-06
sorry to leave you hanging there, I posted that 1st comment and went to sleep

well it's complaining about an ALSA problem, and i have no idea how to fix that, but some things that are run in wine prefer to work with OSS drivers, even though ALSA is better.

there should be on option in winecfg under the audio tab where you can select OSS and uncheck ALSA,  it's not really the best fix but it might help you diagnose the problem

edit: i was just looking at wincfg and there are some other things you can just play around with in there to see what happens, just don't forget the original settings

---

### Post by Zilphanael on 2007-09-09
Thanks Loserboy, that eliminated the error message.  Now all I receive is:
"Stacktrace:

"
(That's the word "stacktrace" followed by a colon, then a blank line, and then returning to the input prompt)

And of course, the apps still don't run.  Any further suggestions?

---

### Post by Faud on 2007-09-09
Mnd if I ask what app you are trying to run ?
and make sure that you dont have ALSA and OSS both checked off

---

### Post by loserboy on 2007-09-10
sorry , I have no idea what stacktrace means... confirm what faud says.

I'll bet the guys at the wine IRC channel will know exactly what is wrong, they are pretty quick to answer as well

---

### Post by Zilphanael on 2007-09-10
The app I'm currently trying to run is a game called Critical Mass, but again, it occurs with every app that isn't installed from disk.  Only OSS is checked off.  Trying to find the Wine IRC channel.

---

### Post by loserboy on 2007-09-10
#winehq   on freenode


you might want to mention that you changes some audio settings to get rid of the other error

---

### Post by Zilphanael on 2007-09-10
No one has any clue what the problem is...the only suggestion I got was "update wine".  However, I originally installed it from Multiverse, and I can't get the Wine repository recognized...

I was told I had wget issues, because whenever I tried running:
sudo wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O - | sudo apt-key add -

I got:
gpg: no valid OpenPGP data found.

And whenever I tried running: 
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O - /etc/apt/sources.list.d/winehq.list

I got:
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
/etc/apt/sources.list.d/winehq.list: Unsupported scheme.

FINISHED --16:57:50--
Downloaded: 0 bytes in 0 files

---

### Post by loserboy on 2007-09-11
or you behind any uncommon security, proxy or strange firewall setup?

what version of wine do you have now?


edit: oh wait thats just showing an invalid host isnt it....  it might be better to reinstall wine, but im not really sure that would fix your issue there, have you had any problems updating or installing other things

---

### Post by Zilphanael on 2007-09-11
> **loserboy said:**
> or you behind any uncommon security, proxy or strange firewall setup?Nope, just standard Ubuntu behind a D-Link router.

> **loserboy said:**
> what version of wine do you have now?0.9.41

---

### Post by loserboy on 2007-09-11
wish I could help you, you're running a fairly recent version of wine so i dunno


you are running wine from the command line right and the error returns at the terminal?


edit: talk to the wine guys they said you could get more info by running this

```
WINEDEBUG=all wine path/of/file
```


"path/of/file" being your exe path obviously


this will force some more info about the error and maybe give the guys on IRC enough info

---

### Post by mysticmatrix on 2007-09-11
> **Zilphanael said:**
> Specifically, whenever I run an app with Wine that I haven't formally "installed" from a CD (i.e., apps I've downloaded from the net) I receive the following error:

fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
Stacktrace:

So, how do I get aforementioned DSCapture support?

fixme: refer to features yet to be implemented by Wine devolopers, which in this case is ALSA support. Remember wine is alpha software, still for devolpers to figure out what is left to be done.

About your application not running, that is a different problem. Fixme's usually don't prevent applications from running. Can you post the complete output when you run that particular program?

EDIT: Your application is a REALLY old game(designed for windows 95). So as far as I know, Wine supports Windows 98 onwards, there is little hope that you can get the game running(Wish that Wine devolopers can prove me wrong). You may try installing Windows 3.1 on DOSBox and then running your game. This would need lot of headbanging indeed. Other option would be to search for old release of Wine, somewhere near 1998, Compile it and then try installing your game.

---

### Post by loserboy on 2007-09-11
mystic you think if he ran his setup as close to 98 settings as possible that it would be backwards compatible enough?

i thought 98 was similar architecture to 95......  but that's purely an assumption


edit: wait they made a big jump there from DOS dependence didnt they

---

### Post by mysticmatrix on 2007-09-11
> **loserboy said:**
> mystic you think if he ran his setup as close to 98 settings as possible that it would be backwards compatible enough?

i thought 98 was similar architecture to 95......  but that's purely an assumption


edit: wait they made a big jump there from DOS dependence didnt they


Windows 1 to Windows 95 are all DOS based, Windows 98 to ME are all called 9x series, and Windows XP onwards are called NT series. So there is technically little difference between XP and Vista, but a large one between 95 and 98.
Also, that 98 idea might help, but I'm not so sure about it....

---

### Post by Zilphanael on 2007-09-11
> **mysticmatrix said:**
> EDIT: Your application is a REALLY old game(designed for windows 95). So as far as I know, Wine supports Windows 98 onwards, there is little hope that you can get the game running(Wish that Wine devolopers can prove me wrong). You may try installing Windows 3.1 on DOSBox and then running your game. This would need lot of headbanging indeed. Other option would be to search for old release of Wine, somewhere near 1998, Compile it and then try installing your game.

This is just one example, however.  I've also tried running custom-made and compiled C++ programs, for example, which work fine on my Windows but receive this message when trying in Wine.  I believe I could recompile them for Linux, but it would be nice to be able to do it this way.

I tried the full debug mode; about to go to IRC with it.  Thanks for the suggestion.

---

