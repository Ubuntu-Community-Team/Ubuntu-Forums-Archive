---
title: "More Wine update woes/update etc. woes....."
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by alfredeneuman on 2007-07-20
I've had wine installed ever since getting automatix. I've been using it successfully for a windows program called mp3trim pro, the executional of which is planted on the desktop. I just got a wine update, and now it doesn't work at all--when I right click the "open with wine" has disappeared.

This is the second really bad experience I've had with updates. I had Ubuntu 6.06 LTS and got an update that forced me to reformat losing all my songs (my own fault here -- I didn't have a backup). So I installed Feisty Fawn thinking I was going to outsmart the update dilemma. No such luck.

Can anybody kindly advise me? I'm not well in the ways of Ubuntu.  Thanks.

---

### Post by grishenko2000 on 2007-07-20
if you open up a terminal and type ```
wine <path to executable>
```
will the program run?

---

### Post by alfredeneuman on 2007-07-20
Nope. I got this message:  

]bash: syntax error near unexpected token `newline'

But thanks anyway.

---

### Post by grishenko2000 on 2007-07-20
you can always go back to the previous version by selecting force version from the menu in synaptic and go back to a version that worked.

---

### Post by grishenko2000 on 2007-07-20
im an idiot.

when you open up the terminal type "wine " and then repalce what was in the <> brackets with the path.
so for example it might be /home/alfredeneuman/Desktop/mp3trim.exe OR whatever it happens to be in your case.

---

### Post by alfredeneuman on 2007-07-20
I thought your ideas were excellent. But I must have done something wrong because wine still isn't right. This is what I did.

1) I force quit uninstalled the previous wine version successfully, but I noticed there was something else downloaded on the "bad" download that started it all. Is there anyway to negate that download? Being able to backtrack on a particular download would be a big help.

2) I placed this in the terminal:  

 wine/home/(my name here) desktop/mp3Trim_Pro.exe: 

    This is what I got:

 No such file or directory

 Am I typing this in correctly?

Are other people having problems with Ubuntu updates and is this generally considered a buggy part of  this linux?  Most of the time I don't have a clue what I am updating and just trust it is for the greater good.

---

### Post by grishenko2000 on 2007-07-20
try ```
wine /home/(my name here)/Desktop/mp3Trim_Pro.exe
```

notice the space between wine and /home and the capital D for Desktop

---

### Post by alfredeneuman on 2007-07-20
Yep. That brought it up. I did as you recommended with the extra space and capital D and BOOM. Thank you much. Good karma to you!

---

### Post by grishenko2000 on 2007-07-20
to save you having to type that in a terminal each time you can right click on the desktop click on create launcher and then type that command into the Command: line so then it works just like an shortcut icon a windows desktop

---

### Post by alfredeneuman on 2007-07-20
That launcher command shortcut/desktop icon is really handy. Speaking for myself, yours is exactly the kind of constructive information newcomers to linux need. Cheers.

---

