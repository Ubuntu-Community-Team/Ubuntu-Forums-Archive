---
title: "Installiing Adobe Reader 8"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by graydave on 2008-04-04
I downloaded the linux version of Adobe Reader but when I try to open the file I get a message that the file cannot be read.  What do I have to do to use the reader.

---

### Post by aeiah on 2008-04-04
what is the filetype? do they provide instuctions on the site?

is there a reason why you want to use adobe reader? i thought ubuntu came with its own pdf reader?

---

### Post by StOoZ on 2008-04-04
where did you download it from? 
how did you try to install it?

---

### Post by TeoBigusGeekus on 2008-04-04
You should go to this page
[http://www.adobe.com/uk/products/acrobat/readstep2_allversions.html]("http://www.adobe.com/uk/products/acrobat/readstep2_allversions.html")
and select linux and the .deb installer. Double click the downloaded deb file and acrobat reader will be automatically installed.

---

### Post by graydave on 2008-04-04
The download was from the Adobe website and I saw no further information there.

---

### Post by logos34 on 2008-04-04
> **graydave said:**
> The download was from the Adobe website and I saw no further information there.

I think it's an .rpm.  

get the deb like they said above, or get he **acroread** pkg (if you're using mozilla browser) through synaptic (-->medibuntu repos).

Have you thought about using the linux Evince pdf reader instead?  It's a lot lighter.  Can't create pdf, but then neither can you on Adobe reader unless you go online or pay for it).  (Well, actually you can export documents as pdf, but you have to use apps like Scribus).

---

### Post by stchman on 2008-04-04
> **graydave said:**
> I downloaded the linux version of Adobe Reader but when I try to open the file I get a message that the file cannot be read.  What do I have to do to use the reader.

Adobe reader is available in the Medibuntu repos.

[http://www.stchman.com/install_adobe.html](http://www.stchman.com/install_adobe.html)

Medibuntu has Adobe reader 8 now.  I personally find using Adobe for .pdf files overkill.  THe load times are long.  Evince doe most of my pdf duties very well.  Some PDFs allow you to enter informationan so I use Adobe for those.

---

### Post by ukripper on 2008-04-04
> **stchman said:**
>   I personally find using Adobe for .pdf files overkill.  THe load times are long.  Evince doe most of my pdf duties very well.  Some PDFs allow you to enter informationan so I use Adobe for those.

You are damn right! i love Evince loads quicker too.

---

### Post by philinux on 2008-04-04
[http://www.adobe.com/products/acrobat/readstep2_allversions.html](http://www.adobe.com/products/acrobat/readstep2_allversions.html)

Select installer - deb

While i agree evince is quick there is no browser plugin.

And some recent pdf's I've needed lately have been too complicated for evince to handle.

---

### Post by logos34 on 2008-04-04
> **stchman said:**
> Adobe reader is available in the Medibuntu repos.

[http://www.stchman.com/install_adobe.html](http://www.stchman.com/install_adobe.html)

Medibuntu has Adobe reader 8 now.  I personally find using Adobe for .pdf files overkill.  THe load times are long.  Evince doe most of my pdf duties very well.  Some PDFs allow you to enter informationan so I use Adobe for those.


> Originally Posted by ukripper
You are damn right! i love Evince loads quicker too.

Good points.

---

### Post by tgalati4 on 2008-04-04
From a terminal:

>sudo apt-get install acroread

---

### Post by philinux on 2008-04-04
> **tgalati4 said:**
> From a terminal:

>sudo apt-get install acroread

Need the medibuntu repos. Ok for gutsy.

Medibuntu have a slight problem now. In Hardy it fails to install the firefox plugin. Wrong directory I think. Not major but the adobe version works out the box.

---

### Post by mbeierl on 2008-04-07
Hmmm.  Hardy 64 bit won't install acroread for me:
```

sudo apt-get install acroread
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  acroread: Depends: libldap2 but it is not installable
E: Broken packages

```
Ideas, anyone? :)

---

### Post by mrgnash on 2008-04-08
I seem to be in the same situation. Hardy 64 user here too.

---

### Post by Jose Catre-Vandis on 2008-04-22
Can anyone advise how to change the default print settings for acroread - permanently!

It defaults to "Letter" and I need "A4". Can select A4 in the print dialog, and this stick during the acroread session, but on restart it goes back to "Letter". Searched my disk but cannot find an appropriate settings file. Thanks

---

### Post by mogelijk on 2008-04-25
I have the same problem, cannot install libldap2, in Hardy AMD64.  Anyone found a solution?

---

### Post by Jose Catre-Vandis on 2008-05-02
Solution: downloaded latest version I could find, 8.1.2 from here:
[http://ardownload.adobe.com/pub/adobe/reader/unix/8.x/8.1.2/enu/AdobeReader_enu-8.1.2-1.i386.deb](http://ardownload.adobe.com/pub/adobe/reader/unix/8.x/8.1.2/enu/AdobeReader_enu-8.1.2-1.i386.deb)
Uninstalled version 7 and other acroread bits and bobs using synaptic
then installed new version using Gdebi

When looking at print settings it defaults to A4, my chosen selection for my HP printer.

HTH

---

### Post by vdobriakov on 2008-06-07
> **Jose Catre-Vandis said:**
> Can anyone advise how to change the default print settings for acroread - permanently!
It defaults to "Letter" and I need "A4".

Did you try setting the default paper size system wide?
Just edit /etc/papersize and replace 'letter' by 'A4'.

Regards,

Vladimir Dobriakov

---

