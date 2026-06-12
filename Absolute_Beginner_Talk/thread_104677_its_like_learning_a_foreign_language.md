---
title: "its like learning a foreign language"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by RBH on 2005-12-16
with no damn teacher!:D 

ok, i still havent figured this out yet. i cant install anything outside of the add applications. i will list my recent attempt with firefox 1.5. i downloaded the tar.gz from the mozilla website. i then tried following the instructions from here [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) and i run into the exact same problem i keep running into when trying to install ANYTHING. it errors out and says i do not have permissions to write to whatever directory. 

having been a windows user since windows 95 up to xp, and having only a few days of using linux, it is frustrating to say the least but i will not give up. i still have one box running xp, but hope to eventually move 100% to linux as so far i very much like the features and have gotten fed up with windows expensive, buggy, and bloated os. if someone could help me with the understanding that i am COMPLETELY ignorant to linux it would be appreciated. i have been reading, searching, trying, reading, researching, trying, etc etc for the last few days but i am stumped!:confused:  THANKS

---

### Post by Koybe on 2005-12-16
Windows just put the default user administrator of is own machine. Linux don't. I don't know exactly your problem but it seems that you try wrinting to a directory you don't have access too. Try running the same command as root. In ubuntu running a command as root (adminisstrator) is quite easy : juste put "sudo" before your command.

---

### Post by Qrk on 2005-12-16
Use 

```
gksudo nautilus
```

to be able to browse with root permission. Then you can move files around easily or install Firefox 1.5.

Also, its just as easy to install Firefox in your /home/user folder. There is nothing requiring Firefox 1.5 to be installed in /opt.

---

### Post by Kimm on 2005-12-16
Bear in mind: You dont wana mess with things you dont know what they are, theres a reason you are dissallowed permition to edit certain files

---

### Post by scarter on 2005-12-16
[QUOTE=RBH]i have been reading, searching, trying, reading, researching, trying, etc etc for the last few days but i am stumped!:confused:  THANKS[/QUOTE]

Join the club!  However: the latest AARP bulletin has an article on How To Keep from Getting Altzheimers.  There were several suggestions, including diet, exercise and stopping smoking, but one of the important techniques was said to be exercising your brain by trying new things - specifically:
[LIST]
[*]Learn to play the piano
[*]Learn a foreign language
[*]Install a different operating system on your computer
[/LIST]
So remember that this is more than merely installing a superior OS (and I'm convinced that it is, even though it can be a little opaque and rough around the edges). You're aiding your mental health... :p

---

### Post by teaker1s on 2005-12-16
first month is gut wrenching after that it's easier-people have grown up with windows and some expect linux to take a day or two to get used to.:rolleyes:

---

### Post by r4ik on 2005-12-16
Firefox 1.5 ?

[http://www.ubuntuforums.org/showthread.php?t=99004](http://www.ubuntuforums.org/showthread.php?t=99004)

Read around a bit there.
good luck.

---

### Post by RBH on 2005-12-16
well, i finally got it working so far. what it isn't doing is displaying some icons, pictures and such for some websites. it isnt the sites because i try them with my xp box and all shows up. it kept all my bookmarks, history and all that jazz but something got changed to make it not show pictures from some sites. any ideas?

---

### Post by Dr. Nick on 2005-12-16
[quote=RBH]well, i finally got it working so far. what it isn't doing is displaying some icons, pictures and such for some websites. it isnt the sites because i try them with my xp box and all shows up. it kept all my bookmarks, history and all that jazz but something got changed to make it not show pictures from some sites. any ideas?[/quote]

Just a wild guess, Go to Edit - Prefrences - Content and check "load images" and uncheck "from originating site only"

---

### Post by RBH on 2005-12-16
that fixed it. thanks a bunch!:D

---

### Post by Dr. Nick on 2005-12-16
Glad it worked, Dont you love it when a fix is easy :)
The originating site option is a neat idea but most sites host images on another domain so it really isnt feasable

---

### Post by Mustard on 2005-12-16
Check you preferences in firefox for what images it will display?

I vaguely recall a preference in firefox to only display images from the same server (or not).

-edit-

Doh..late to the party!  Sorry. :)

---

