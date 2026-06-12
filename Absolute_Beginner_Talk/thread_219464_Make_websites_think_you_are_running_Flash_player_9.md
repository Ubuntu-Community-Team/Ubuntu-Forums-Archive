---
title: "Make websites think you are running Flash player 9?"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by GStubbs43 on 2006-07-20
I know I have seen a way to do this on a thread here somewhere but I couldn't find it. I think you can just edit a file and websites will think you are running Flash 9. I am using Firefox. Does anyone know how to do this? Thanks! ;)

---

### Post by spin2cool on 2006-07-20
I've never heard of that, but you can use Wine to run firefox w/ flash 9 installed.  Sound and everything else work fine for me.

---

### Post by OU812 on 2006-07-20
Why not just install flashplayer? Get the .tar.gz from

[http://www.adobe.com/products/acrobat/readstep2.html](http://www.adobe.com/products/acrobat/readstep2.html)

Choose .tar.gz from the drop down menu. If I remember correctly it's the basic

./configure
make
make install

sequence. I got it running on zenwalk (slackware based) but haven't tried it on ubunut yet.

john

---

### Post by trent dillman on 2006-07-20
spin2cool: could you post a howto on making flash 9 work through wine, or post a link to one?

---

### Post by GStubbs43 on 2006-07-20
[QUOTE=spin2cool]I've never heard of that, but you can use Wine to run firefox w/ flash 9 installed. Sound and everything else work fine for me.[/QUOTE]
Yeah, I know you can do that but I would rather just use Firefox right on Ubuntu, instead of through Wine, it runs slow in my opinion, I have tried it before.


[QUOTE=OU812]Why not just install flashplayer? Get the .tar.gz from
[http://www.adobe.com/products/acrobat/readstep2.html](http://www.adobe.com/products/acrobat/readstep2.html)[/QUOTE]

Because that is "Download the latest version of Adobe Reader"

---

### Post by GStubbs43 on 2006-07-20
[QUOTE=trent dillman]spin2cool: could you post a howto on making flash 9 work through wine, or post a link to one?[/QUOTE]

I'm assuming it is just like shockwave on Wine, which is actually what I did before... [but here is a link on how to do that]("https://help.ubuntu.com/community/Shockwave").

---

### Post by trent dillman on 2006-07-20
[http://www.howtoforge.com/ubuntu_flash_player](http://www.howtoforge.com/ubuntu_flash_player)

I'm off to try this one...thanks for the shockwave link, too!

EDIT: Forget this link...firefox under wine? forget it...

---

### Post by OU812 on 2006-07-20
Sorry. Maybe the link got corrupted. Try

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

john

---

### Post by trent dillman on 2006-07-20
Hey, I got 9.0.16 working, using Crossover Office 5.

---

### Post by Malac on 2006-07-20
This will make most sites think you are running version 9 in Ubuntu even if you are not.
Don't forget to copy/backup the file before editing it.

Open the file ~/.mozilla/firefox/pluginreg.dat
change 
Shockwave Flash 7.0 r63:$
to
Shockwave Flash 9.0 r63:$

Hope this helps.

---

### Post by aeto on 2006-07-20
> **OU812 said:**
> Sorry. Maybe the link got corrupted. Try

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

john

..isnt the threadstarter talking about Flashplayer **9**? anyway some of the methods are working..but currently im having no sound from Linux Firefox in Youtube. Running wine version for the meantime..

---

### Post by OU812 on 2006-07-20
Maybe the version # is different in linux.

john

---

### Post by GStubbs43 on 2006-07-20
[QUOTE=Malac]This will make most sites think you are running version 9 in Ubuntu even if you are not.
Don't forget to copy/backup the file before editing it.

Open the file ~/.mozilla/firefox/pluginreg.dat
change
Shockwave Flash 7.0 r63:$
to
Shockwave Flash 9.0 r63:$

Hope this helps.[/QUOTE]

Thanks, that is exactly what I was looking for!

---

### Post by Malac on 2006-07-20
You're most welcome, glad to help.

---

