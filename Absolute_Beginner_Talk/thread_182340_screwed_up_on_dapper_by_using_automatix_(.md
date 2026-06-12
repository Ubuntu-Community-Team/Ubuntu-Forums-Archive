---
title: "screwed up on dapper by using automatix :("
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by sotonin on 2006-05-25
dangit. i ran the automatix on dapper without looking and ended up cause more problems. sigh..... i ran the breezy automatix in case ur wondering :(

anyways.. mainly i was TRYING to get azureus working.. but it failed miserably and now i can NOT remove the automatix azureus... I deleted the /opt folder so its gone but the icon is still in the launcher menu. i went into alacarte menu editor to try and delete it but no avail (the delete option on righ click menu is faded and unclickable)... i tried installing from repos and then uninstalling hoping it would remove it or at least add a new link somewhere for the repo version... no cookie.... grrr

it wont go away :(

---

### Post by user1397 on 2006-05-25
[quote=sotonin]dangit. i ran the automatix on dapper without looking and ended up cause more problems. sigh..... i ran the breezy automatix in case ur wondering :(

anyways.. mainly i was TRYING to get azureus working.. but it failed miserably and now i can NOT remove the automatix azureus... I deleted the /opt folder so its gone but the icon is still in the launcher menu. i went into alacarte menu editor to try and delete it but no avail (the delete option on righ click menu is faded and unclickable)... i tried installing from repos and then uninstalling hoping it would remove it or at least add a new link somewhere for the repo version... no cookie.... grrr

it wont go away :([/quote]
deleting your /opt folder was not a good idea...
you should never delete any system folder, or any that are in /.
about azureus, ignore the icon in alacarte, just untick the box next to it to make it invisible in your applications menu.  if its not there, why let it bother you? 8)

---

### Post by Mustard on 2006-05-25
You probably want to examine your sources.list now, as automatix will have altered the repos and probably added breezy repos to your dapper sources.list.

---

### Post by cstudent on 2006-05-25
I'd be interested in seeing a copy of your sources.list. Arnieboy put error checking in a long time ago to check for Dapper. Automatix should not have run on your Dapper system. I'd be willing to bet that your problem lies more in the fact you deleted the /opt directory. If by chance Automatix did run, your sources.list would be loaded with Breezy repositories.


.

---

### Post by Mustard on 2006-05-25
[QUOTE=cstudent]I'd be interested in seeing a copy of your sources.list. Arnieboy put error checking in a long time ago to check for Dapper. Automatix should not have run on your Dapper system. I'd be willing to bet that your problem lies more in the fact you deleted the /opt directory. If by chance Automatix did run, your sources.list would be loaded with Breezy repositories.


.[/QUOTE]

Alternatively, it may have been an older version of Automatix that didn't do the check for Dapper?

---

### Post by cstudent on 2006-05-25
[QUOTE=Mustard]Alternatively, it may have been an older version of Automatix that didn't do the check for Dapper?[/QUOTE]


That's a possibility, but the user would have had to have saved it or found it somewhere else. Arnieboy and beerorkid don't keep older versions up on the website. And Arnieboy updates the download link each time he updates Automatix.


.

---

### Post by Sef on 2006-05-25
sotonin wrote > ...i ran the breezy automatix in case ur wondering. 

---

### Post by NeoGreen on 2006-05-25
Can someone explain to me in lamens terms what you are talking about?:confused:   I want to learn:) Just a quick tutorial or guide me to a link:)

---

### Post by Sef on 2006-05-25
> Can someone explain to me in lamens terms what you are talking about?

Automatix is third party software that can automatically download certain programs or codecs.  However, the orginal poster has Dapper.  However, they used Automatix for Breezy instead.  This has created problems.  Hence how does the poster undo what automatix did.  'That is the question I ask of thee?' William Shakespear

---

### Post by NeoGreen on 2006-05-26
Thank for the explanation Sef:)

---

### Post by sotonin on 2006-05-26
to answer all your questions. it did run on dapper ..... but when it asked me about the sources i chose NO to keep my original source.list i caught that and didnt wanna mess my sources up after i'd realized what id done (read some of the scrolling text and spied some breezy repositories there. i got it from the thread... hmm

---

### Post by sotonin on 2006-05-26
oh lord. ever since this thing happened my system has been acting CRAZY. it doesnt want to boot up sometimes it hangs on loading hardware drivers.... also my repo installed azureus doesnt create a system tray icon or a menu shortcut i had to make a shortcut manually. when i minimize it disappears completely. when those popups get stuck on my screen the only way to get rid of them is to killall java.

sigh... i think i screwed over my system badly :(

---

### Post by Sef on 2006-05-26
> sigh... i think i screwed over my system badly 

sometimes the best thing to do is a clean install.

---

### Post by sotonin on 2006-05-26
ha ha. yeah.. i guess so. lol

thats what i'll be doing tonight then.

:)

---

