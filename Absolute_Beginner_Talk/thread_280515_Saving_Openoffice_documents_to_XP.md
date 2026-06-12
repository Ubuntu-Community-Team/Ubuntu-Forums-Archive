---
title: "Saving Openoffice documents to XP"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by mongooseman1128 on 2006-10-19
I need to write papers for school, and I would much prefer to use Ubuntu while I'm writing these, but I'mm not able to get drivers for my printer for linux and therefore need to boot into my XP pertition in order to print the documents. I thought this wouldn't be a problem, but when I go to save a word document to my XP partition (NTFS by the way) it gives me the error message "Error Saving the document Untitled1: /media/hda1/documents and settings/Charlie/My Documents/test does not exist." I'm trying to save a document with the name test to my my documents folder in XP.

---

### Post by arochester on 2006-10-19
Linux can safely read NTFS but mostly cannot safely write to it. You should not even try and risk serious corruption.

There might be ways around the problem. A fat32 partition for both Linux and Windows might work.

Open Source programmes e.g. OpenOffice and Abiword are available for Windows

---

### Post by mongooseman1128 on 2006-10-19
okay thanks, I think what I'll do instead is just use my pen drive as a middle man. It's formatted as Fat32. Thanks.

---

### Post by sailor2001 on 2006-10-19
when I want to save things so can be seen in whatever os, I just send it to a webmail (yahoo in my case) gmail is good for this also

---

### Post by taurus on 2006-10-19
Why not try to figure out how to get your printer to work in Ubuntu!  Then, you don't have to use the "middle man" so you can open/print it under XP!!!  What is the manufacture and model of your printer?

---

### Post by Mimsy on 2006-10-19
I was just going to suggest that. Check out [www.linux-drivers.org](www.linux-drivers.org), it has very good hardware compatibility lists and links.

/Mimsy

---

### Post by Sef on 2006-10-19
For printers, [LinuxPrinting.org]("http://LinuxPrinting.org") is the best place to check if your printer will work or not.

---

### Post by mongooseman1128 on 2006-10-19
I spent a while tryint to find drivers for my printer, but it's a Lexmark X73 and as far as I've ever heard lexmark is in no hurry to work with linux, but if you know of a way to get it to work that would rock. I also tried using my pendrive as a middle man but it looks like Ubuntu doesn't want to do that either, I think it's because it's formatted as Fat16 instead of Fat32 like I thought. If I reformatted it to Fat32 do you think that would help?

---

### Post by yman on 2006-10-19
microsoft is devloping a plugin that would allow their office apps to work with open document format. so far they only came out with a plugin that allows word to read odt and save it in a word XML format.

[The article on ZDNet Asia.]("http://www.zdnetasia.com/toolkits/0,39047352,61960038-39094244p,00.htm")

[The project site on sourceforge]("http://odf-converter.sourceforge.net/") (yes, it's an open source project).

---

### Post by Sef on 2006-10-19
> microsoft is devloping a plugin that would allow their office apps to work with open document format. so far they only came out with a plugin that allows word to read odt and save it in a word XML format.


[Groklaw]("http://Groklaw.net") had a link in their news site to a site that should the plug in was basically useless. If you search the past articles you may find it.

> it's a Lexmark X73

[LinuxPrinting]("http://linuxprinting.org/show_printer.cgi?recnum=Lexmark-X73") says that you're X73 works partially, which means not very well.

---

### Post by ShadowVlican on 2006-10-19
great link

[http://linuxprinting.org/show_printer.cgi?recnum=Canon-i860](http://linuxprinting.org/show_printer.cgi?recnum=Canon-i860)

turns out my Canon i860 is a paperweight, though it works GREAT with WinXP...

---

### Post by mongooseman1128 on 2006-10-19
yeah I went to the linux printing link and I'm going to try and get my printer working (more as a learning experience than for using the printer because it's only partially functional), but right now I'm pretty confused as to how to install the PPD, so I'll probably be back later with more questions.

---

### Post by Buck2348 on 2006-11-12
This procedure worked for me without a hitch--you should be able to write to an NTFS partition in 30 minutes:  
[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=write+ntfs]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=write+ntfs")

Buck

---

