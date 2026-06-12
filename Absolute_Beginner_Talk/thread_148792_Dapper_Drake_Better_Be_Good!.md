---
title: "Dapper Drake Better Be Good!"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-03-22
I have to admit that even though I love ubuntu, there are always unexplainable things and weird things that happen that I woudn't know how to fix.  Windows XP didn't really have those problems (no, I'm not working for gates;) ) Well anyway I really hope Dapper Drake is more compatible/pre-installed with more software so I can have a life instead of always solving a problem on my box! I also gotta admit that this is an awesome community that is very helpful, but not all posts always get answered.......
By the way I have a few problems of my own such as :
How do you get programs to be up on startup?
And, how do you get your mic to work with sound recorder/audacity/skype as I have not had any success with that!](*,)

---

### Post by taurus on 2006-03-22
I am not sure what you mean by better be good when Dapper comes out in June!  Some people may have problems with it while it might run like a dream for others...  It's already running like a dream on my machine with Dapper Flight 5!  And if you have a problem and don't know how to solve it, then let's hear it!  

If you want a program to start when you log in, add it to your Sessions!!!

---

### Post by arctic on 2006-03-22
System -> Preferences ->advanced preferences ->sessions, then add the command you want to launch after logging in and give it a number (50 onwards)

---

### Post by user1397 on 2006-03-22
Thanks for the quick replies!
So does anyone know how do you get your mic to work with sound recorder/audacity/skype?

---

### Post by Brunellus on 2006-03-22
[QUOTE=erik1397]Thanks for the quick replies!
So does anyone know how do you get your mic to work with sound recorder/audacity/skype?[/QUOTE]
have you unmuted it in the volume control applet?

microphone and line-inputs are muted by default.

---

### Post by user1397 on 2006-03-22
So what's the difference between mic and line-in?

---

### Post by varunus on 2006-03-22
Well, line in and mic should be different ports on your sound card...

---

### Post by user1397 on 2006-03-22
I tried selecting both line-in and microphone, but in sound recorder i press record, say something, then stop, play, but i hear nothing!

---

### Post by Brunellus on 2006-03-22
[QUOTE=erik1397]I tried selecting both line-in and microphone, but in sound recorder i press record, say something, then stop, play, but i hear nothing![/QUOTE]
turn 'em up.

---

### Post by user1397 on 2006-03-22
They're turned up all the way!

---

### Post by celloandy on 2006-03-22
Depending on what program you're using to do the recording, the program may be trying to get sound from the OSS sound system instead of from ALSA.  Try loading the OSS emulation modules, doing something like this, at the terminal:
```
sudo modprobe snd-pcm-oss
sudo modprobe snd-mixer-oss
```
And try it again.

Andrew

---

### Post by dcstar on 2006-03-23
[QUOTE=erik1397]
......
Windows XP didn't really have those problems (no, I'm not working for gates;) ) Well anyway I really hope Dapper Drake is more compatible/pre-installed with more software so I can have a life instead of always solving a problem on my box! 
......[/QUOTE]
It is doubtful any Ubuntu distro will have more "pre-installed" packages as it is distributed on a single CD and there is a limit to what can be put on it.

The whole point of Ubuntu is to be as simple as possible, with the option of anything not on the CD being available in the repositories.

If you want a distro with more packages, there are many multi-cd Linuxes available to choose from.

---

### Post by meborc on 2006-03-23
[QUOTE=dcstar]It is doubtful any Ubuntu distro will have more "pre-installed" packages as it is distributed on a single CD and there is a limit to what can be put on it.

The whole point of Ubuntu is to be as simple as possible, with the option of anything not on the CD being available in the repositories.

If you want a distro with more packages, there are many multi-cd Linuxes available to choose from.[/QUOTE]

yeah... i know a collection of 18cd's... debian stable :mrgreen:

---

### Post by akiro.yamamoto on 2006-03-23
The funny thing is that Ubuntu actually comes with more Apps installed (free)..
than XP......

XP comes with: IE6 ,  MS Player 9 , Outlook and Wordpad.... 
My that is immpressive :roll:
Ubuntu comes with: (Drum roll Please ;) )
OpenOffice , Totem Media Player , Evolution , Firefox , CD-Burner App built in , Archiver , download Manager  , Games , CD Ripper ........
Do YOU SEE a difference ;)

---

### Post by akiro.yamamoto on 2006-03-23
meborc I LOVE your sig :)

---

### Post by meborc on 2006-03-23
[QUOTE=akiro.yamamoto]meborc I LOVE your sig :)[/QUOTE]

well :oops: I LOVE your sig too... hehe :twisted:

---

### Post by akiro.yamamoto on 2006-03-23
:oops:
:roll:

---

