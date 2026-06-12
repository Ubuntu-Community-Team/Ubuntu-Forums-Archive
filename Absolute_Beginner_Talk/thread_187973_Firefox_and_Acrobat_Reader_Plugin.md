---
title: "Firefox and Acrobat Reader Plugin"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by Young Breezy on 2006-06-03
I recently upgraded to Dapper Drake and almost everything has been going flawlessly except that when i try to open embedded pdf files in firefox nothing happens.  I have already installed the mozilla-acroread and still get a blank screen when trying to view pdfs in firefox.  Ive looked around but havent found any solutions as of yet, any help would be appreciated.

---

### Post by tonyr on 2006-06-03
I have the following packages installed:
acroread             7.0.1-0.0.ubuntu1
acroread-plugins  7.0.1-0.0.ubuntu1
mozilla-acroread  7.0.1-0.0.ubuntu1

and it works for me.  Try removing and re-installing these packages.

---

### Post by Rackerz on 2006-06-03
It's probably not the best solution but it worked for me.

Go to 

```
http://ardownload.adobe.com/pub/adobe/reader/unix/7x/7.0.5/enu/AdobeReader_enu-7.0.5-1.i386.tar.gz
```

Once that archive has been opened open up this file 'ILINXR.TAR'

Then go into the 'Browser' folder, then to the 'intellinux' folder and extract the file; ```
nppdf.so
```

Copy that file and navigate to /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/ and replace the exisiting file with the one you extracted earlier. 

Restart firefox and see if it works ;).

---

### Post by jdong on 2006-06-03
Just to be a grumpy old critic, but what do you find attractive about the Acrobat Reader Plugin? ;)


Adobe Acrobat Reader feels extremely heavy compared to the Linux PDF viewers, both in terms of CPU and RAM usage. The Firefox plugin is especially talented at using absurd amounts of RAM.


I really suggest giving the external Linux PDF viewers that are pre-installed a shot before deciding to need Acrobat Reader integrated into Firefox.

I have standalone Acrobat Reader installed on my Ubuntu system, but not the Firefox plugin. I only use it for features unsupported in the current Linux readers, such as filling out PDF forms.

---

### Post by Young Breezy on 2006-06-03
Thanks Rackerz, that worked quite well! 

And why do i want acrobat reader plugin, i guess im just used to using it and havent tried any of the linux pdf viewers, but you are very right about the ram usage, maybe i will check them out.

---

### Post by jdong on 2006-06-03
Give the Linux PDF viewers a shot, you will not be disappointed. These guys have the resource footprint of like Wordpad, eliminating the groaning and moaning that usually comes with seeing the .pdf extension :)

---

### Post by bccomm on 2006-06-05
I'll second that. Xpdf is great. However, neither bonobo (gpdf) nor mozplugger can correctly handle pdf indexes that have references to internet resources. This is because both of the wrappers pass a temporary file to the pdf viewer instead of the Internet URL. see [http://www.ldsces.org/inst_Manuals/NTStdntStdyGd34188000/Start_Here.pdf]("http://www.ldsces.org/inst_Manuals/NTStdntStdyGd34188000/Start_Here.pdf")
 for an example. 

It works with KPDF under Konqueror, though. :|

---

### Post by harfooz on 2006-06-05
There are some important reasons I choose acroread over the others:

1. Our expense reports and medical expense reimbursement plans require their .pdf forms to be completed in the .pdf, printed and signed. None of the linux .pdf readers are capable of doing that.

2. I regularly write technical presentations using the latex beamer package. Evince won't render the resulting .pdf presentations accurately, and others don't have the presentation tools done as well as acroread.

3. I occasionally have to write music using lilypond, and the fonts that music requires is better supported in acroread.

Any solution for the acroread-firefox issue yet?

Clint

---

### Post by Young Breezy on 2006-06-05
Harfooz,

Yeah, the post that Rackerz put up worked just fine for me.  If you are having similar difficulties as mine, and reinstallation of the acroread and mozilla-acroread doesnt help at all, follow his post and see if that works for you.

---

### Post by dpm on 2006-06-09
[quote=jdong]Give the Linux PDF viewers a shot, you will not be disappointed. These guys have the resource footprint of like Wordpad, eliminating the groaning and moaning that usually comes with seeing the .pdf extension :)[/quote] 
After not being able to use acroread inside tabs in Epiphany after the Dapper upgrade, I decided to use mozplugger + Evince a go. Unfortunately, this combination is quite flaky [1] on my system, and as much as I prefer Evince over Acroread, I really miss the acroread plugin for opening pdf files inside tabs.

I would try other viewers, but I'm afraid that has got more to do with mozplugger than the viewer, and plus my Dapper installation is unstable enough to start trying new things now.

In summary, I love Evince, but I think there is still some work to do in order to embed Open Source viewers within Firefox tabs, which the acroread plugin seemed to handle quite well on Breezy.

[1] a) you can clearly see the Evince instance opening before it gets "swallowed" inside the tab, b) many times (mostly with big pdfs) you end up with a frameless Evince completely outside of the browser window c) after clicking on a pdf link, opening the document and then closing it, clicking on the link a second time will not load the document.

---

### Post by Dirkomatic on 2006-06-11
Rackerz, this was perfect!  Thank you very much! I'd just like to know how in the h311 you figured that out...

---

### Post by lpf on 2006-06-12
[QUOTE=Dirkomatic]Rackerz, this was perfect!  Thank you very much! I'd just like to know how in the h311 you figured that out...[/QUOTE]
So do I :D ... works like a charm... thanks.

---

### Post by sgla1 on 2006-06-12
Thanks for the fix--it worked for me (using dapper + automatix).  Apparently there is a problem with the nppdf.so file in the .deb

AFAIK Automatix does not install acroread-plugins 7.0.1-0.0.ubuntu1.  This is necessary to interact with fillable acrobat files.  Pretty important in many businesses.  Thanks for pointing out that this has to be installed also.

---

### Post by evil_elman on 2006-06-15
Thank you! Fix works... Who comes up with these things, anyway?

---

### Post by Limulus on 2006-06-17
[QUOTE=Rackerz]nppdf.so[/QUOTE]
I went to Adobe's site and it offered me version 7.08, so I tried the nppdf.so from that and it worked, so if anyone doesn't feel like downloading the ~40 MB archive to extract it from, here's just the one file :)

[http://members.shaw.ca/Limulus/files/nppdf.so.tar.gz](http://members.shaw.ca/Limulus/files/nppdf.so.tar.gz)

Double click on it to open the Archive manager and extract it, then follow Rackerz' instructions.

**Update:** Similar to how James R. Philips (below) did it, if you add the Marillat repository:

deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) stable main

You not only get a the updated version of the acrobat reader, but you also can get w32codecs, libdvdcss2 (though older than the PLF version) and a newer version of libdvdread3.

---

### Post by John Jason Jordan on 2006-06-20
[QUOTE=Limulus]I went to Adobe's site and it offered me version 7.08, so I tried the nppdf.so from that and it worked, so if anyone doesn't feel like downloading the ~40 MB archive to extract it from, here's just the one file :)

[http://members.shaw.ca/Limulus/files/nppdf.so.tar.gz](http://members.shaw.ca/Limulus/files/nppdf.so.tar.gz)

Double click on it to open the Archive manager and extract it, then follow Rackerz' instructions.[/QUOTE]
I'd love to have Reader 7.08, but I don't know how to make a .deb out of the tar.gz file. I did use force-architecture to install 7.01, but it has a lame print user interface. Someone told me that they overhauled the print dialog box, so I'd like to get a later version.

Also, I tried to follow rackerz's advice to put the nppdf.so file in /usr/lib/Adobe/Acrobat7.0/ but I didn't have the folder he said to put it in.

---

### Post by stig on 2006-06-20
[QUOTE=jdong]Just to be a grumpy old critic, but what do you find attractive about the Acrobat Reader Plugin? ;)[/QUOTE]

I use the Ubuntu default reader for general viewing of PDFs but, like others who have replied here, I still need Acrobat reader too. In my case, it's because I publish material in hard copy and PDF which is sold to large companies worldwide. Until other PDF readers exactly mimic Acrobat Reader in their features, or until these corporations start to use the Linux readers, I will need AR - unfortunately!

---

### Post by Limulus on 2006-06-20
[QUOTE=John Jason Jordan]I'd love to have Reader 7.08, but I don't know how to make a .deb out of the tar.gz file. I did use force-architecture to install 7.01, but it has a lame print user interface. Someone told me that they overhauled the print dialog box, so I'd like to get a later version.

Also, I tried to follow rackerz's advice to put the nppdf.so file in /usr/lib/Adobe/Acrobat7.0/ but I didn't have the folder he said to put it in.[/QUOTE]

If you feel like trying 7.0.8, try this:

- go to [http://www.adobe.com/products/acrobat/readstep2.html](http://www.adobe.com/products/acrobat/readstep2.html) and get the ".rpm" version
- run Synaptic: uninstall "acroread" (and dependent packages) and install "alien"
- once alien is installed, use the command "sudo alien --scripts package_name.rpm" from Terminal, where package_name.rpm is the name of the file you just downloaded (and don't use quotes ;)
- a DEB will be generated; double-click it and gdebi should allow you to install it

---

### Post by John Jason Jordan on 2006-06-20
[QUOTE=Limulus]If you feel like trying 7.0.8, try this:
- go to [http://www.adobe.com/products/acrobat/readstep2.html](http://www.adobe.com/products/acrobat/readstep2.html) and get the ".rpm" version
- run Synaptic: uninstall "acroread" (and dependent packages) and install "alien"
- once alien is installed, use the command "sudo alien --scripts package_name.rpm" from Terminal, where package_name.rpm is the name of the file you just downloaded (and don't use quotes ;)
- a DEB will be generated; double-click it and gdebi should allow you to install it[/QUOTE]
Thanks! I used alien once some time ago and it failed to generate a .deb that would work. Nevertheless, I'll try it, but just a question first. I installed 7.01 from the command line with force-architecture. Hence it is not listed in Synaptic. How do I uninstall it?

---

### Post by Limulus on 2006-06-21
[QUOTE=John Jason Jordan]Thanks! I used alien once some time ago and it failed to generate a .deb that would work.[/QUOTE]
It is always a possibility that it might fail to produce a working DEB (such was the case with Java, as I recall), but its worth a shot, ne? :)

> Nevertheless, I'll try it, but just a question first. I installed 7.01 from the command line with force-architecture. Hence it is not listed in Synaptic. How do I uninstall it?
I found these instructions for 7.05; they should work for you too:

"By default, Adobe Reader is installed at /usr/local/Adobe/Acrobat 7.0. You can however, specify a different location. To uninstall Adobe Reader, simply delete the directory where it was installed."

---

### Post by James R. Phillips on 2006-06-29
I have found that the acrobat packages in the marrillat repository install OK in dapper (IA32).

First remove any installed acroread* packages, including mozilla-acroread.

Then, using a command line method, 
=============
wget [http://www.debian-multimedia.org/pool/main/a/acroread/acroread-escript_7.0.8-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/a/acroread/acroread-escript_7.0.8-0.0_i386.deb)
wget [http://www.debian-multimedia.org/pool/main/a/acroread/acroread-plugins_7.0.8-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/a/acroread/acroread-plugins_7.0.8-0.0_i386.deb)
wget [http://www.debian-multimedia.org/pool/main/a/acroread/acroread_7.0.8-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/a/acroread/acroread_7.0.8-0.0_i386.deb)
wget [http://www.debian-multimedia.org/pool/main/a/acroread/mozilla-acroread_7.0.8-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/a/acroread/mozilla-acroread_7.0.8-0.0_i386.deb)

dpkg -i *.deb
=============

---

### Post by dmizer on 2006-06-29
[QUOTE=evil_elman]Who comes up with these things, anyway?[/QUOTE]
heh ... don't know about Rackerz, but as for me ... i'm COMPLETELY bald. lol

by the way ... open office can save anything you create in pdf format.

---

### Post by Jott on 2006-06-29
The James R. Philips method worked great, thanks!

---

### Post by DavidFourer on 2006-07-03
How do I use Evince or other viewer to load a url instead of a file?  It says, "what file do you want to load" and I don't have a file name, just a url.
Also, Evince is in my /usr/bin/ but not in my Dapper applications menu.  Can you tell me how to get it on the menu?  Thanks.

---

