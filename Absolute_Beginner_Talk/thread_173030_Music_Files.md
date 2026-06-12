---
title: "Music Files?"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by StellerD on 2006-05-09
yea im a noob i know, I just downloaded Full ubuntu onto my pc and theres a few things i dont understand.

Firstly,

How do I play music files? it says it cant read it because its of windows media player format, how do I change it?


Secondly,


how do i change the resolution?


Lastly,

Whats a Good Score for the robot game? lol

---

### Post by Rinzwind on 2006-05-09
Robots game: I never seem to be able to outrun the bots more then 2 screens :D

Regarding music: what extension do you have trouble with?
mp3? 

Do you know about the unofficial ubuntu guide?
It has a sollution for some multimedia issues here:
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

Below it there's also the install you need for dvd playback and lots of other cool programs.

Resolution:
You can do that by adding manually extra resolutions into the file /etc/X11/xorg.conf 

(command to use:
**sudo gedit /etc/X11/xorg.conf **
) 
Go to the line that has resolutions and add the ones you need.


But it depends on your screen what you can add. 

You can also add them automatically by reconfiguring with the command:

**dpkg-reconfigure xserver-xorg **

BUT this ALSO depends on wether you installed your videocard correcly.

---

