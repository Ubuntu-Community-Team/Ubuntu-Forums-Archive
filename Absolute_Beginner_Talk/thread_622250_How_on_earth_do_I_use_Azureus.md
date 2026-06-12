---
title: "How on earth do I use Azureus?"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by gheywood on 2007-11-24
Hello, 

I used the supplied bitorrent program with no major problems, but it would be nice to download (or attempt to) several at the same time. So, bingo, install Azureus right? 

Managed to get that done, but when I go to a bit torrent site ([www.isohunt.com](www.isohunt.com) for example), and select one, it automatically uses the supplied client rather than Azureus. Next thing I tried was saving the torrent locally and then opening it, but i cannot find anything to open with Azureus. 

Can anyone tell me how to integrate Azureus with the shell so I can use it automatically? 

Or any other really basic steps to use it? 

Cheers

---

### Post by kellemes on 2007-11-24
> **gheywood said:**
> Hello, 

I used the supplied bitorrent program with no major problems, but it would be nice to download (or attempt to) several at the same time. So, bingo, install Azureus right? 

Managed to get that done, but when I go to a bit torrent site ([www.isohunt.com](www.isohunt.com) for example), and select one, it automatically uses the supplied client rather than Azureus. Next thing I tried was saving the torrent locally and then opening it, but i cannot find anything to open with Azureus. 

Can anyone tell me how to integrate Azureus with the shell so I can use it automatically? 

Or any other really basic steps to use it? 

Cheers

You could open Azureus and browse for the torrent.
Or you can configure your browser to use Azureus to open the torrent.. look in the configuration-dialog.

---

### Post by bluepowder7 on 2007-11-24
i use Deluge, but the same process would apply - either set it up from within the browser, or if you save the .torrent files like i do, you need to manually find the torrent executable file (or whatever it's called).  i can't recall where i found it.  it was probably in /etc or /usr or one of those..


EDIT - here we go, found it.  when you have the .torrent file, right-click on "open with other application" and then on the bottom of the dialog box click on "use a custom command" and "browse" to your /usr/bin directory, and select the azureus file.  in my case, i found the deluge file, and selected that.  it seems to have worked for me.

---

### Post by markharding557 on 2007-11-24
right click on a torrent file,open with other application--add 
this will then open with azureus.
you can configure azureus as the default by propertys-->open with,select one to be default

---

### Post by gheywood on 2007-12-04
OK, when I click on a link (such as from [www.isohunt.com](www.isohunt.com)), I can right-click and choose "save" then save the file to desktop. I then have a file called (for example) film111.2006.eng.cam.divx-ltt.342432.tpb.torrent.

The file is (for exmample) 14.8k. 

If I then right-click on it, and choose Open with "Azureus", I get a message saying:

'file:///home/greg/Desktop/film111.2006.eng.cam.divx-ltt.342432.tpb.torrent' could not be opened: Not a file


It looks like a file to me though!

Any clues?

Cheers

---

### Post by gheywood on 2007-12-05
Hmm...

Also, if I open Azureus by itself, it closes immediately after the splash screen..

Maybe it just doesn't work with this version of Linux?

---

### Post by vikram on 2007-12-05
trying running Azureus from the terminal. the error may give you a clue. I use Azureus in Kubuntu Feisty and Gusty without any issues.

also look at alternate clients like ktorrent available in the repos.

---

### Post by gheywood on 2007-12-05
Thanks. Ktorrent worked.

(if anyone wants it, you can do "sudo apt-get install ktorrent" (I was pretty proud of myself for getting that right first time :) )

---

