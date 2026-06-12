---
title: "Creating a launcher in KDE"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by HelloKitty on 2008-04-09
I've seen documentation for creating a launcher in Gnome, but nothing really for KDE.

I know how to actually create the launcher.  I right click on the desktop and go > Create New > Link to Application.

However my problem rises when I'm trying to actually put in the details for the launcher.  If it was single lined I'm sure I could do it, but the code given is 3 lines...

```

       java -Dwyvern.home="/wyvern/client/wyvern" \
       -cp "wyvernclient.jar;jl020.jar;jogg-0.0.5.jar;jorbis-0.0.12.jar;mp3sp.1.5.jar;vorbisspi0.7.jar" \
       wyvern.client.Client

```

Seeing as there 3 lines but only one line of input, I'm not exactly sure how I go about formatting it.  Do I put it in verbatim?  Do I take out the slashes at the end of the lines?

If someone could answer, it would also help a lot if you could re-format it exactly how I'd use it.  Not because I'm lazy, just so I don't misinterpret what you're saying and have to ask again.

Also, I'm trying to install Wyvern using this guide...
[http://www.cabochon.com/wyvern/download#download](http://www.cabochon.com/wyvern/download#download)

---

### Post by ajgreeny on 2008-04-09
I'm not certain but I think you will need to turn the code into an executable shell script file and then use that filename as the launcher target.

---

### Post by HelloKitty on 2008-04-09
Thanks for the quick reply.

I've never created a bash script before, but I found some documentation.

The moment I saved the file with the extension .sh, Kate (the editor I'm using) colour-coded the text, presumably to highlight problems and such.  A *lot* of the text, from anything past "home=" to the end of the second line turned red.  "home=" turned green, and everything else stayed white.

When I double click it, nothing happens.

I tried messing around with the formatting.  I removed the "slashes" at the end of lines 1 and 2, to turn them into one whole line.  This did nothing for the formatting, nor the success in execution.

I'm as helpless as before, any help would greatly be appreciated.

Edit:

Ah, friendly google.  It turns out the code given on the developers site is incorrect.

While googling I saw this very thread pop up in Google.  So in case anyone is in the same predicament as I was, check this thread out..

[http://www.wyverneers.biz/showthread.php?tid=909](http://www.wyverneers.biz/showthread.php?tid=909)

---

### Post by ajgreeny on 2008-04-10
You need to change the .sh file and make it executable.  Right click it and in Properties select the executable button.  I can't remember where it is in kde but I'm sure you will find it somewhere.

---

