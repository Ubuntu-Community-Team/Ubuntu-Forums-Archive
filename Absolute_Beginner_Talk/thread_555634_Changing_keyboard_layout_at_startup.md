---
title: "Changing keyboard layout at startup"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by Ranulfo on 2007-09-20
Good day... 

I've been using ubuntu for tree days now, and have this question....

I use the [Colemak keyboard layout]("http://www.colemak.com"), which is currently not supported on ubuntu to this date.

I downloaded the installation files and followed the instructions [here]("http://colemak.com/Unix") and everything seems to work perfect, except for the little detail that I have to execute this commands every time I start ubuntu.

[INDENT]
 cd Colemak/colemak-1.0/
setxkbmap us; xmodmap xmodmap/xmodmap.colemak && xset r 66
[/INDENT]

And the save session options doesn't seem to save this command.

My question is, Is there any way to automatically execute this commands at startup, or even before, so that I can even type my user name and password using the colemak layout?

It's just a little problem since I can also type in Qwerty, but solving it would makel my experience much better.

By the way, sorry for the bad English...

---

### Post by mridkash on 2007-09-20
You can try putting these commands in a bash script and then launch that script on startup. 

Reply back if you dont know how to do it.

---

### Post by Ranulfo on 2007-09-20
Thanks for your answer....

Ok... so I created this Script... (a friend of mine helped me to do it by im, but he doesn't use ubuntu.:-?

Its a file called 'colemak.sh' in my user carpet. (/home/ranulfo/)

[INDENT]!#/bin/bash
cd Colemak/colemak-1.0/
setxkbmap us; xmodmap xmodmap/xmodmap.colemak && xset r 66[/INDENT]

now... if this is ok, how do I get it to run on startup :confused:

---

### Post by mridkash on 2007-09-20
Hi,
PLease see that the first line of the script is 

#!/bin/bash 

rather than !#/bin/bash

Now, to run this script at startup try adding it to the startup list.

Go to System>Prefrences>Sessions
You see the startup programs tab, click on new button and enter a name.
In the command box, browse to the script file and press ok.

It might work this way, though I admit I've not tried running scripts at startup.

I dont know well but there are other ways to run startup scripts, like putting file in rc0 folder or something. I'm not clear about this.

Regards

---

