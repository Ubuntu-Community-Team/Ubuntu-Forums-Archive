---
title: "Impressed! But looking for a combined FTP client / file editor"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by mattywarr on 2008-04-21
Hello all :)

I'm a linux newcomer and last week decided that I had enough of windows and wanted to try Linux. Searching around, it was clear that Ubuntu was the right choice. After some installation woes, I installed it and even managed to get my Broadcom wireless working easy enough! Now I'm flying along with Ubuntu, trying desperately to make sure i can ditch windows for good by getting all the applications I need to use my PC for what I need!

Where possible, I'm trying to use Linux programs, but some places I've had to resort to using WINE (Which is still remarkably easy to use) These being:
- Photoshop CS2
- Symantec pcAnywhere
- Ladbrokes Poker

I LOVE the way its so easy to install apps from the repositories and LOVED the way I could just open an ISO I downloaded instantly! Its just great!

However, there is one particular app I could really use - a combined FTP and File Editor! I used to use CuteFTP Pro, which had multiple site support and an in built code editor, which allowed you to edit files and save them on the server without having to work on it, save, and upload seperately. Is there anything similar to this available?

---

### Post by sdennie on 2008-04-21
I believe that nautilus directly supports this (though, I've never tried).  You could try this by going to Places->Connect to Server.  It should be straightforward to test from there.

---

### Post by mattywarr on 2008-04-21
> **vor said:**
> I believe that nautilus directly supports this (though, I've never tried).  You could try this by going to Places->Connect to Server.  It should be straightforward to test from there.

Gret, I can download gEdit which will make my PHP editing virtually seamless!

Next question:

I like to view all my windows as "List". Is there any way to set this to be the default for ALL the windows I ever open (Windows could do this in Folder Options)?

---

### Post by sdennie on 2008-04-21
Edit->Preferences from nautilus.  It's the first option.  ;)

---

### Post by mattywarr on 2008-04-21
Legend :)

---

### Post by mattywarr on 2008-04-21
Ok, next dumbass question...

Trying to migrate my Thunderbird mail in Windows to Ubuntu.

I'm following the guide: [http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

I've found the profile folder I want to copy and added to clipboard - but i don't know where to copy to. It says to put it in ~/.thunderbird/xxxxxxxx.default/ But i can't find the folder. What i can find is in /etc/thunderbird.

Any ideas?

---

### Post by skymera on 2008-04-21
In your home folder press CTRL+H to show hidden folders.
It should be there if you have Thunderbird installed.

And it might be 
~/.**T**hunderbird/xxxxxxxx.default

---

### Post by hums07 on 2008-04-21
~/.thunderbird is hidden folder. In Nautilus, press Ctrl+H to hide/unhide.

---

### Post by sdennie on 2008-04-21
Also, if you've never started thunderbird on linux, you won't have that particular directory.  You'll need to start it at least once to create the place that you need to put that file.

---

### Post by mattywarr on 2008-04-21
Wicked, cheers :)

In this instance, it was in ./mozilla-thunderbird

---

### Post by HyperHacker on 2008-04-21
> **mattywarr said:**
> Where possible, I'm trying to use Linux programs, but some places I've had to resort to using WINE (Which is still remarkably easy to use) These being:
- Photoshop CS2Photoshop works in WINE? Sweet! I'd heard it didn't, but I haven't yet tried it myself. (Still getting graphics to work. <_<)

Personally, I was impressed that even with the graphics card not set up properly, I was able to run a 3D rendering app (that I wrote :D) almost flawlessly in WINE (couldn't detect input from the joystick POV hat), and it ran full speed even with the window turned translucent! Trying to turn a 3D window translucent in Windows gave me a BSOD. :P

I was also very much impressed with the support for all my hardware (except video cards >_>) out of the box, especially given how cheap and obscure some of it is.

---

### Post by mattywarr on 2008-04-21
Well, its INSTALLED in WINE. I havent quite managed to get it actually working yet. Still configuring stuff will get to working that problem out later :D

---

### Post by mattywarr on 2008-04-21
Ok, here's a new question.

One of the benefits of moving from my windows to ubuntu is that I like to fiddle in PHP/MySQL. I've installed LAMP and PHPMYADMIN but when I go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) as described everywhere, it tells me the URL does not exist on this server.

Is there someway to start this running/autorun?

And another - Any PDF writing software available for Ubuntu?

---

### Post by lizzard on 2008-04-21
> **mattywarr said:**
> Ok, here's a new question.

And another - Any PDF writing software available for Ubuntu?

Openoffice and Abiword can export to PDF. For editing PDFs you may have a look at PDFedit.

---

### Post by mattywarr on 2008-04-21
> **lizzard said:**
> Openoffice and Abiword can export to PDF. For editing PDFs you may have a look at PDFedit.

Thats OK, but I don't have a printer at home so i tend to just print to PDF anything I want to keep, such as eReceipts and other important Docs - So i need something that can do that kind of task.

---

### Post by mdr on 2008-04-21
Install a cupsys printer driver for pdf by going to 

System / Administration / Printing 
New Printer
Wait for the search 
Print to PDF

and there you go just print to this to create a pdf.   Creates a pdf in a PDF folder in your /home.

---

### Post by mattywarr on 2008-04-21
I'm loving Ubuntu more and more by the minute!

Quick note to HyperHacker - I got CS2 working OK but you need the very latest version of WINE to get through the activation screen. The default one in the Repository isn't quite the latest I don't think.

[http://ubuntuforums.org/showthread.php?t=679886](http://ubuntuforums.org/showthread.php?t=679886)

---

### Post by amir1979 on 2008-04-21
Hi Matty    im new to linux/ubuntu i just installed it im a first time user  and i have a broadcom wireless   can u help me get it working?  
thanks

---

### Post by MONODA on 2008-04-21
> Hi Matty im new to linux/ubuntu i just installed it im a first time user and i have a broadcom wireless can u help me get it working?
thanks
you should start a new thread for this, do not hijack this thread.

---

### Post by amir1979 on 2008-04-21
> **MONODA said:**
> you should start a new thread for this, do not hijack this thread.

ok will do sry

---

### Post by MONODA on 2008-04-21
> ok will do sry 
it's ok i just wanted you to get more replies.:D

---

### Post by bartcramer on 2008-04-21
> **mattywarr said:**
> 
One of the benefits of moving from my windows to ubuntu is that I like to fiddle in PHP/MySQL. I've installed LAMP and PHPMYADMIN but when I go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) as described everywhere, it tells me the URL does not exist on this server.


See: [http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/)

That might help you in a lot of cases. If not, keep posting :)

---

### Post by mattywarr on 2008-04-21
Indeed it did help!

I managed to get MySQL-Admin installed, but PHPmyadmin (Which I am a lot more comfortable with due to its ease of use) still doesn;t seem to want to play ball!

Anyone else had this issue?

---

