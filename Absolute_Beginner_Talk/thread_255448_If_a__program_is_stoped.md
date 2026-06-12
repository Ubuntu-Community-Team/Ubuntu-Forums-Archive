---
title: "If a  program is stoped"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-09-11
My program xmmls has stoped its just lagging to my screen what to do?

---

### Post by Klaidas on 2006-09-11
Umm... Close it?
if it doesnt respond... umm, kill it? alt +f2, enter xkill, klick on it.

---

### Post by whizbaby on 2006-09-11
ps aux lists all processes with process id's, grep fetches a pattern in a stream. Type (in terminal):

[B]ps aux | grep xmm
[/B]
spot the program and remember it's process ID (it's the number following the owner's login name). Then

**kill -9 *process_id_you_remembered***

p.s. with **man *command*** you get the manual of the *command*.

---

### Post by haxer on 2006-09-11
Thx xkill i tryied worked good :)

---

### Post by haxer on 2006-09-11
Now i cant open xmmls :S why?

---

### Post by Najand on 2006-09-11
If it stops, it might be in the background... use the command
```

fg

```
to send it back to the foreground.

---

### Post by haxer on 2006-09-11
i tryied fg nothing happens just bash: fg: current: no such job

---

### Post by Najand on 2006-09-11
When executing the following command what do you get? 
```

ps aux | grep xmmls

```
Is it still there or it is already killed?

---

### Post by whizbaby on 2006-09-11
Perhaps time for **kill**ing it?

---

### Post by haxer on 2006-09-11
When i tried ps aux i got this: oem       9768  0.0  0.0   2892   812 pts/0    R+   20:44   0:00 grep xmmls

---

### Post by Najand on 2006-09-11
Hmm, seems your process has been already killed... Hmm... Do you get any errors when you want to start it in the terminal?

---

### Post by haxer on 2006-09-11
I type in xmms in the terminal window but the little marker is just blinking

---

### Post by Najand on 2006-09-11
And then what do you do? Do you terminate it using Ctrl+C or just close the terminal?

---

### Post by haxer on 2006-09-11
just closing the terminal:S why?

---

### Post by haxer on 2006-09-11
when im using ctrl+c it come a message youve probalby found a bug in xmms :P is that good deosnt sunds like it huh?

---

### Post by Najand on 2006-09-11
Hmm, maybe a computer restart solve your problem or in the worse case, removing the package and installing it again might be neccessory.

---

### Post by haxer on 2006-09-11
hmm.. ill try restart... but how do i unintall it? i know how to install just sudo apt-get install xmms :D

---

### Post by Najand on 2006-09-11
Just change the word "install" with the word "remove",,, However try to reboot first... And tell us the result...

---

### Post by haxer on 2006-09-11
Ok now i have restarted my computer and its working just fine maybe ill tell you why it hung up? I was trying to open a radio channel and then it was laggy and then it hung up and now its working but what should i do next time this is happening?

---

### Post by Najand on 2006-09-11
Sounds like a bug... Try to kill the process or terminate it if you are running it from terminal using Ctrl+C...  Then start it over.. Nothing else can be done about it.

---

### Post by haxer on 2006-09-11
ok terminate how? clickin at the X symbol isnt working :(

---

### Post by Najand on 2006-09-11
If you click on the X symbol for several times, the X environment will ask you if you want to close it by force? Then you can select yes.

---

### Post by haxer on 2006-09-11
ah okej i clicked it like 20 times and nothing happend:S

---

### Post by Najand on 2006-09-11
Is it freezed again?

---

### Post by haxer on 2006-09-11
No but for like 1 hour agao when i started this thread :P

---

### Post by Najand on 2006-09-11
Hmm, then nothing else can be done about it, except killing the process... If it fails again to load, you might push Ctrl+Alt+Backspace to restart X and see if it can load the process or not. If not you should restart your system.

---

### Post by haxer on 2006-09-11
Ok thanks for the help :)

---

### Post by whizbaby on 2006-09-11
This means that no process except your **grep** contains the string *xmmls*. You should try with a shorter string (e.g. *xmm*) and if that doesn't produce any new output it is very probable that the process is not running anymore. (Besides, what is this **xmmls**? I only know **xmms** and cannot find the other in the repositories.)

---

