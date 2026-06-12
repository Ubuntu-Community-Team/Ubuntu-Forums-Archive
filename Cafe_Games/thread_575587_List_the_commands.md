---
title: "List the commands"
date: 2007-10-14
forum: Cafe Games
---

### Post by ashvala on 2007-10-14
A thread game where you have to just write a bash command

Ill start: ls

---

### Post by Lord Illidan on 2007-10-14
echo hello
EDIT : If someone feels the urge to write a dangerous command like rm, please do say that it's dangerous beforehand...not after someone wrecks his/her system.

---

### Post by Tyche on 2007-10-14
man [just about every name I can think of, and many I can't]  :-)

---

### Post by yabbadabbadont on 2007-10-14
```
    NextPage=$(cat $NextPage.html |\
               grep "page[1-9]" |\
               grep '/">next' |\
               sed "s:^.*/$Category/$Name/::" |\
               sed 's:/">.*$::')

```
From a bash script of mine.  ;)

---

### Post by FuturePilot on 2007-10-15
```
while true; do sleep $(($RANDOM/5000)) && beep -f $((RANDOM/10)) -l $(($RANDOM/100)) ; done
```
If you have the program beep installed this will make your computer randomly beep in different tones.:lolflag:
(press Ctrl+C to stop the madness :lol:)

---

### Post by yabbadabbadont on 2007-10-15
> **FuturePilot said:**
> ```
while true; do sleep $(($RANDOM/5000)) && beep -f $((RANDOM/10)) -l $(($RANDOM/100)) ; done
```
If you have the program beep installed this will make your computer randomly beep in different tones.:lolflag:
(press Ctrl+C to stop the madness :lol:)

I used to do something similar to other users of a Unix system on which I was root.  :twisted:

(their text used to randomly change colors too :lol:)

---

### Post by santiagoward2000 on 2007-10-15
cd /ubuntuforums/communitycafegames

---

### Post by FuturePilot on 2007-10-15
> **yabbadabbadont said:**
> I used to do something similar to other users of a Unix system on which I was root.  :twisted:

(their text used to randomly change colors too :lol:)

Hahaha, lol:lolflag:

---

### Post by xyz on 2007-10-15
I found these [H E R E]("http://frankmash.blogspot.com/2006/03/linux-commands-funny-linux-commands.html")

but they don't work for me. If someone can tell me why...Maybe they will for you.

> 
% cat "food in cans"
cat: can't open food in cans

% nice man woman
No manual entry for woman.

% "How would you rate Quayle's incompetence?
Unmatched ".

% Unmatched ".
Unmatched ".

% [Where is Jimmy Hoffa?
Missing ].

% ^How did the sex change operation go?^
Modifier failed.

% If I had a ( for every $ the Congress spent, what would I have?
Too many ('s.

% make love
Make: Don't know how to make love. Stop.

% sleep with me
bad character

% got a light?
No match.

% man: why did you get a divorce?
man:: Too many arguments.

% !:say, what is saccharine?
Bad substitute.

% %blow
%blow: No such job.

% \(-
(-: Command not found.

$ PATH=pretending! /usr/ucb/which sense
no sense in pretending!

$ drink matter
matter: cannot create

---

### Post by FuturePilot on 2007-10-15
They don't work for me either. :confused:

Here's my command 
cat

---

### Post by yabbadabbadont on 2007-10-15
@xyz & FuturePilot: I think that you have to be using the C shell (csh) in order to get that output.

```
find /media/music -type f \( -name "*mp3" -o -name "*ogg" \) -print0 | xargs -0 mv -t /media/removable/music/lossy 
```

---

### Post by -grubby on 2007-10-15
dir

---

### Post by FranMichaels on 2007-10-17
I use this one all the time

```

history

```

Lists your previous entered commands, with a number on the left.
Let's say this came up

```

414  cd audacious-plugins.hg/

```

To execute that again
type
```

!414

```

Will I get in trouble if I mention another command :razz:

grep

try this

```

history | grep cd

```

It will return every line with 'cd' in it.

I use these two commands all the time, saves on typing!

:KS

---

### Post by init1 on 2007-10-18
kill :twisted:

---

### Post by lespaul_rentals on 2007-10-19
```
killall <name of application>
```

Kills the application and eliminates it from memory.

---

### Post by yabbadabbadont on 2007-10-19
```
export LESSHISTFILE="-"
unset HISTFILE

```
Stops the less utility (first line) and the bash shell (second) from saving any command history files.  I have those lines in my ~/.bashrc file.

---

### Post by Overbyte on 2007-10-20
Of course, everyone's favorite exercise!
```
$ cat>fibonacci
# Overbyte is really geeky, don't date him
echo Enter a number:
read num
x=0
cur=1
prev=0
temp=0

while [ x -le num ]
do
	echo -n prev
	temp=cur
	let cur=cur+prev
	prev=temp
done
echo

<Press Enter then CTRL-D>

$chmod +x fibonacci
$fibonacci
Enter a number: 5
0 1 1 2 3

$
```

To get the % jokes you need to go to the C shell :)
```
$ csh
% make love
make: Don't know how to make love. Stop.
% exit
$ echo Now back to bash
Now back to bash
$

```

Don't know if that script works, made it up quickly in Notepad, but you get the idea :D
Just my 2 cents :popcorn:

---

### Post by runemaste644 on 2007-10-20
```
xkill
```
Gives you a skull and crossbones cursor and allows you to kill a window

---

### Post by rocknrolf77 on 2007-10-20
> **FuturePilot said:**
> ```
while true; do sleep $(($RANDOM/5000)) && beep -f $((RANDOM/10)) -l $(($RANDOM/100)) ; done
```
If you have the program beep installed this will make your computer randomly beep in different tones.:lolflag:
(press Ctrl+C to stop the madness :lol:)

Why do I get the feeling I'm playing an old sierra game :)


```
sudo fdisk -l
``` 

For viewing you partitions

---

### Post by koenn on 2007-10-20
> **yabbadabbadont said:**
> I used to do something similar to other users of a Unix system on which I was root.  :twisted:

(their text used to randomly change colors too :lol:)
sysadmins from hell !

----
```
sudo -i   
```
become root, get rid of the endless sudo's when you need to run multiple commands as root

---

### Post by xyz on 2007-10-21
```
shred -fuzv file_whatever
```
...when you really want to delete something.

---

### Post by yabbadabbadont on 2007-10-21
> **xyz said:**
> ```
shred -fuzv file_whatever
```
...when you really want to delete something.

Not really.  Read the warnings on the author's website for shred, wipe, and similar utilities.  With the advent of journaling filesystems and hard drives that do automatic sector relocation, short of physical destruction of the media, there really isn't any way to eliminate all traces from a determined attacker.  However, since you probably don't want to destroy your drive, a reasonably secure way of using shred (and other similar utilities) is to use it on the device containing the filesystem in order to wipe the entire filesystem.  (/dev/hda1 for example)

---

### Post by -grubby on 2007-10-21
> **FuturePilot said:**
> ```
while true; do sleep $(($RANDOM/5000)) && beep -f $((RANDOM/10)) -l $(($RANDOM/100)) ; done
```
If you have the program beep installed this will make your computer randomly beep in different tones.:lolflag:
(press Ctrl+C to stop the madness :lol:)

I didn't know my system good make this kind of noise

---

### Post by xyz on 2007-10-22
> **yabbadabbadont said:**
> Not really.  Read the warnings on the author's website for shred, wipe, and similar utilities.  With the advent of journaling filesystems and hard drives that do automatic sector relocation, short of physical destruction of the media, there really isn't any way to eliminate all traces from a determined attacker.  However, since you probably don't want to destroy your drive, a reasonably secure way of using shred (and other similar utilities) is to use it on the device containing the filesystem in order to wipe the entire filesystem.  (/dev/hda1 for example)

You're right.
I don't use shred to wipe drives. Only as a 'delete' tool.

---

### Post by Christmas on 2007-10-22
```
 echo -en "Viva\f"; sleep 1; echo -en "Pink\f"; sleep 1; echo -en "Floyd\f"; sleep 1; echo -en ":)\n"
```

---

### Post by FuturePilot on 2007-10-22
> **Christmas said:**
> ```
 echo -en "Viva\f"; sleep 1; echo -en "Pink\f"; sleep 1; echo -en "Floyd\f"; sleep 1; echo -en ":)\n"
```

What does this do?

---

### Post by yabbadabbadont on 2007-10-23
> **FuturePilot said:**
> What does this do?

```
/home/daffy $ echo -en "Viva\f"; sleep 1; echo -en "Pink\f"; sleep 1; echo -en "Floyd\f"; sleep 1; echo -en ":)\n"
Viva
    Pink
        Floyd
             :)

```
;)

---

### Post by FuturePilot on 2007-10-23
```
Viva
    Pink
        Floyd
             :)

```
:lolflag:

---

### Post by init1 on 2007-10-23
> **FuturePilot said:**
> ```
while true; do sleep $(($RANDOM/5000)) && beep -f $((RANDOM/10)) -l $(($RANDOM/100)) ; done
```
If you have the program beep installed this will make your computer randomly beep in different tones.:lolflag:
(press Ctrl+C to stop the madness :lol:)
That's amazing

---

### Post by Wiebelhaus on 2007-10-23
sudo apt-get wtf this dude is talking about?

---

### Post by nikoPSK on 2007-12-08
> **xyz said:**
> I found these [H E R E]("http://frankmash.blogspot.com/2006/03/linux-commands-funny-linux-commands.html")

but they don't work for me. If someone can tell me why...Maybe they will for you.

I like the  % %blow command. Wit, theres espeak...

espeak "lkf;rjtaebrjkazmyassssr'bl;jtljtrlsykj"

---

