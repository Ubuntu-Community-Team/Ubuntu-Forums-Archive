---
title: "downloading problems"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by warchalk on 2007-03-30
Hi
I am new to Unbuntu and have diffculty in opening games like cube when downloaded.

the following message appears when I try to open 


gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again. 

cheers

---

### Post by 67GTA on 2007-03-30
Are you trying to install?

---

### Post by MikeDX on 2007-03-30
what are the files you are downloading.. do you have a url?

also, it sounds like you are selecting "view" after you double click the file and it gives you some options. Try "run in terminal" and see if you get any further.

---

### Post by warchalk on 2007-03-31
Hi Guys
trying to install cube (see below) from this Linux site [http://liflg-tracker.death-row.org/](http://liflg-tracker.death-row.org/)

cube_2005.08.29-english-2.run

where am I going wrong?

regards:(

---

### Post by Maestro23 on 2007-03-31
> **warchalk said:**
> Hi Guys
trying to install cube (see below) from this Linux site [http://liflg-tracker.death-row.org/](http://liflg-tracker.death-row.org/)

cube_2005.08.29-english-2.run

where am I going wrong?

regards:(

Open terminal:

Get to where you downloaded the file (ex: on Desktop... cd /home/username/Desktop) then

> chmod a+x cube_2005.08.29-english-2.run

sudo ./cube_2005.08.29-english-2.run

---

### Post by warchalk on 2007-03-31
Hi
thanks for te quick return

when i type cd/home/myusername/desktop into terminal and hit return, it replies 'no such file/dir  exists'

i am obviously not used to this

---

