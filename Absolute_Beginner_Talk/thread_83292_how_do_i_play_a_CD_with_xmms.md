---
title: "how do i play a CD with xmms?"
date: 2005-10-28
forum: Absolute Beginner Talk
---

### Post by fuscia on 2005-10-28
when i put a CD in, sound juicer automatically opens, ready to play. there does not seem to be any option on xmms to play the CD, nor is there anything from the right click menu on the CD icon that will allow me to open it in xmms.

---

### Post by Robgould on 2005-10-28
A guess here.  I have never actuall done this from a CD, but it works from mounted folder...should be the same.
 
Can you open the CD from file system and see the individual tracks?  If so righ click on one of the songs and you should get an open with option.
 
selcet Xmms from the list.  The beauty is that you can choose the option to do this automatically from now on.
 
Hope this helps.

---

### Post by fuscia on 2005-10-28
[QUOTE=Robgould]A guess here.  I have never actuall done this from a CD, but it works from mounted folder...should be the same.
 
Can you open the CD from file system and see the individual tracks?  If so righ click on one of the songs and you should get an open with option.
 
selcet Xmms from the list.  The beauty is that you can choose the option to do this automatically from now on.
 
Hope this helps.[/QUOTE]

close. i opened up the file system and there was an audio disc icon. but, when i clicked on it, it said "cdda:///dev/hdc" is not a valid location. so, i must have the path set up incorrectly. unfortunately, i wouldn't know how to fix it.

---

### Post by Robgould on 2005-10-28
Was the CD mounted automatically when you inserted it?  If so the path is correct.  I am on XP here are work so I can't try playing a CD to help you.  sorry.  I'm sure someone will answer you soon.  If not, I will look at home tonight.

---

### Post by fuscia on 2005-10-28
[QUOTE=Robgould]Was the CD mounted automatically when you inserted it?  If so the path is correct.  I am on XP here are work so I can't try playing a CD to help you.  sorry.  I'm sure someone will answer you soon.  If not, I will look at home tonight.[/QUOTE]

'mounted'? if that means it loaded and opened sound juicer automatically, then yes, that's what happened. i wonder why i'd be getting that error if the path is correct.

thanks for the responses, btw.

---

### Post by Robgould on 2005-10-28
yeah, that is what I mean by mounted.  In linux things are mounted to the filesystem.  Kind of a strange word, getting used to it myself.  You can mount entire other filesystems to yours.  It is neat.  I'm off track though..... how did you try to play the cd from xmms?

---

### Post by fuscia on 2005-10-28
[QUOTE=Robgould]yeah, that is what I mean by mounted.  In linux things are mounted to the filesystem.  Kind of a strange word, getting used to it myself.  You can mount entire other filesystems to yours.  It is neat.  I'm off track though..... how did you try to play the cd from xmms?[/QUOTE]

'mounted' makes it sound more dramatic than it is. i guess people who use 'rich' and 'powerful' like ketchup, are going to lean in that direction.

i just opened xmms and put the CD in, which automatically opened sound juicer, and that's as far as i got.

---

### Post by Robgould on 2005-10-28
did you right click on the top of xmms and see the menu?  If not try that.  You should get a context menu that has a lot of options.  Part of those are Open file, Open directory...that kind of thig.  Try to play that way.

---

### Post by fuscia on 2005-10-28
[QUOTE=Robgould]did you right click on the top of xmms and see the menu?  If not try that.  You should get a context menu that has a lot of options.  Part of those are Open file, Open directory...that kind of thig.  Try to play that way.[/QUOTE]

yeah, i tried that. i was surprised not to see 'open' as one of the choices. 'play file, directory and location' are all there, but they don't lead to the CD. 'play directory' lead to the cdrom, but that was as far as it got.

---

### Post by Robgould on 2005-10-28
I'm out of answers until I look at it tonight.

---

### Post by fuscia on 2005-10-28
[QUOTE=Robgould]I'm out of answers until I look at it tonight.[/QUOTE]

thanks for trying. i appreciate it.

---

### Post by fuscia on 2005-10-28
DOH! i tried to play the CD with sound juicer, in the meantime, and now i'm getting the same error described in this thread - [http://www.ubuntuforums.org/showthread.php?t=81797&highlight=cd](http://www.ubuntuforums.org/showthread.php?t=81797&highlight=cd)
that error went away after i reinstalled, but now it's back again.

---

### Post by raublekick on 2005-10-28
here's how i did it, but it may not be complete because i kinda messed with stuff that i thought would help:

1. right click on XMMS to get the menu
2. click "play location"
3. type "media/cdrom and hit enter, hopefully it will play and you'll hear sound, but i suspect it won't***

from here it's a matter of setting the preferences correctly
4. right click, go to options->preferences
5. make sure output plug-in is Alsa (i don't see a reason why it should be anything else)
6. in the input plug-ins section select CD Audio Player and click "configure"
7. if "analog" is selected then select "digital" and visa versa
8. click ok and exti all the menus, try playing the CD again (just double click a song in the playlist 

if you have sound now, then great! it might be a good idea to follow this step even if you do have it working:
9. go back into the preferences and configure the AudioCD Reader plug-in
10. click the output tab and change the Cdrom speed to your drives speed. 
NOTE!! I have no idea if this is good or bad to change, I did it and it improved the speed in XMMS.
11. if sound is still not working, change the output mode plugin


hopefully at this point it is working for you. this doesn't cover how to get CD's to automatically open in XMMS.

***alternatly select "play directory" and go to media/cdrom. also, cdrom might not be the exact name of the cdrom, but it should be cdrom, cdrom0, something of that nature.

---

### Post by fuscia on 2005-10-28
raub, i tried your suggestions. i can now get xmms to play the cd, but there is no sound. when i try to play the cd on sound juicer (the program the cd automatically opens), i get the error meassage "error playing cd. could not open resource for writing."

---

### Post by raublekick on 2005-10-28
the only suggestion i can make is that in the CD Audio Player and AudioCD Reader plug-ins, make sure either both are configured to digital, or both are configured to analog. One of those *should* work, usually digital.

---

### Post by fuscia on 2005-10-28
[QUOTE=raublekick]the only suggestion i can make is that in the CD Audio Player and AudioCD Reader plug-ins, make sure either both are configured to digital, or both are configured to analog. One of those *should* work, usually digital.[/QUOTE]

ah! both on analog did it. thanks. much appreciated.

---

### Post by raublekick on 2005-10-28
no problemo! you were the first person i've ever helped on these forums, or about linux in general. what a task i undertook!!

:)

---

### Post by fuscia on 2005-10-28
[QUOTE=raublekick]no problemo! you were the first person i've ever helped on these forums, or about linux in general. what a task i undertook!!

:)[/QUOTE]

i was your first? really? you were terrific.

---

