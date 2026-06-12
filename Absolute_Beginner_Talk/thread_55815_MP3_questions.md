---
title: "MP3 questions"
date: 2005-08-10
forum: Absolute Beginner Talk
---

### Post by akechi on 2005-08-10
Is there an app that can rip a whole CD as on file so i can compress it to mp3 or ogg?  i have K3b, Gnomebaker, Graveman, Grip.  and more, but none of these do what i need.  on my win machine i use burnatonce and Exact Audio Copier which both do more than what i need for whatever audio creation i want.  we need something like eac on linux.  i kinda like K3b although it limited, not as limited as Gnomebaker.  what i mean by that is,  i do alot of live sets with cue,  i dont want to split them up into seperate files, i want to keep them as one file for archives. i dont mind flac and other lossless, but i distribute these files to many dj's and most dont want to deal with flac compression.  and i find it more pleasing that i can fit more on a cd/dvd for distribution. (sorry got off the subject).  basically, i just need a app that can take the live sets off of the cd's i create and keep them as one file with or without a cue sheet, i can always create one later with gedit.  also not to bitch,  is there anything like Foobar around?  [http://www.foobar2000.org/](http://www.foobar2000.org/)   that has a great feature where if you have seperate tracks encoded as one mp3 with a cue it will read directly from the cue and play the songs as individual tracks without splitting the mp3.  and it has and archive reader, so if you compress all your audio, say zip or what have you, it will play directly from the archives.

sorry about the rant,  not trying at all to bash ubuntu or linux, i actually use ubuntu as my main pc and windows just for cd/dvd creation and games. other than that i could care less about my win box. hardly every see it unless i need to play battlefield 2.

---

### Post by KingBahamut on 2005-08-10
Hmmmm, try GooBox yet?

[http://www.gnomefiles.com/app.php?soft_id=531](http://www.gnomefiles.com/app.php?soft_id=531)

---

### Post by akechi on 2005-08-10
Not yet.   i will take a peek at that one when i get home from work, thanks!
if anymore ideas are out there keep em commin, i love testing apps!

---

### Post by akechi on 2005-08-10
Hmmmm.....looking on [www.gnomefiles.com](www.gnomefiles.com)  i found a nice app i have to try, TunaPie, im always recording streams from [www.bassdrive.com](www.bassdrive.com)   all linux needs now is a type of stream ripper with multiple scheduling (that will re-que itself when finished recording) i usually leave the app open and let it record live dj sets each week.

---

### Post by KingBahamut on 2005-08-10
Well there is an app called streamripper. Dunno if it has scheduling capability or not. 

apt-get install streamripper

---

### Post by KingBahamut on 2005-08-10
Gnome Files has a bunch of really cool stuff. Some you can apt-get others you cant. I use it as a catch all for stuff I need on occasion.

---

### Post by akechi on 2005-08-10
i've used Streamripper with Streamtuner, it works great but has no scheduling abilities, then again the only reason why there is a scheduler with foobar in windows is because a fan of it created the plugin.  the only other program in windows that does the same is winamp, and i despise that program IMHO.

I have been looking around gnome files a bit, and i like it alot!  i have another question, if i install the .deb and .tar files with dependencies and i decide i dont like what i get, is there a way to remove the app including the dependencies?  i apt-get alot of stuff and im pretty sure when i remove the app with the --purge switch (which i think only removes config files) the dependencies that were downloaded with the app stay.  which after awhile takes up unecessary space on drives, and i have no clue as to what i can and cannot remove.

thanks for the respones, as soon as i can find all the apps i need, no more windows.  well, except for my games that is ^_^

---

### Post by akechi on 2005-08-10
Hmmmm...... seems this post has already been started on cleaning useless files:  [http://www.ubuntuforums.org/showthread.php?t=55433](http://www.ubuntuforums.org/showthread.php?t=55433)

---

### Post by lunadog on 2006-03-04
Sorry about replying to this very old thread, but I am the author of Tunapie, and I would like to announce that the latest version (0.9.0) has the capability of scheduling multiple recording streams. You don't even need to keep the program open: it sends the scheduled recordings to the "at" queue so as long as the computer is on when the time is reached, it will launch streamripper to record the stream for you.

I hope people find this useful, and please submit bug reports and feature requests.

The program is available at:

[http://www.sourceforge.net/projects/tunapie](http://www.sourceforge.net/projects/tunapie)

Best wishes,

James

---

