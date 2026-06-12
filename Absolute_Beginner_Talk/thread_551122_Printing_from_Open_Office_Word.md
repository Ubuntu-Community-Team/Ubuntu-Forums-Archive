---
title: "Printing from Open Office Word"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by Sabar on 2007-09-14
Ok guys, here is my problem.

While using Open office Word Processor everything works great. In fact I even like it more than windows word.  

But here is my problem I type things out have it spaced how I want it everything looks good. Before printing I even double check it under print preview. Now this is were things get a little weird.

When I print, everything comes out mashed together. In other words what was filling an entire page now is crammed into the top 4-6 inches of paper.  As far as I can tell it has to be a setting some were because My printer seems to be working with every other program.  

What I have been doing is saving in word format moving it to my documents on windows and then using word to print things out. Well this is a pain in the butt at best and counter productive at worst.

Does anybody have any ideas for this? what do I have wrong? I know in the past I had Ubuntu installed and used OO and everything came out great. don't know what I have wrong this time.

Sabar

---

### Post by por100pre1 on 2007-09-14
Close OpenOffice.org and then do this:

```
mv .openoffice.org2 .openoffice.org2_backup
```

then restart OOo. Your settings will be gone. If that doesn't work put it all back togheter

```
mv .openoffice.org2_backup .openoffice.org2
```

---

### Post by Sabar on 2007-09-14
Just type these lines into the terminal? Ok, hopfully this works.

---

### Post by Sabar on 2007-09-14
The bad news is, it didnt work. The good news is I didnt mess anything up. :) Thanks for the try though. 

Ok. so this means it isnt anything to do with my settings in OO?

---

### Post by deadgobby on 2007-09-14
What is your printer. I use to have a brother laser printer and it was hell to get to print just fine with OO.
Gobby

---

### Post by splintercellguy on 2007-09-14
It could be, perhaps margin or printer paper settings?

---

### Post by Sabar on 2007-09-14
My printer is a HP Photosmart 3210 all in one I also have a cheap lexmark that I think I used before and now thats not doing anything but shooting blank paper at me. 

I was expieramenting with a driver I found that was supposedly for my HP wonder if thats it? then again like I said it seems to work fine with things like picasa.

I have no idea what to do here. I know I have gotten better answers here so far than I got on the OO forums ;-) thanks guys

---

### Post by raycosm on 2007-09-14
What I would do instead of exporting to .doc, I would export it as a .pdf, then print that .pdf file out in Windows. It should look fine when you export it as a .pdf, and then it should print exactly as shown in Windows, with the exception that there may be a page marking.

[IMG]http://img116.imageshack.us/img116/5640/openofficeorgwriterlu0.png[/IMG]

In case ya didn't know where the print to pdf button was.

---

### Post by Sabar on 2007-09-15
Actually I am already using windows to print my documents with. I just have OO save my files in windows format. however I am looking for a way so I dont have to shut down and switch to XP everytime I wish to print something out.

---

### Post by mlentink on 2007-09-15
What driver are you using for that HP? You can check this out in System>Administration>Printers

Edit: check out: [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

---

### Post by armandh on 2007-09-15
try exporting as pdf and printing the pdf in ubuntu
if the pdf looks good and the printed pdf looks good 
see if saving in another format [rtf] has the same problem.
I have a similar problem no drivers for a dds-32
[the best I could do for xp were win2k beta drivers]

---

