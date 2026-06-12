---
title: "[SOLVED] Streamtuner version 0.99.99 - ripped files not going to desired save locatio"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-09-02
Streamtuner version 0.99.99 - ripped files not going to desired save location!

I've partitioned my drive in two, to keep OS and home apart
(see my pc specs below)

Streamtuner is putting all my ripped mp3 files into "/opt/ripped" by default
(as I'm a 1st time Linux user it took me some time to even find that location, frustrating)
and as my OS "/" partition is 10GB small it's causing me trouble!
I desperately need those ripped files to be saved in home!

I've put into the Streamtuner settings that I want to save in my home (which is a separate partition)
>edit>preferences>general>music folder (browse and put in desired save location)

but doesn't change anything, I can see it's saved the path in the little preferences window but it still keeps saving my ripped files to "/opt/ripped"

Is this a bug? Have you had the same experience?

================================================================================

other similar posts with no solution
[http://ubuntuforums.org/showthread.php?t=485975](http://ubuntuforums.org/showthread.php?t=485975)

[http://ubuntuforums.org/showthread.php?t=202687](http://ubuntuforums.org/showthread.php?t=202687)

[http://ubuntuforums.org/showthread.php?t=167785](http://ubuntuforums.org/showthread.php?t=167785)

---

### Post by Daveth on 2007-09-02
have a look at

[http://www.djlosch.com/article_How-to:_StreamRipper_and_StreamTuner_to_Download_Free_Mp3s_Legally_(for_now](http://www.djlosch.com/article_How-to:_StreamRipper_and_StreamTuner_to_Download_Free_Mp3s_Legally_(for_now))

he seems to have added a path to the record to stream option- never used it myself so cannot expand on this. Hope it helps..

---

### Post by MozartlovesUbun2 on 2007-09-02
> **Daveth said:**
> have a look at

[http://www.djlosch.com/article_How-to:_StreamRipper_and_StreamTuner_to_Download_Free_Mp3s_Legally_(for_now](http://www.djlosch.com/article_How-to:_StreamRipper_and_StreamTuner_to_Download_Free_Mp3s_Legally_(for_now))

he seems to have added a path to the record to stream option- never used it myself so cannot expand on this. Hope it helps..

hmmm, links not working, comes up with
You have an error in your SQL syntax. Check the manual that corresponds to your MySQL server version for the right syntax to use near 'limit 1' at line 3

---

### Post by djlosch on 2007-09-02
the proper link is [http://www.djlosch.com/article_How-to%3A_StreamRipper_and_StreamTuner_to_Download_Free_Mp3s_Legally_%28for_now%29]("http://www.djlosch.com/article_How-to%3A_StreamRipper_and_StreamTuner_to_Download_Free_Mp3s_Legally_%28for_now%29")

---

### Post by MozartlovesUbun2 on 2007-09-02
> **djlosch said:**
> the proper link is [http://www.djlosch.com/article_How-to%3A_StreamRipper_and_StreamTuner_to_Download_Free_Mp3s_Legally_%28for_now%29]("http://www.djlosch.com/article_How-to%3A_StreamRipper_and_StreamTuner_to_Download_Free_Mp3s_Legally_%28for_now%29")

thx djlosch :)

your link worked

basically this line needs to be changed

StreamTuner>edit>preferences>Applications
Record a stream: x-terminal-emulator -e streamripper %q -r -q -d /home/your_username/stream_mp3s

my mistake was I changed the settings in
StreamTuner>edit>preferences>General
=============================

so as this problem has been resolved does this thread need to be closed?
or how does one close a thread, is that necessary? or do the admins do that?

thanks

---

### Post by MozartlovesUbun2 on 2007-09-03
oops talking about closing this thread

hmm i got another question

how do i change the output file names?

I mean the ripped mp3 names created by default have a 0001 etc number in front of them

(i don't want any numbers in front so to make it blend in nicely with my older collection, also i need to rid of duplicates, which is easier)

how can i change that around

or is there an app of gnome or kde for batch renaming files?

thanks

---

### Post by bharani on 2007-09-06
Streamtuner not working...I mean I use rip the songs b4 but now it says unable to read the file ...this happens for all the stations in shoutcast.com...please some body help...

:guitar:

---

### Post by MozartlovesUbun2 on 2007-09-06
> **bharani said:**
> Streamtuner not working...I mean I use rip the songs b4 but now it says unable to read the file ...this happens for all the stations in shoutcast.com...please some body help...

:guitar:

can u please explain in detail what the problem is, hard to help otherwise

also depending on the problem you may wanna start a new thread

---

### Post by MozartlovesUbun2 on 2007-09-06
> **MozartlovesUbun2 said:**
> oops talking about closing this thread

hmm i got another question

how do i change the output file names?

I mean the ripped mp3 names created by default have a 0001 etc number in front of them

(i don't want any numbers in front so to make it blend in nicely with my older collection, also i need to rid of duplicates, which is easier)

how can i change that around

or is there an app of gnome or kde for batch renaming files?

thanks

THUNAR FILE MANAGER

that did the trick :)

---

### Post by bharani on 2007-09-07
Mozart,
                   A Picture is better than a thousand words...here is my problem...

---

### Post by MozartlovesUbun2 on 2007-09-07
> **bharani said:**
> Mozart,
                   A Picture is better than a thousand words...here is my problem...

hi there
ok sorry i couldn't reply any sooner been busy
i'll have more time later on in the evening

in the mean time, did u try or different radio channels
where are u ripping the files to? did u make your folder?
type your error message in google, see what it says

ok i will write back later

---

### Post by bharani on 2007-09-07
Okay I did some research looks like we need to put our hands in coding...atleast this si what i could make out after diggin forums...basically a problem with character set...

---

### Post by MozartlovesUbun2 on 2007-09-07
> **bharani said:**
> Okay I did some research looks like we need to put our hands in coding...atleast this si what i could make out after diggin forums...basically a problem with character set...

oh well its gonna take a while till i reply

my feisty went down

[http://ubuntuforums.org/showthread.php?t=545412](http://ubuntuforums.org/showthread.php?t=545412)

apparently the main boot drive is 100% full

now i cant even log in!!!
====================

phew, sweat sweat

got it working again

---

