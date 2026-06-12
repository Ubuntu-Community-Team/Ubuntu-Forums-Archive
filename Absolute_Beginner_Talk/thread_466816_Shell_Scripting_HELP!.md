---
title: "Shell Scripting HELP!"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by bamdev on 2007-06-07
hello friends ,
presently i am using ubuntu6.06.i am pretty new to linux . My question is like this

suppose i write a shell script that starts playing a song using mp3blaster .now i want to write some more commands in the script that controls the this player like its sound

NOTE:I am doing this from the Console .

example

[------------------------------------------------------------------------------------------------]
#! /bin/bash
#example.sh

mp3blaster xyz.mp3 # xyz.mp3 is in the same directory in which i am executing example.sh

# here i need a body that controls this mp3blaster plyer
# like i need to control increasing and decreasing the sound level automatically while execution is being done.
#
#
#
exit
[--------------------------------------------------------------------------------------------------]


my question is not regarding the mp3blaster . it is for any console based application.

i would appreciate greatly if someone can reply to this logically . i do have some basic idea about navigating the shell and the shell scripting in general.

thanking all in advance

---

### Post by pbw on 2007-06-07
> **bamdev said:**
> 
my question is not regarding the mp3blaster . it is for any console based application.


.. uhh, what is your question anyways?

---

### Post by justleen on 2007-06-07
it depends on the mp3blaster commandline options?
mp3blaster xyz.mps --volume 50% ?
sumtin' like that i'd guess..

im not sure if there is a command to actually change the volume itself..

---

### Post by pbw on 2007-06-07
> **justleen said:**
> it depends on the mp3blaster commandline options?


He said his question isn't even regarding mp3blaster, it's for any non-gui app. I got nothin'..

Don't mind helping once a question is asked (or made clear to me) however.

---

### Post by bamdev on 2007-06-07
hello pbw,
               let me make the question a bit more clear.
1- it is regarding any console-based app.


2 the script i have given earlier is just an EXAMPLE.


3- let me get to u in another way.
               suppose i want to write a script 
that plays the song for exactly 20 secs and quits automatically.again i dont have a direct mp3blaster command line option for the same.

explaing with the help of mentioned example .

when i write $mp3blaster xyz.mp3 
 a window of mp3blaster opens up in the shell (actually in a subshell).
i want to navigate this mp3blaster window from the parent shell that created it because 
 i want to get the  job done with the help of  script  


hope i am able to make myself a bit more clearer .

 thanking all in advance

---

### Post by hillbilly on 2007-06-07
If I get this right, you are trying to get the script to wait for user input and based on that control the application ? Something like mplayer ??
Well I don't think a shell script is powerful enough for that ! And I do not know how to it through shell scripts.

---

### Post by bamdev on 2007-06-07
hello hillbilly,
                     u are right but the only catch is that the shell should do that for me.
suppose pressing "q" quits the application then, how do i make the shell understand that it should "press q"( this is just a literal meaning )  to actually quit the application or for that matter another any other keybinding that is specific to tht application.

thanking all in advance .

---

### Post by jfinkels on 2007-06-07
> **bamdev said:**
> hello hillbilly,
                     u are right but the only catch is that the shell should do that for me.
suppose pressing "q" quits the application then, how do i make the shell understand that it should "press q"( this is just a literal meaning )  to actually quit the application or for that matter another any other keybinding that is specific to tht application.

thanking all in advance .

You may want something more than just a shell script if you want interaction like that with the program. Take a look at the ncurses library, and write your program in C or Python, for example. Here's an introduction on how to program using the ncurses library: [http://web.cs.mun.ca/~rod/ncurses/ncurses.html#introduction](http://web.cs.mun.ca/~rod/ncurses/ncurses.html#introduction)

---

### Post by bnuytten on 2007-06-07
> **bamdev said:**
> hello hillbilly,
                     u are right but the only catch is that the shell should do that for me.
suppose pressing "q" quits the application then, how do i make the shell understand that it should "press q"( this is just a literal meaning )  to actually quit the application or for that matter another any other keybinding that is specific to tht application.

thanking all in advance .

If I'm correct you will not be able to do this with a shell script. But I will answer your last question anyway. Say I telnet to the ubuntuforums webserver manually.
```

**telnet ubuntuforums.com 80**
Trying 82.211.81.186...
Connected to ubuntuforums.com.
Escape character is '^]'.
[I]GET / HTTP/1.0
[COLOR="DarkGreen"]press enter
press enter again[/COLOR]
You get some output...
[/I]
```

Now I want to do the same thing but in a script... Easy to do... Use so called "pipes". First try the command
```
**echo -e "GET / HTTP/1.0\r\n\r\n"**
```
The output of this command is exactly the input the telnet program needs. So we "redirect" or send the output from the echo program to the input of the telnet program. Because telnet kinda behaves strange... Dunno why, I used netcat (nc) in stead.
```
**echo -e "GET / HTTP/1.0\r\n\r\n" | nc ubuntuforums.com 80**
```

Good luck!

---

### Post by Funktown on 2007-06-07
To me, it looks like you want a shell script to allow you to control your music playing. If that's the case, your best bet would be to play music with MPD and control it using MPC.

There are plenty of HowTos regarding how to properly install and run MPD, so I won't go into detail here, but MPC is a console-based controller for MPD. You'd issue commands such as "mpc start", "mpd stop", etc. etc., and wouldn't have to worry about coding anything. Don't fix it if it isn't broken, eh?

A more "interactive" shell, with an ncurses interface, would be ncmpc. Both of these programs do everything you requested, provided you use MPD instead of MP3Blaster.

Hope that helps some.

---

