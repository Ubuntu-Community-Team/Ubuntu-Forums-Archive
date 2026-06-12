---
title: "Deleting programs"
date: 2008-09-07
forum: Apple Hardware Users
---

### Post by TeachThai on 2008-09-07
I have recently installed Ubuntu Edgy Eft version 6.10 on my 4 year old PowerBook G4. The Edgy version seems to work well on the PowerBook.

I wanted to try video editing in Linux so I installed the Kino version that came with the distribution. I wasn't satisfied with the results so I downloaded and installed Kino 1.3.0.  

I have not been happy with the new version so I would like to go back to the version that came with Ubuntu Egy Eft (6.10)

I am so new to Linux I don't know how to proceed any further. I was able to uninstall the first version of Kino with the uninstall program that came with the Ubuntu distribution but I don't know how to use that to delete Kino version 1.3.0. At this point do I somehow delete the Kino program from the Ubuntu operating system on my Powerbook G4?

Thank you for every bit of help that you can provide.

---

### Post by Qloor on 2008-09-07
In Terminal type:

```
sudo apt-get purge kino
```

---

### Post by schauerlich on 2008-09-07
Edgy is a rather old and unsupported version of Ubuntu. All of the repositories will be carrying new versions of the software, and you're bound to run into more issues similar to this. What are the specs of you Powerbook? Perhaps I can refer you to a more current OS that would work well on those specs.

---

### Post by TeachThai on 2008-09-07
Thank you for this note Qloor. I will give this a try. Just looking at it gives me hope again.

---

### Post by TeachThai on 2008-09-07
Thank you for your offer David. I have used this distribution after first starting with a Yellow Dog distribution for my PowerBook G4 and then deciding to try Ubuntu when I was not able to get any help with Yellow Dog and finding that it behaved a bit poorly in a few areas. To come to the point where I installed Festy I first tried an older version and then a newer version than Festy.  The newer version of Ubuntu did not work as well as Festy on my computer. The screens for some of the work went below the bottom of the computer. In other words, I could not see some of the "buttons" I had to click on because they were below the bottom of the monitor so I went back to Festy again. I know it is old but it installed well on my laptop.  

To give you some specs I would have to find out how to get them. When I had Mac OS-10.2 on the laptop it was easy to find the specs but I don't know how to do it in Linux yet.  Do you have any suggestions?   Actually, to give you a better view of what I want to do, I want a system with the usual Word processor and Spreadsheet. Those are the basic programs I use. If it is possible, I would like to do video editing on the computer as well.  I don't want to spend any more money on programs at this point. This is the main reason I switched from using OS-10.2 to using Linux. I didn't have any decent Word processor program or Spreadsheet program for OS 10.2.   A few years ago I did some video editing on this Mac using OS-9 so I think my Mac can do it, i.e. I think it is fast enough and has enough  memory.

---

### Post by TeachThai on 2008-09-07
Qloor,

Thank you for your help but when I typed in the command sudo apt-get purge Kino I received a reply that the command was not accepted.  Any thoughts what to try next?

---

