---
title: "Script or App to automate scanning/printing?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by dwp0980 on 2008-02-19
Hi,

After finally getting my Lexmark All-in-one X1130 working in Gutsy 64bit (thanks to all the people who share their knowledge of the wonderfully un-linux friendly Lexmarks), I'm now trying to push on and solve another little niggle that will move me one step closer to ditching Windows. . .

The Lexmark All-in-one has a 'one button' facility to effectively copy a colour or b/w document (it scans it and then prints it).  This works fine in Windows, but don't in Ubuntu.

Does anyone know if. . .

1)  This facility can be made to work in Ubuntu?
2) Is there a script / GUI that can be used to replicate this task, as SANE seems to work ok, as does the printing now.

Any help gratefully received.

---

### Post by marufaberlin on 2008-02-19
Do you use SANE or do you use XSANE?
Will you need a GUI?

---

### Post by marufaberlin on 2008-02-19
I just found out there is a scanimage command: [http://linux-command.5w.cz/manual/scanimage](http://linux-command.5w.cz/manual/scanimage)
Also, I think, gutenprint does what you want to do (the GIMP printing lib). Maybe you can use scanimage to scan the image to a temporary file (in the /tmp/ folder) and then use some prog to print that file.

---

### Post by dwp0980 on 2008-02-24
Thanks very much for the suggestions.  Yes it's XSANE that I'm using, but my plan is that I can just write a small script and put a shortcut to it so that I can tell my wife "use that when you want to photocopy stuff".

I've done a bit of playing, but I'm not sure where to start.  For example, when I preview/scan in XSANE GUI, I have to adjust the histogram to get the picture to look right (colour levels etc).  I cannot seem to get those settings to save.

Any ideas?

---

### Post by marufaberlin on 2008-02-25
There is a  autoadjust setting in XSANE.

---

### Post by marufaberlin on 2008-03-21
You can print images using lp. so: scan an image to a temporary location (/tmp/something) using scanimage and then print it using lp. Do't forget to delete the file! put all of this in a shell script and then run the script to photocopy.

---

### Post by marufaberlin on 2008-04-07
Please let me know if it worked.

---

### Post by dwp0980 on 2008-04-22
Sorry for not responding, I gave up in the end.  I know it's possible, but the best I could get was a quite poor copy of the original, and it was slightly shrunk.  I still have my Windows partition, so I tell my wife to boot into that if she wants to photocopy something.  I'm saving up for a new 'non-lexmark' all-in-one that has standalone copying facilities.  Any recommendations?

Thanks

---

### Post by marufaberlin on 2008-04-22
Try having a look at the canon pixma mx 300.

---

