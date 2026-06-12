---
title: "MP3 bitrate displayed in Nautilus?"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by spock84 on 2006-09-26
Is there a way to have nautilus show bitrate in a separate column, like in windows explorer? I'm a bit anal about all songs in an album needing to be the same bitrate (i.e. from the same rip) and I always tag the folder with bitrate by adding it to the end of the folder name. To do that now I'll have to check all files one by one and that is very inefficient and time consuming.

Someone said I could use a program called mp3info and gave me the line:

for i in *.mp3; do mp3info -p "%f: %r KB/s \n" "$i"; done 

which I guess is a python script or something, which I don't know much about. I tried just writing it in a terminal window, but it didn't do anything. I'm thinking that it works so that I browse to an album in the terminal, execute this script and I'll get a list there showing the bitrate? If that's correct, that is not what I wanted.

Any ideas?

---

### Post by spock84 on 2006-09-26
impatient bump.. ;)

---

### Post by spock84 on 2006-09-26
No one??

---

### Post by angler on 2006-10-24
Me too! I would like to have all id3 options available as columns in nautilus if anybody knows how, or cares to drop the gnome dev peeps a line. tanks

---

### Post by paul6 on 2006-11-09
Me third

---

### Post by TherapyQuestionMark on 2006-12-03
I would also like to know how to implement this function.
Please, thanks, and much appreciated.

---

### Post by Pitxyoki on 2007-02-23
And me!

By the way, spock84, if you apt-get install mp3info, you can do that command on the terminal. It is not the same thing as having a column for each file, but it somehow does what you want.
You can add that as an alias to your ~/.bashrc.
```

alias mp3br='for i in *.mp3; do mp3info -p "%f: %r KB/s \n" "$i"; done'

```
You can put that near other aliases you might have there or at the end of the file.
After doing that and saving, type:
```
. .bashrc
```
^ notice the first dot
And then, cd to an mp3 folder and
```

$ mp3br
audio1.mp3: 192 KB/s
audio2.mp3: 192 KB/s
$

```

Anyway, I too would like to see this feature on Nautilus.

---

