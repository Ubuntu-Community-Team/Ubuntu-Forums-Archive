---
title: "Docx, pptx, etc."
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by hikujk123 on 2008-04-13
I have been running OOo 2.4 with wine on my ubuntu gutsy gibbon install.  I have been using wine because the OOo 2.3 metapackage refused to work properly on my computer and I could not install directly from the OOo website because of my amd64 arch.  It turns out that this OOo and wine combo runs faster then OOo for linux ever did.  Anyway, that is besides the point, so please to ask about why I am doing that.

Just answer this:  Is there a way to read/write .docx or any other Office 2007 using OOo 2.4?

---

### Post by mister_pink on 2008-04-13
docx is down as as planned for the next version I'm afraid. I've heard people say they've had some success at the moment but it sounds really quite unlikely that you'll be able to extract anything but the plain text from it.

---

### Post by hikujk123 on 2008-04-13
Anyone else have an idea or will I have to get Microsoft Word Viewer 2007 :( ?

---

### Post by mister_pink on 2008-04-13
Personnally I'd send an email to whoever sent you a file in docx format explaining why thats totally unacceptable. Have a look here [http://www.gnu.org/philosophy/no-word-attachments.html](http://www.gnu.org/philosophy/no-word-attachments.html)

Also, I'm actually quite interested, do you really think openoffice is quicker in wine than natively? There's seriously something wrong with the code if this is the case! I might have try it out at some point.

---

### Post by hikujk123 on 2008-04-13
On my computer, it is.  The OOo meta package forms weird black lines all over my screen.  When I try to install the .deb packages from OOo's website, I get an error saying that my computer has the wrong architecture (I have an amd 64 machine).  I did not have any problems when running OOo in windows on this machine (windows is now long removed).  Abiword and Gnumeric just didn't make the cut, so then it occurred to me, why not use wine?   I found it much faster to start up and everything seems to work perfectly.  :) I think it is weird, too, but hey, it works!  You should test it on your machine.

---

### Post by tango_ninja on 2008-04-13
mister_pink is correct, i'm afriad. no support for .docx files as of yet. bloody annoying. i would rather get .txt than .docx at present.

---

### Post by FuturePilot on 2008-04-13
You certainly can open .docx files in OpenOffice already. You can't save them, but you can open them. They must be opened from inside OpenOffce. Double clicking them won't work, unless you associate them with OO first. But since you're running it in Wine, that won't be possible.

---

### Post by calc on 2008-04-20
> **hikujk123 said:**
> I have been running OOo 2.4 with wine on my ubuntu gutsy gibbon install.  I have been using wine because the OOo 2.3 metapackage refused to work properly on my computer and I could not install directly from the OOo website because of my amd64 arch.  It turns out that this OOo and wine combo runs faster then OOo for linux ever did.  Anyway, that is besides the point, so please to ask about why I am doing that.

Just answer this:  Is there a way to read/write .docx or any other Office 2007 using OOo 2.4?

This already works with the Ubuntu (GoOO) version but does not with the official OpenOffice.org version until 3.0 is released.

---

### Post by rmockler on 2008-04-20
I'm running Gutsy (7.10) with Open Office 2.3, and I open .docx file regularly with perfect results.  My son initially sent them to me from his Microsoft Office 2007 thinking I wouldn't be able to open them with Ubuntu.  Surprisingly, to both of us, the joke was on him.

---

### Post by FredB on 2008-04-21
I didn't know that OOo 2.3 and 2.4 can open some docx files.

Good to know ;)

Thanks for the info.

---

### Post by aimpau on 2008-04-21
> **hikujk123 said:**
> On my computer, it is.  The OOo meta package forms weird black lines all over my screen.  When I try to install the .deb packages from OOo's website, I get an error saying that my computer has the wrong architecture (I have an amd 64 machine).  I did not have any problems when running OOo in windows on this machine (windows is now long removed).  Abiword and Gnumeric just didn't make the cut, so then it occurred to me, why not use wine?   I found it much faster to start up and everything seems to work perfectly.  :) I think it is weird, too, but hey, it works!  You should test it on your machine.

I can confirm the lines. It's really annoying and really, OO.o Impress is slow and I'm on xubuntu with Sempron 1.7Ghz 512 RAM. I've been digging the web for any linux .ppt alternative but so far...none...

---

### Post by calc on 2008-04-21
> **aimpau said:**
> I can confirm the lines. It's really annoying and really, OO.o Impress is slow and I'm on xubuntu with Sempron 1.7Ghz 512 RAM. I've been digging the web for any linux .ppt alternative but so far...none...

Is your video chipset and Xorg driver SiS also?

---

### Post by unMourned on 2008-04-28
> **calc said:**
> This already works with the Ubuntu (GoOO) version but does not with the official OpenOffice.org version until 3.0 is released.

Is that a rumor, or verified release objective?

And 3.0 is due out...when?

:)

---

### Post by calc on 2008-04-28
> **unMourned said:**
> Is that a rumor, or verified release objective?

And 3.0 is due out...when?

:)

Verified release objective. See: [Planned Features for 3.0 Release]("http://wiki.services.openoffice.org/wiki/Features#Planned_Features_for_3.0_Release"). The estimated release date is [September 2nd, 2008]("http://wiki.services.openoffice.org/wiki/OOoRelease30"). If they hit their target or are close, and I think they will, then we will have 3.0 in Ubuntu 8.10.

---

### Post by oedha on 2008-04-29
> **FuturePilot said:**
> You certainly can open .docx files in OpenOffice already. You can't save them, but you can open them. They must be opened from inside OpenOffce. Double clicking them won't work, unless you associate them with OO first. But since you're running it in Wine, that won't be possible.

i can open docx(by double click on it).....and i can save it to odt 
i am using OO-2.4 on HH

---

