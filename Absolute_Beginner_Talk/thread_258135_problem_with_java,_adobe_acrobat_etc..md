---
title: "problem with java, adobe acrobat etc."
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by rameez on 2006-09-15
I recently upgraded to 6.06 now when I try to install java plugin for thunderbird and Acrobat reader I get the error message 

'acroread' is not available in any software channel

The application might not support your system architecture.

Can someone please help me with this problem.

Rameez.

---

### Post by Najand on 2006-09-15
What is your system architecture?

---

### Post by rameez on 2006-09-15
Toshiba Satellite A25 S207
Pentium 4 2.6GHz

---

### Post by cacharreo on 2006-09-15
My recomendation is to use automatix to download and install these programs and much more...

---

### Post by Najand on 2006-09-15
> **cacharreo said:**
> My recomendation is to use automatix to download and install these programs and much more...

If you want to use linux using Automatix is fine, but if you want to learn howto use linux, I  recommend doing it manually.

---

### Post by rameez on 2006-09-15
already tried automatrix it just skips installing these

---

### Post by Najand on 2006-09-15
How did you install acrobat reader?

---

### Post by rameez on 2006-09-15
I did not install it, I get the same error

---

### Post by Brunellus on 2006-09-15
seems to be an issue with Automatix.  Try their forums-- [http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by Najand on 2006-09-15
To install Acroread, Click:
System -> Administration -> Software Properties
And check all unchecked options.
Then Open click:
System -> Administration -> Synaptic Software Management
And Click "Reload"
Then find "Acroread" and mark it for installation by righ clicking on it.
And then click on "Apply".

---

### Post by welshboy on 2006-09-16
If you're using Gnome, you can use the add/remove program to install Adobe Acrobat.  I'm doing so at this very moment.  Not sure why though, as it's all going to disappear next week when my new hard drive arrives! 

But hey!   I'll have all the fun of re-installing Linux again :D

welshboy

---

### Post by rameez on 2006-09-17
This is the error I am getting

---

### Post by arnieboy on 2006-09-17
> **rameez said:**
> already tried automatrix it just skips installing these

not sure AX skips anything. from the error message, I think your multiverse is not enabled. Try installing and running AX from the AX wiki in [www.getautomatix.com](www.getautomatix.com).
If you are on Gnome, you need to run AX from Applications --> System Tools 
on KDE and XFCE, it would be in Main menu -->System.
Run it from there and install all the options you need.
Recently, we have released a fix for flash and acrobat reader plugin both of which are broken in Ubuntu Dapper Multiverse (and have not been fixed as of now). Users have reported that the procedure used by AX works and they now have working flash and can open embedded pdf files in their browsers.

---

### Post by Najand on 2006-09-17
Did you check all options in "Software Properties"?

---

