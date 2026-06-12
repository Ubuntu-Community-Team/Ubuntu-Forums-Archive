---
title: "Problem with installing Acrobat Reader 8.1.1 with plugin for firefox"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by baz.g on 2008-01-01
Hi,

i followed the instructions for this here:

[http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-811-with-plug-in-for-mozilla-firefox-in-gutsy-gibbon.html](http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-811-with-plug-in-for-mozilla-firefox-in-gutsy-gibbon.html)

but i get this error after inputting the install command:

```

Do you want to continue [Y/n]? y
(Reading database ... 150150 files and directories currently installed.)
Unpacking acroread (from .../acroread_8.1.1-0medibuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/acroread_8.1.1-0medibuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu
Selecting previously deselected package acroread-escript.
Unpacking acroread-escript (from .../acroread-escript_8.1.1-0medibuntu3_i386.deb) ...
Selecting previously deselected package acroread-plugins.
Unpacking acroread-plugins (from .../acroread-plugins_8.1.1-0medibuntu3_i386.deb) ...
Unpacking mozilla-acroread (from .../mozilla-acroread_8.1.1-0medibuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/mozilla-acroread_8.1.1-0medibuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/firefox/plugins/nppdf.so', which is also in package adobereader-plugin
Errors were encountered while processing:
 /var/cache/apt/archives/acroread_8.1.1-0medibuntu3_i386.deb
 /var/cache/apt/archives/mozilla-acroread_8.1.1-0medibuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

and when i then try to start acrobat from the applications menu, i get a "Failed to execute child process "Acroread".

please help :)

---

### Post by bcrom on 2008-01-01
Instead of using Acrobat I use Evince Document Viewer 2.20.1 to read PDFs.  It opens faster and I've never had a problem.  Install it in Add/Remove programs (it's named Document Viewer) and see if it does what you need.

---

### Post by mount_evans on 2008-01-13
> **bcrom said:**
> Instead of using Acrobat I use Evince Document Viewer 2.20.1 to read PDFs.  It opens faster and I've never had a problem.  Install it in Add/Remove programs (it's named Document Viewer) and see if it does what you need.

Can it be turned into a plugin for Firefox, so that you can open "webpages" that are actually PDFs?

---

### Post by mount_evans on 2008-01-13
> **baz.g said:**
> Hi,

i followed the instructions for this here:

[http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-811-with-plug-in-for-mozilla-firefox-in-gutsy-gibbon.html](http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-811-with-plug-in-for-mozilla-firefox-in-gutsy-gibbon.html)

but i get this error after inputting the install command:


For what it's worth, I went to that site and followed the directions, and now I can read PDFs iin FIrefox.

---

### Post by LinuxMonk on 2008-01-13
I did this just a couple of days ago.  What worked for me was to go to [http://www.adobe.com](http://www.adobe.com), download the latest Linux version of Reader, then use alien to convert it to a deb package.  Run sudo dpkg -i, and presto, Adobe Reader...

If you do this, don't forget to add the -c parameter (to convert any scripts) to the alien command.

---

### Post by Majorix on 2008-01-13
You can try enabling the Medibuntu repos (Google, I Feel Lucky) and install mozilla-acrobat or whatever it was called through Synaptic. If you search for "acroread" on Synaptic with Medibuntu enabled you should get 4 packages listed. I would install all of them. And you should have an acrobat plugin in your Firefox after that.

---

### Post by bcrom on 2008-01-13
mount_evans: just for the record, I don't have evince set up as a plugin but it does automatically open whenever I click a PDF in firefox.  I like that better because I don't lose all my firefox hotkeys.

---

