---
title: "help with script"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by ssaamon on 2007-10-26
Please could someone help me figure what is wrong with this script, which is more of just command.

here is my script:

```


mplayer "`locate "$1"'"



```

I believe that $1 is the value of the first parameter passed to the script. The script searches my system for the song name I specify (or partial song name). then it passes it as a parameter to mplayer.

when I try run the script in the following way:

```


$ ./playScript Strawberry_Fields


```

I get the error message:

```


./playScript: line 1: unexpected EOF while looking for matching ``'
./playScript: line 2: syntax error: unexpected end of file


```


thanks so much :)

saamon

---

### Post by llamakc on 2007-10-26
You're missing a backtick after the "$1". You have a single ' but it needs to be a matching ` backtick.

---

### Post by Paul820 on 2007-10-26
You will get a quicker answer if you ask your question in the programming section of the forum: [http://ubuntuforums.org/forumdisplay.php?f=39]("http://ubuntuforums.org/forumdisplay.php?f=39")
:)

---

