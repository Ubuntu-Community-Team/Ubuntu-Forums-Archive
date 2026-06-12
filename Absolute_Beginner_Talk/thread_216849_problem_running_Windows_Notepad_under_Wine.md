---
title: "problem running Windows Notepad under Wine"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Bob Unitt on 2006-07-16
Gentlefolk,

Just downloaded ubuntu and I'm most impressed ! I'm really a newcomer to Unix, apart from a brief brush with SCO some 15 years ago, so please be gentle with me...

I need to give someone the ability to create Windows-format text documents, which I can then copy (via SMB) to a W2000 machine for further processing. I've got the file-sharing up and running, and Wine installed and running Windows Notepad OK, but I've hit a snag trying to set it up to load Notepad automatically when the file-icon is clicked :-

Environment - ubuntu 6.06, gnome 2.14.2, wine 0.9.17, notepad 5.0.2140.1

create a new text-file 'home/guest/Desktop/test.txt'
select it in Gnome, and right-click for menu
choose 'Open with other application'
in 'Use custom command' enter 'wine notepad'

notepad opens with error message :-
  ERROR
  file 'ome/guest/Desktop/test.txt' does not exist
  do you want to create a new file ? YES NO
choosing 'YES' gives 'path does not exist'

I can navigate to the file via 'File Open' and it opens OK.

It looks as if 'open with other application' is failing to construct the command-line argument correctly - is this a known problem, or have I misunderstood the process here ?

TIA

---

### Post by adam.tropics on 2006-07-16
I can't be too specific with your problem as I don't use wine at all. But I was curious what the files are for exactly, as most things like this should be possible without wine. For example, OpenOffice can create and edit .doc files for use on Word etc etc.Come to think of it, also text, text encoded, and rich text.

---

### Post by Bob Unitt on 2006-07-16
> **adam.tropics said:**
> I can't be too specific with your problem as I don't use wine at all. But I was curious what the files are for exactly, as most things like this should be possible without wine. For example, OpenOffice can create and edit .doc files for use on Word etc etc.Come to think of it, also text, text encoded, and rich text.

My beloved other half is used to doing things a particular way, and I mess with that at my peril...
:-)

---

### Post by adam.tropics on 2006-07-16
As good a reason as any, and I don't believe you are alone.

---

### Post by YokoZar on 2006-07-18
I couldn't tell from reading your post, but are you putting 'wine notepad' in single quote marks like that, or not?

Also, realize that Wine comes with its *own* version of notepad.  This isn't the Notepad that comes with Windows, but is actually a clone written by the winedevs and compiled with winelib.  You may actually be running that version instead of the Windows notepad, however since it's such a simple app that might not matter.

---

### Post by FuzZy2006 on 2006-07-18
I can't see why you like Notepad. Linux has better text editor. Notepad is so old ....

---

### Post by T700 on 2006-07-18
As far as I know, Notepad just creates a plain text file.  Couldn't you use any text editor in Linux (vi, vim, nano, kate, gedit) and create a text file?  If you didn't tell your wife, she would be none the wiser.

Paul

---

### Post by aysiu on 2006-07-18
Aren't plain text documents all just plain text documents? I can't tell the difference between plain text I create in Notepad and plain text I create in Gedit...

And can't you select different kinds of character encoding in Gedit?

---

### Post by Brunellus on 2006-07-18
> **aysiu said:**
> Aren't plain text documents all just plain text documents? I can't tell the difference between plain text I create in Notepad and plain text I create in Gedit...

And can't you select different kinds of character encoding in Gedit?
Windows .txt documents are different from *nix textfiles in one important respect:  

hitting ENTER encodes both  a line feed (newline) AND a carriage return character in Notepad.  In *nix text editors, hitting ENTER only a line feed is encoded.  

small, but significant.

---

### Post by adam.tropics on 2006-07-18
Brunellus: Now you mention it, I seem to remember something of that from my Pascal days...many years ago, when transferring files from Solaris to NT.

---

### Post by mrvw0169 on 2006-07-19
Try using gedit (Accessories>Text Editor) and when you hit Save as for "windows text files" try changing the Current Locale on the save dialog by clicking Add or Remove on it and selecting Western WINDOWS-1252 and adding that and so next time just save using that format (it should be on the dialog now)... Sounds like it will work but I haven't tried it... You can always use dos2unix or unix2dos I think from dosfstools too...

---

### Post by Arisna on 2006-07-19
> **mrvw0169 said:**
> You can always use dos2unix or unix2dos I think from dosfstools too...

That's definitely the way I'd do it.

---

### Post by Bob Unitt on 2006-07-19
Thank you all for your responses - this is now resolved, YokoZar's post having pointed me in the right direction (except that it just needed the 'notepad' argument in single quotes, rather than the whole command line).

See 3rd post in thread for the reason I couldn't just use a unix editor instead...

---

### Post by mrvw0169 on 2006-07-19
Ahh haha, I missed your one line response and that is most definitely a good reason to get notepad working =P

---

