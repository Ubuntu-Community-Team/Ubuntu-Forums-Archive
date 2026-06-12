---
title: "Adobe Reader - libgtkembedmoz ?"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Bri0 on 2007-10-21
I installed Adobe-Reader, but when starting it up its saying I need to find the ' libgtkembedmoz '?
---
Message:
Unable to find the HTML rendering library
(libgtkembedmoz). Please specify the folder location in
Edit->Preferences->Internet.
---

Don't know what it is, or where its located.

Thanks

---

### Post by ariel on 2007-10-23
I run into the same problem. Found the fix in this page in French:

[http://forum.ubuntu-fr.org/viewtopic.php?pid=1209475](http://forum.ubuntu-fr.org/viewtopic.php?pid=1209475)

In plain english: start your new acroread, the go to Prefereces then click Internet and fill in:

   Browser Executable: /usr/bin/firefox
   libgtkembedmoz Folder: /usr/lib/firefox

Then click OK and restart your acroread. That's it, enjoy.

---

### Post by bigken on 2007-10-24
> **ariel said:**
> I run into the same problem. Found the fix in this page in French:

[http://forum.ubuntu-fr.org/viewtopic.php?pid=1209475](http://forum.ubuntu-fr.org/viewtopic.php?pid=1209475)

In plain english: start your new acroread, the go to Prefereces then click Internet and fill in:

   Browser Executable: /usr/bin/firefox
   libgtkembedmoz Folder: /usr/lib/firefox

Then click OK and restart your acroread. That's it, enjoy.

Cheers :)

---

### Post by denar on 2007-10-25
thanks

---

### Post by jasidog on 2007-10-25
Thank you Ariel! :)

---

### Post by merlin666 on 2007-10-28
Unfortunately, this didn't work for me :(

---

### Post by scott2004 on 2007-10-28
The file acroread needs is probably in /usr/lib/firefox

If not, check out this blog from Adobe which lists several options:

[http://blogs.adobe.com/acroread/](http://blogs.adobe.com/acroread/)

---

### Post by merlin666 on 2007-10-28
> **scott2004 said:**
> The file acroread needs is probably in /usr/lib/firefox

If not, check out this blog from Adobe which lists several options:

[http://blogs.adobe.com/acroread/](http://blogs.adobe.com/acroread/)

I think my problem may be that I am running 64-bit Gutsy, and the html rendering is not supported under 64bit.

---

### Post by plantman on 2007-10-29
> **ariel said:**
> I run into the same problem. Found the fix in this page in French:

[http://forum.ubuntu-fr.org/viewtopic.php?pid=1209475](http://forum.ubuntu-fr.org/viewtopic.php?pid=1209475)

In plain english: start your new acroread, the go to Prefereces then click Internet and fill in:

   Browser Executable: /usr/bin/firefox
   libgtkembedmoz Folder: /usr/lib/firefox

Then click OK and restart your acroread. That's it, enjoy.

Thanks so much!:) It worked for me.

---

### Post by gupta_sumesh63 on 2007-10-30
# On starting acroread, a dialog box pops up "Unable to find the HTML rendering library (libgtkembedmoz)."

This happens if acroread was unable to find libgtkembedmoz.so and related component files on your system.

GNOME Help (aka Yelp) also uses these libraries for displaying the HTML content. To find out if your system has libgtkembedmoz.so, check the output of the following command:

ldd `which yelp` | grep libgtkembedmoz

If this returns a valid folder name, set the Adobe Reader preference at "Preferences > Internet > libgtkembedmoz Folder" to the returned folder name (see screenshot below). If this does not work for you or your desktop environment is non-GNOME based, then try one of the following:

    * Check to see if you have XULrunner installed (you can install the latest XULrunner from here), and find the folder containing libgtkembedmoz.so in the XULrunner installation. Set this folder in the "Preferences > Internet > libgtkembedmoz Folder" preference in Adobe Reader.
    * Check to see if you have Mozilla web-browser installed. Make sure the Mozilla installation is based on GTK 2+ (you can install GTK 2+ based Mozilla from here). Find the folder containing libgtkembedmoz.so in the Mozilla installation. Set this folder in the "Preferences > Internet > libgtkembedmoz Folder" preference in Adobe Reader.
    * For debian based distributions you can install libxul0d from here, and find the folder containing libgtkembedmoz.so in the libxul0d installation. Set this folder in the "Preferences > Internet > libgtkembedmoz Folder" preference in Adobe Reader.

If you're still not able to fix this, please post a comment to this page with the details and we will try to help you. Also refer FAQ item no. 10 below.

libgtkembedmoz setting in the preference pane

---

### Post by vonroeder on 2007-10-30
Hi

after you set the path: /usr/bin/firefox and /usr/lib/firefox make sure when u exit hat you do not click
on the x in the right hand corner, but go to File->Exit command otherwise it did not save the setings

---

### Post by CoolDreamZ on 2007-11-01
Hi, I have tried this and it does not work for me. I have Firefox installed and the file libgtkembedmoz.so is present in the /usr/lib/firefox folder.

Acroread allows me to set the folder (if I mistype it gives me an error, so I know it is picking up the setting).

I restart using the File menu but I still get the error message on startup. The setting is retained in the Edit->Preferences dialog

---

### Post by rudeboyskunk on 2007-11-01
Which version of Adobe Reader is being used?  I thought they fixed this bug for Reader 9.

---

### Post by CoolDreamZ on 2007-11-02
8.1.1 from the Medibuntu repository. I can't see a version 9 on the Adobe site.

---

### Post by redlabour on 2007-11-02
> **CoolDreamZ said:**
> 8.1.1 from the Medibuntu repository. I can't see a version 9 on the Adobe site.

Same to me - thanks for the Instructions - they worked! :guitar:

---

### Post by faical117 on 2007-11-02
thank's :)

---

### Post by blastradius on 2007-11-26
Followed the instructions, the file is there in /usr/lib/firefox (Gutsy 64 bit) but Acrobat still says it can't find it! Tried the command line thing which confirmed the location but still no change.

HELP!

---

### Post by merlin666 on 2007-11-26
> **blastradius said:**
> Followed the instructions, the file is there in /usr/lib/firefox (Gutsy 64 bit) but Acrobat still says it can't find it! Tried the command line thing which confirmed the location but still no change.

HELP!

I don't think acrobat works with 64-bit firefox libraries. maybe installing 32-bit firefox will help.

---

### Post by dschaefer79 on 2007-11-28
Hi,

I installed Firefox 32 bit from the 3in1 script. I installed the Xulrunner 32 bit and when I set in acrobat 8 firefox 32 bit and libgtkembedmod 32 bit. It doesn't work.

Can someone help me ?

Thanks. 

Dominique Schaefer

---

### Post by yangli on 2007-11-29
Thanks a lot. 

> **ariel said:**
> I run into the same problem. Found the fix in this page in French:

[http://forum.ubuntu-fr.org/viewtopic.php?pid=1209475](http://forum.ubuntu-fr.org/viewtopic.php?pid=1209475)

In plain english: start your new acroread, the go to Prefereces then click Internet and fill in:

   Browser Executable: /usr/bin/firefox
   libgtkembedmoz Folder: /usr/lib/firefox

Then click OK and restart your acroread. That's it, enjoy.

---

### Post by krambo on 2007-12-02
Thank you ariel - worked for me ;)

---

### Post by logos34 on 2007-12-05
Add another 64-bit gutsy user to the complaint list.  

Tried libgtkembedmoz in the /usr/lib/firefox (x64 version), newly-installed xulrunner (/usr/lib/xulrunner). and even /usr/lib/thunderbird.  No dice.

Good thing I it's not an absolute necessity...evince works fine for most part (lot lighter too), although I do need acroread for one thing: pdf download add-on in firefox.  Would be nice if it worked properly.

---

### Post by jbaloul on 2007-12-05
and yet another...
my amd64 gutsy install has the same issues described, and the solution that works for the x86 install does not apply.

Jacob
[http://howtoforums.net](http://howtoforums.net)

---

### Post by Ozztopia on 2007-12-06
This seems to be an issue with amd64 gutsy. Doesn't work on my one too.

---

### Post by amd-64 on 2007-12-13
This issue is resolved on a x64 Gutsy 7.10

[http://lglinux.blogspot.com/2007/10/acroread-81-on-ubuntu-gutsy-amd64.html](http://lglinux.blogspot.com/2007/10/acroread-81-on-ubuntu-gutsy-amd64.html)

Enjoy!


```

uname -a
Linux ultra 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux
```

---

### Post by logos34 on 2007-12-13
> **amd-64 said:**
> This issue is resolved on a x64 Gutsy 7.10

[http://lglinux.blogspot.com/2007/10/acroread-81-on-ubuntu-gutsy-amd64.html](http://lglinux.blogspot.com/2007/10/acroread-81-on-ubuntu-gutsy-amd64.html)

Bingo!  Thanks!  I untarred it in home dir.  (But maybe I'll move it to /usr/lib).  It would only seem to accept it if I browsed to the folder, then hit ok, and closed acroread with File>Exit.  Then restarted and all is well in Ubuntuland.  (well, almost).

So, **32-bit** xulrunner/libgtkembedmoz is the key.

(I uninstalled the x64 version 1.8.1.4 beforehand.  Not sure if it matters though)

---

### Post by CoolDreamZ on 2007-12-15
> **amd-64 said:**
> This issue is resolved on a x64 Gutsy 7.10

[http://lglinux.blogspot.com/2007/10/acroread-81-on-ubuntu-gutsy-amd64.html](http://lglinux.blogspot.com/2007/10/acroread-81-on-ubuntu-gutsy-amd64.html)

Enjoy!


```

uname -a
Linux ultra 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux
```

Works for me too :)

---

### Post by mastergunner on 2007-12-17
....

---

### Post by jbaloul on 2007-12-19
Perfect...like a glove

Jacob
[http://howtoforums.net](http://howtoforums.net)

---

### Post by mastergunner on 2007-12-21
Does anybody have the complete http address to download from mozilla?

---

### Post by mastergunner on 2007-12-21
Nevermind I got it.

---

### Post by vgrisham on 2007-12-26
> **merlin666 said:**
> I think my problem may be that I am running 64-bit Gutsy, and the html rendering is not supported under 64bit.

merlin666, 

I have the same problem, and I want to uninstall Adobe Reader. How does one uninstall this thing?

EDIT: I found the answer to the question above. 

# sudo dpkg -r AdobeReader-enu

---

### Post by logos34 on 2007-12-27
> **vgrisham said:**
> merlin666, 

I have the same problem, and I want to uninstall Adobe Reader. How does one uninstall this thing?

EDIT: I found the answer to the question above. 

# sudo dpkg -r AdobeReader-enu

Did you try the workaround contained in the link Amd64 posted above?
> 
[http://lglinux.blogspot.com/2007/10/...tsy-amd64.html](http://lglinux.blogspot.com/2007/10/...tsy-amd64.html)

---

### Post by vgrisham on 2007-12-27
> **logos34 said:**
> Did you try the workaround contained in the link Amd64 posted above?

No, but I'd like to. The link is broken. Would you please verify the URL?

Thank you.

---

### Post by logos34 on 2007-12-27
it broke when I copied 'n pasted...click on original in post #25

---

### Post by waltclay on 2008-01-03
> **ariel said:**
> I run into the same problem. Found the fix in this page in French:

[http://forum.ubuntu-fr.org/viewtopic.php?pid=1209475](http://forum.ubuntu-fr.org/viewtopic.php?pid=1209475)

In plain english: start your new acroread, the go to Prefereces then click Internet and fill in:

   Browser Executable: /usr/bin/firefox
   libgtkembedmoz Folder: /usr/lib/firefox

Then click OK and restart your acroread. That's it, enjoy.

Thanks, Ariel. I can't give you a vote of thanks because the icon isn't there. In fact, there's a whole thread about the missing icon. Crappy software generates its own activity: bugs on bugs.

---

### Post by HorsesTwo on 2008-01-10
thanks much! works on my gutsy 7.10 ia64.

---

### Post by jayarsantos on 2008-01-25
thanks ariel

---

### Post by gmolleda on 2008-04-26
In my computer, the file libgtkembedmoz was in the directory /usr/lib/thunderbird

You must search in the typical mozilla directories (firefox, thunderbird, ... other mozilla programs).

And finally change the Edit - Preferences - Internet: Folder to libgtkembedmoz.

Bye.

---

### Post by robcasort on 2008-04-26
I had worked installing the following packages:
libmozjs0d
libxul-common
libxul0d

Once installed, the library was located in libgtkembedmoz.so **/usr/lib/xulrunner**

That is the path that he wrote in preferences/internet Acrobat Reader

I hope I have helped, certainly use ubuntu hardy 8.04

---

