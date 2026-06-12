---
title: "chose wrong resolution!  How to fix?"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by linux-curious on 2007-10-23
I chose the wrong resolution and now my screen is just a jumbled flashing mess.  Short of reinstalling, how do I get back to a resolution that I know works?  There must be some sort of switch I can use at boot-up similar to Windows' "Start computer in VGA mode"   Thanks in advance for your help all.  David

---

### Post by R_U_Q_R_U on 2007-10-23
Try reading this:

Your can reconfigure x-server by running:

```
*sudo dpkg-reconfigure xfree-xserver* 
```

[B]HOWTO: Change bootup and console resolution

[http://ubuntuforums.org/showthread.php?t=258484&highlight=HOWTO%3A+Screen+resolution]("http://ubuntuforums.org/showthread.php?t=258484&highlight=HOWTO%3A+Screen+resolution")


[/B]

---

### Post by linux-curious on 2007-10-23
Okay, sorry, but I followed the instuctions at that link and they gave me the same results.  I cannot see anything when UBUNTU boots.  Also please understand that I have NO experience with linux at all, so some of the instructions are total gibberish to me.  I did manage to add vga=0x317 to my boot line, and I wound up with an error that said the mode was bad.  So far I have re-installed this system 3 times, and 3 times when I tell it I have an ACER 1913 (which is listed) it goes nuts.  If I tell it I have an LCD 1440x900, it works, but only in 1024x768 mode, which is stretched horizontally.  I don't mind re-installing again, but I would like to be able to use the full res of my screen.  Failing that I would like to be able to drop back to a lower res that is still correctly proportioned.  I have to say that as nice as UBUNTU is, it hasn't struck me as all that friendly yet.  An operating system should allow the user to back up a step if a mistake is made.  When I was selecting the screen and resolution, the test button was greyed out.  so I had to take a deep breath and step into the abyss.  Not encouraging at all.  SOmeone please tell me how to solve this problem.  And again, assume I am a total idiot when it comes to Linux.  Thanks!

---

### Post by PmDematagoda on 2007-10-23
Can you get to a terminal using Recovery Mode? If so, try this:-

```
sudo dpkg-reconfigure xserver-xorg
```

and change the resolution to one you know is safe.

---

### Post by linux-curious on 2007-10-23
Thank you.  Telling me to go into recovery mode was the best part, since I wouldn't have know to do that otherwise.  The line you gave me worked.  However, now I am having what I guess are frequency problems.  Vertical lines through the screen, looking like flowing water strems going from top to bottom. Any clues as to what setting I need to change?  Thanks for your help (all of you) so far.  David

---

### Post by PmDematagoda on 2007-10-23
Hmm, check your monitor specifications on it's manufacturer's website, find out the proper vertical frequency, then do sudo dpkg-reconfigure xserver-xorg, and enter the proper vertical frequency where it is needed.

---

