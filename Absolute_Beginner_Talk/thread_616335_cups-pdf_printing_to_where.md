---
title: "cups-pdf printing to where?"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by shuttleworthwannabe on 2007-11-18
I have cups-pdf configured and realised that it saves the document in user's home PDF folder. It did this the first time I printed a web page into pdf; but subsequent docs are not getting saved in the same directory. Where are they being saved?

I am in gutsy.

thanks
S

---

### Post by shuttleworthwannabe on 2007-11-18
Hey, nobody??

---

### Post by ddrichardson on 2007-11-18
Mine go to /home/username/PDF

---

### Post by shuttleworthwannabe on 2007-11-18
That is correct, and mine too goes to same folder. But the problem is with subsequent prints, no new file gets saved in addition to the 1st one created. So, I tried deleting the 1st pdf created, and created a new pdf file, well, it got saved correctly.

Now how do I get cups-pdf to save more than once in the same place??

Also the file names are a bit wiered: like "_stdin_.pdf"

How could I change this file naming? Is it possible?

S

---

### Post by ddrichardson on 2007-11-18
I don't know to be honest, have you looked at your [CUPS set up and docs]("http://localhost:631/help/")?

---

### Post by shuttleworthwannabe on 2007-11-18
yes, thanks I had a look at the page; 

Is there an alternative application that do the same and better (create pdf documents from any application: Print>to pdf creator? in Gnome-Gutsy?

thanks

---

### Post by diskotek on 2008-02-05
i think i'm having the same trouble now.
before gutsy i installed cups-pdf by myself and i can had my prints in folder "home/username/pdf"...
but now, i couldn't figured it out. 

any comment?

---

### Post by kernel tom on 2008-02-05
check you cups-pdf.conf file...

its in /etc/cups/cups-pdf.conf

the line that looks something like

Out ${HOME}/PDF

tells u where its printing

-kt

---

### Post by kernel tom on 2008-02-05
> **shuttleworthwannabe said:**
> That is correct, and mine too goes to same folder. But the problem is with subsequent prints, no new file gets saved in addition to the 1st one created. So, I tried deleting the 1st pdf created, and created a new pdf file, well, it got saved correctly.

Now how do I get cups-pdf to save more than once in the same place??

Also the file names are a bit wiered: like "_stdin_.pdf"

How could I change this file naming? Is it possible?

S

I think your problem has to do with Labeling

edit your /etc/cups/cups-pdf.conf file 
Find where it talks about LABEL
and change #Label 0
to Label 1


that should do the trick, oh and naming is always gonna be funky
-kt

---

### Post by diskotek on 2008-02-05
thank you for quick reply. unfortunatrely i found another solution :)

i configured it again from system/administraion/printing
and i just install a **new printer** (pdf_file generator)

than it worked like in previous versions and i found myself in "/home/user/PDF"

but your suggestion is great, so i can change that directory now.

note: i thought that it was coming pre-configured in gutsy (is it?).

---

### Post by kernel tom on 2008-02-05
> **diskotek said:**
> 
note: i thought that it was coming pre-configured in gutsy (is it?).

Yeah i thought so too... but the 'pre-installed' one either wasn't there or didnt work for me... i cant remember...

Also, there seem to be permission problems if you change the output folder from /home/user/pdf so if you change ur output directory and it stops working thats why...

not sure if thats been fixed yet.

-kt

---

### Post by diskotek on 2008-02-05
> **kernel tom said:**
> Also, there seem to be permission problems if you change the output folder from /home/user/pdf so if you change ur output directory and it stops working thats why...

not sure if thats been fixed yet.
-kt

hmm, i didn't tried to changed it yet. now it makes me wanna try :D

---

