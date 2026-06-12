---
title: "KMid on Gnome"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-09-04
I want to use a program: KMid. This program plays MIDI files. It is for the K-Desktop, but was available from Ubuntu/Applications/Add/Remove/Sound & Video. Even tho' this is a Gnome Desktop, I, as a novice Ubunter, thought -- Why would Ubuntu offer to download/install a program that needs a different desktop than the one I have, and moreover, why would the installer not check to determine if there was some "conflict".

So I downloaded KMid. It fires up, but when I ask it to play a MIDI file, I get the following error window:

Could not open /dev/sequencer.
Probably there is another program using it.

So, I opened a terminal, and cd /dev

next

ls

no "sequencer" word appeared in the sub-directory.

Can you please tell me whether this "sequencer" is a file, a directory an executable?

any and all of the above?

I've read and re-read:

[http://www.ubuntuforums.org/showthread.php?t=8736&highlight=Kmid](http://www.ubuntuforums.org/showthread.php?t=8736&highlight=Kmid)

and

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Advanced_Guides_by_other_Ubuntuers](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Advanced_Guides_by_other_Ubuntuers)

and doing a "Check if Already Posted" next to my subject line returned:

vBulletin Message

    Sorry - no matches. Please try some different terms. 

I've looked in How-To's and the KMid developer webpages. But I don't know nothin' 'bout 'birthin no babies, so, will the real MIDI player please stand up!

---

### Post by cwaldbieser on 2006-09-04
> **Mark_in_Hollywood said:**
> I want to use a program: KMid. This program plays MIDI files. It is for the K-Desktop, but was available from Ubuntu/Applications/Add/Remove/Sound & Video. Even tho' this is a Gnome Desktop, I, as a novice Ubunter, thought -- Why would Ubuntu offer to download/install a program that needs a different desktop than the one I have, and moreover, why would the installer not check to determine if there was some "conflict".

So I downloaded KMid. It fires up, but when I ask it to play a MIDI file, I get the following error window:

Could not open /dev/sequencer.
Probably there is another program using it.

So, I opened a terminal, and cd /dev

next

ls

no "sequencer" word appeared in the sub-directory.

Can you please tell me whether this "sequencer" is a file, a directory an executable?

any and all of the above?

I've read and re-read:

[http://www.ubuntuforums.org/showthread.php?t=8736&highlight=Kmid](http://www.ubuntuforums.org/showthread.php?t=8736&highlight=Kmid)

and

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Advanced_Guides_by_other_Ubuntuers](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Advanced_Guides_by_other_Ubuntuers)

and doing a "Check if Already Posted" next to my subject line returned:

vBulletin Message

    Sorry - no matches. Please try some different terms. 

I've looked in How-To's and the KMid developer webpages. But I don't know nothin' 'bout 'birthin no babies, so, will the real MIDI player please stand up!

You are probably best off using timidiy.  It is a command line program, but you can make it launch with one of several graphical front ends.

---

### Post by jISh on 2006-09-04
You can use KDE apps in GNOME and so forth, you just need to install the correct libraries. A lot of people like the ability to cross-install applications.

Try running killall esd in the console before running your program.
esd can re-enable afterwards.

---

### Post by Mark_in_Hollywood on 2006-09-04
OK, in a terminal I issued: 

killall esd

then I called KMid. It returned:

Could not open /dev/sequencer.
Probably there is another program using it.

Does ESD "enable" without my issuing a command? I'm lost. And to the other response, I'm trying to have karaoke, so Timidity from the command line isn't going to work. But thanks.

---

