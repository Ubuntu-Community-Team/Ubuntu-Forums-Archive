---
title: "[SOLVED] NEED help with GEDIT"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-09-26
Ok, so that may seem like a silly title. Who needs help figuring out a text editor like gedit?
well.....
I have this Java teacher who is on a macintosh and when I write my java programs in gedit it looks dif on his end then it does on mine. Here is how he explained it:
> 
BTW: What text editor are you using? iIt seems to have a different new line since your program comes out as one line word wrapped (I hope it is not intentional) Try to set the new line to the Windows format of (CRLF). Unix uses only LF and Mac uses only CR.

So... Anybody?? I can imagine how annoying it is and hard to follow all the syntax when it is one line and scattered about the page.

Static Void

---

### Post by Linux_Man on 2007-09-26
try using geany its in the Ubuntu repositories and its a nice text editor with syntax highlighting, and see if that helps you with it. Im not that familiar with gedit to tell you which options to change.

---

### Post by vambo on 2007-09-26
[This]("http://www.thefreecountry.com/tofrodos/index.shtml") might be worth a look. Also it's in the repos

---

### Post by Lord Illidan on 2007-09-26
Perhaps disabling Text Wrapping in Gedit Preferences might do the trick?

---

### Post by staticvoid on 2007-09-26
Hey guys, thanks a ton. I bragged to my Java professor that within 30 seconds I had two responces to my post in Ubuntu. Keep on rockin peoples technological world ya'll. I'll be checkin' out some sweet IDE's and disabling text wrap. BTW: geany is awsome!!! I love it.

Nate

---

### Post by Linux_Man on 2007-09-26
Glad you like geany, I enjoy using elinks in the bottom text terminal and surfing the 'net to look for new ideas for code and then coding at the top, has a nice geeky charm to it :)

---

### Post by Adramelech on 2007-09-26
unix2dos is the command to convert text files from unix to dos style =) but i forgot what package is this command into :(

---

### Post by vambo on 2007-09-26
> **Adramelech said:**
> unix2dos is the command to convert text files from unix to dos style =) but i forgot what package is this command into :(

See above

---

### Post by mcduck on 2007-09-26
The problem is the difference between how Windows, Unix/Linux and OSX handle changing the line.

In the time of teletypes and typewriters changing line was made in 2 steps, Carriage return to move the carriage back to the beginning of the line, and Line Fed to move to the next line. 

Windows still uses both Carriage Return & Line Feed together for newline, Unix/Linux uses just the Line Feed and OSX uses just the Carriage Return..

There are tools to convert text files between these different formats, I'm not sure if Gedit has a built-in tool for the purpose and I can't check it right now as my Ubuntu laptop is broken and I'm using OSX currently..

[http://en.wikipedia.org/wiki/Newline]("http://en.wikipedia.org/wiki/Newline")

---

### Post by staticvoid on 2007-09-27
Vambo said it: [http://www.thefreecountry.com/tofrodos/index.shtml](http://www.thefreecountry.com/tofrodos/index.shtml)

I think if you convert from unix to dos it will be ok for the osx viewers?

sv

---

### Post by hyper_ch on 2007-09-27
Also have a look at "Quanta +". It's meanwhile my favourite editor as it supports SFTP and project managment and a lot of other niefty things.

---

### Post by staticvoid on 2007-09-27
I'l check it out, but all I need is a simple editor for Java with 

1. a button to compile
2. an execute button
3. change line feed/carriage input methods (windows, mac, unix)

And Geany seems to do the job fine :)
I am just a student, so I might need something more advanced as time progresses.

Edit: actually i needed just that, man, something similiar to dream weaver, and this quanta + looks like it will do the job :D thanks for recomending it.

---

