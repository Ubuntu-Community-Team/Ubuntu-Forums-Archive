---
title: "newbie questions"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by qrm on 2006-03-11
Hi!
Ive installed last version of Ubuntu and it went perfect, no problems at all. The xchat and gaim and firefox are working nicely and i can get on to internet without the need to configurate anything :D 

But as im absolute newbie to Linux and Ubuntu Ive got some questions

1) my keyboard is acting weirdly. I was able to set the  language from prefereces>keyboard to my native language, which is Estonian. But my keyboard is absolute noname and i cant figure out which one to select. Tried the generic ones but still the special letters dont come at all and the second and third ones on the numbers are all messed up. I even read how much buttons my keyboard has :p , and it was more then 105, so i guess its not generic at all.

2) my computer has frozen for 2 times already in 6 hours. Under windows it happened only when i was running one certain application, so it shouldnt be an hardware problem.

3) I know, that i can give commands to install something or configure something in the @Konsole@ and i should use sudo, but when should i use it_ what is the command to install something or unistall_ Where should i put the .gz or .run files and where should i install them. I know, that the command is @install source destination@ , but i dont understand the logic of the filetree :???: 

4) music. Yes, i love listening to music and id love to listen it in linux too :) I can hear the theme melody in the beginning , when i log in to my account, but when i try to open a mp3 file in vlc player i dont hear a thing. In the lower right corner of my desktop is next to the speaker icon a little red/white cross and when i mouseover it it says, that my master mono is muted. Tried to change things in Volume control, but it didnt solve it :neutral: 

Thats about all now :rolleyes: . Im willing to learn and love the first 6/hour experience with ubuntu, because it quite radically different from windows and strange things dont happen that often . The main reason i switched to linux were some really odd things happening without a reason. Im quite experienced windows user but after messing around in registry and trying everything and not getting somethimes even clear error messages i decided to try something, that was evolving and had quality feedback.

thanks in advance,

qrm

EDIT> thought a bit and i some more questions popped up my mind

1) do i need to install any specific gfx drivers or was it done while i installed Ubuntu_

2) what is the use for lower right hand corner_ couple of boxes in there that are empty and the trashcan. 

3) How could i minimize my firewall Firestarter to the @tray@ ?

---

### Post by Zimmer on 2006-03-11
Hello. Have you had a good look here for starters?
[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

The sound problem can be cured a couple of ways.
First try : Applications>Sound&Video>Volume control  and make sure the master volume is unmuted.
Or open a Terminal session and type  :   alsamixer 
and make sure the Master Volume is unmuted from there.
As for gfx drivers, see here...
[https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)
Hope this helps you....
Regards

---

### Post by Zelut on 2006-03-11
Well that is quite a lot of questions.  I'll see what I can answer here and hopefully it helps.

1) Your keyboard--I dont know.  I've only had to deal with English & that all auto-detects just fine :)  You might just have to keep trying on that one..

2) The freezing could be a hardware problem, even if it doesn't happen in windows.  Windows & Linux deal with hardware very differently and with different drivers.  Windows may recognize something differently than linux or visa versa.  You might be able to find error messages in your System Log.  You should be able to find that (i believe) in Applications > System Tools > System Monitor (or log)

3) If you want to add an application you can do it very easily using Synaptic (System > Admin > Synaptic).  There you can search for a program by name or keyword & it'll download & install it for you.  You should also have an Add/Remove Applications listing in your menu which will have a list of available programs for installing.  You can also manually install things but this is much easier, faster & avoids potential conflicts.

4) My first guess on your mp3 issue is that you dont have mp3 support installed.  This is due to licensing issues with mp3 and ubuntu not being able to distribute it.  If you search the forum I'm sure you'll find tips on how to add mp3 support or you can find some information [here]("https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=mp3")

5) specific graphics drivers would depend on your hardware type.  Are you using nvidia? ATI? etc?  A basic driver was installed but for advanced drivers you'd need more info about your hardware.

6) The lower-right hand corner boxes represent 'virtual-desktops'.  Test it.  Open something and then click one of those other three boxes.  Notice how it isn't displayed?  Those are 4 'virtual-desktops' where you can open additional programs.  I use this to keep things organized if I'm using a lot of programs.

4) the minimize firestarter option should be in firestarter itself.  I remember seeing a checkbox for 'minimize on close' or something.. just take a look.

---

### Post by qrm on 2006-03-11
Thanks a lot for the feedback so far. I think i was able to install my gfx-drivers :D Atleast i saw Nvidia logo ;) Ill be working on things further and post my upcoming questions here. Thx alot again:rolleyes:
And by configuring my xserver (or whatever its called :-|  ) i got the commas and other symbols OK, but the special letters, that i need in my language are dead.
And id still like to know the logic of the install command, because id like to install the only game i like to play: Enemy Territory and its not in Synaptic. And a command how to unzip thing would be nice too

one question still:

in the alsamixer dialogue i was able to figure out how to change the volume, but how do i mute or unmute things?

---

### Post by qrm on 2006-03-11
another problem i came across

Ive been following the tut [https://wiki.ubuntu.com/Wine](https://wiki.ubuntu.com/Wine) and there is, that when i want to run some exe files i have to put in my konsole "wine filename.exe" if i want to run some windows specifc programs or installers. Ive got one exe file on my desktop but i get this error: wine: cannot find 'ventrilo-2.1.4-Windows-i386.exe'
unfortunately there is no linux version of ventrilo and id like to get it running 

Edit: i figured it out, that i had to put desktop/ infront of the installer name. I got through the instalation althou the butons were all messed up. They had something like sansSherif on them, so I guess im missing some fonts?

Thanks in advance

---

### Post by Zimmer on 2006-03-12
[https://wiki.ubuntu.com/EnemyTerritory](https://wiki.ubuntu.com/EnemyTerritory)

That should help with the game,   it did for me :)

And if you get problems, there are plenty of threads (including some of mine, ) that will sort you out.
Best Regards

---

### Post by soonindallas on 2006-03-12
[QUOTE=qrm]
And by configuring my xserver (or whatever its called :-|  ) i got the commas and other symbols OK, but the special letters, that i need in my language are dead.[/QUOTE]

if reconfiguring xorg.conf did not autodetect your keyboard:

Go to system > preferences > keyboard > layout tab

there seems to be a config for estonian keyboards.  set to use it as default.

[QUOTE=qrm]And id still like to know the logic of the install command, because id like to install the only game i like to play: Enemy Territory and its not in Synaptic. And a command how to unzip thing would be nice too[/QUOTE]

look at this thread: [http://www.ubuntuforums.org/showthread.php?t=78674](http://www.ubuntuforums.org/showthread.php?t=78674)

one question still:

i[QUOTE=qrm]n the alsamixer dialogue i was able to figure out how to change the volume, but how do i mute or unmute things?[/QUOTE]

if you have the volume control applet, dragging the volume slider to the bottom mutes all sounds.

---

