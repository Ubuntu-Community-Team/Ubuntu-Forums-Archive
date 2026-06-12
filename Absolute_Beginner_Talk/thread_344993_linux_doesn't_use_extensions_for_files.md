---
title: "linux doesn't use extensions for files?"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by bone2006 on 2007-01-23
I'm really not sure how linux determines what a file is and what's registered to it.  The reason I'm asking is that I have some sfv files, which are just ascii files and ubuntu thinks it's a text file, so it opens it up with a text editor.  I have an sfv checker program installed and if right click on the sfv file and say open with the sfv checker program, then text files are then opened with this instead of a text editor.

How do I tell ubuntu that I want an sfv file to be opened with my software utility that I installed, instead of gedit.

---

### Post by bionnaki on 2007-01-23
right click>properties
and then change application to open with.

---

### Post by ComplexNumber on 2007-01-23
>  		 		 		 		I'm really not sure how linux determines what a file is and what's registered to it.
mime-types. 

it may well be that the sfv file does not have any associated program to open/edit it at that time, so defaults to a text file type.

---

### Post by bionnaki on 2007-01-23
well, a sfv file *is* just a text file.

---

### Post by macogw on 2007-01-23
ASCII = text
What it's doing makes sense...

And no, Linux doesn't require file extensions.  It sort of just knows.  I never attach file extensions when I do text files.  Consequently, shell scripts don't end in .sh, they just have a name.  Linux figures it out.  The .sh is just for humans to read it.  Same with .txt or whatever else.  I leave off .txt, but then when I send it to Windows users they get confused and add .doc like the only possible type of file that can display text is .doc.  If they saw that it's only like 12kb, it should be obvious that no Word file is that little and it has to be plain text.  They could save themselves like 2 minutes of load time if they used Notepad instead of Word.  Silly people.  There is almost no reason to ever use Word or Writer.  The exception would be if you need to have a header or footer (because of finding page breaks).  If you're just saving a note-to-self thing, plain text is better (and smaller).

---

### Post by bone2006 on 2007-01-25
Ok, I don't think my question was really answered or maybe linux is just behind?
I am very aware that an sfv/md5 file are simply text ascii files.  
The bottom line is I don't want to use gedit to open an sfv file.  I want to use the parano and if I change the properties so that an sfv file will open in parano, now guess what? my text file are being open in parano. I just want my sfv files to be opened with parano, which is a gui based sfv checker creator and I want my text file to open in a text editor.  

I find it hard to believe that every ascii file has to be registered with the same program.  So if I have a cpp or anything that's ascii I'm going to be forced to use the same program?

---

### Post by aysiu on 2007-01-25
> **bone2006 said:**
> Ok, I don't think my question was really answered or maybe linux is just behind?
I am very aware that an sfv/md5 file are simply text ascii files.  
The bottom line is I don't want to use gedit to open an sfv file.  I want to use the parano and if I change the properties so that an sfv file will open in parano, now guess what? my text file are being open in parano. I just want my sfv files to be opened with parano, which is a gui based sfv checker creator and I want my text file to open in a text editor.  

I find it hard to believe that every ascii file has to be registered with the same program.  So if I have a cpp or anything that's ascii I'm going to be forced to use the same program?
Use KDE, then. In KDE you can specify file associations by extension, not just type.

---

### Post by Threbus5 on 2007-01-25
Hi,  

No, You need not use the same program.

You can assign a particular program to open a particular file type/extension.
See the note by bionnaki and aysiu " 	right click>properties
and then change application to open with.".

And Linux certainly assigns file extensions. For example Observe .gif and .jpg extensions on graphics and when saving an open office document there are multiple options for extension. (And I am using gnome not kde)


Take care

---

### Post by az on 2007-01-25
> **bone2006 said:**
> Ok, I don't think my question was really answered or maybe linux is just behind?

[http://en.wikipedia.org/wiki/Magic_number_(programming](http://en.wikipedia.org/wiki/Magic_number_(programming))

A magic number is a way to identify the contends of a data file.  Unfortunately, if something is a text file, it's a text file.

Despite that, this is the first time I have ever heard of that being an inconvenience.

---

### Post by bone2006 on 2007-01-26
what you suggested Threbus5 is what I did and what I was explaining that when I change the association with sfv files, then any text file regardless of the extention would open in the associated sfv program. 
I'm using KDE on one system and Gnome on another system. 

I guess some people just love terminals as I'm certain thousands of users check md5 files all the time in linux and I"m just guessing that they love terminals. I just prefer double clicking a file then opening up a terminal and navigating and typing in the command.  Just seems like my hand is on the mouse more than the keyboard, so my perference would be to use a gui based application.    I've just been using gui based applications for MD5 and SFV files in windows for over a decade and the only thing I found in linux that was worth anything was parano and even though I've found it, it's a shame that I'm not able to tell parano to open sfv and gedit to open other text files.

---

### Post by rccharles on 2007-01-27
> **bone2006 said:**
> what you suggested Threbus5 is what I did and what I was explaining that when I change the association with sfv files, then any text file regardless of the extention would open in the associated sfv program. 
I'm using KDE on one system and Gnome on another system. 

You can use the terminal command file to display the linux filetype.  Example:
file grabber.gif

Linux tends to put the file type in the first record of the file.

You might try appending .sfv to the file.  Perhaps there is some way of telling linux to pay attention to the extension.

I suspect Linux doesn't know about file extensions.  When you see the extension it is a convention for human understanding.

Robert

---

### Post by bone2006 on 2007-01-31
Am I the only one who doesn't think it's not very intelligent to treat every ascii file the same?

Lets' say I have a text file emailed to me from windows, I only want to view it in a text editor.  I have an sfv file I want to open in a gui sfv checker, then I'm writting code in an asci file with the extention cpp, but I'd like to use a programming syntax editor that shows colors for my logic when programming.  Are you guys saying that linux isn't able to do this?  It really has no way of knowing when I want to open an ascii file to check an sfv, to write code in a different editor and when to just use a default text editor?

I can't believe I'm the first one to have used linux that is finding this hard to believe or to find if this is true kind of backwards?

---

### Post by szf on 2007-01-31
I think that you're over-thinking the problem here... if you have an extension that you want to assign to a particular application a particular way - then do so *within your operating system*. There is no 'central authority' for file extensions, nor is there a smart in-between for determining the file content [aside] how many here cannot send a *.zip file to their co-workers? Is .zap a reasonable mis-extension?  How about .arch? [/aside]. Asking Linux to *do exactly what you want* based on the file extension (or lack thereof) borders on precognition.

---

### Post by macogw on 2007-01-31
> **bone2006 said:**
> Am I the only one who doesn't think it's not very intelligent to treat every ascii file the same?

Lets' say I have a text file emailed to me from windows, I only want to view it in a text editor.  I have an sfv file I want to open in a gui sfv checker, then I'm writting code in an asci file with the extention cpp, but I'd like to use a programming syntax editor that shows colors for my logic when programming.  Are you guys saying that linux isn't able to do this?  It really has no way of knowing when I want to open an ascii file to check an sfv, to write code in a different editor and when to just use a default text editor?

I can't believe I'm the first one to have used linux that is finding this hard to believe or to find if this is true kind of backwards?
Gedit has syntax highlighting.  So does vim.  Just turn it on.  In Gedit you can pick what language you're programming and it will adjust the syntax to match.

---

### Post by macogw on 2007-01-31
> **bone2006 said:**
> what you suggested Threbus5 is what I did and what I was explaining that when I change the association with sfv files, then any text file regardless of the extention would open in the associated sfv program. 
I'm using KDE on one system and Gnome on another system. 

I guess some people just love terminals as I'm certain thousands of users check md5 files all the time in linux and I"m just guessing that they love terminals. I just prefer double clicking a file then opening up a terminal and navigating and typing in the command.  Just seems like my hand is on the mouse more than the keyboard, so my perference would be to use a gui based application.    I've just been using gui based applications for MD5 and SFV files in windows for over a decade and the only thing I found in linux that was worth anything was parano and even though I've found it, it's a shame that I'm not able to tell parano to open sfv and gedit to open other text files.

Can you add the sfv checker to the open-with options?  Then you can right click and pick if you want Gedit or SFV when you go to open the file.

---

### Post by rccharles on 2007-01-31
> **szf said:**
>  Asking Linux to *do exactly what you want* based on the file extension (or lack thereof) borders on precognition.

In Mac OS you can set what program will open a file on a per file basis.  That is abc.html can be opened in a text editor and def.html can be openned in a browser.  By default, whatever program creates the file, opens the file.  

In Windows, you can choose the program to used to open a group of file on  the file extension.  

Would be nice if Linux could do this.

Robert

---

### Post by aysiu on 2007-01-31
> **rccharles said:**
> 
In Windows, you can choose the program to used to open a group of file on  the file extension.  

Would be nice if Linux could do this. I thought we already established Linux could do this (go to File Associations in KDE). Gnome cannot, however, right now. If it's that important to you, use KDE.

---

### Post by szf on 2007-02-01
> **rccharles said:**
> In Mac OS you can set what program will open a file on a per file basis.  That is abc.html can be opened in a text editor and def.html can be openned in a browser.  By default, whatever program creates the file, opens the file.  

Wow. That would take me some getting used to... but then again I'm not a mac person. 

> **rccharles said:**
> 
In Windows, you can choose the program to used to open a group of file on  the file extension.  

Would be nice if Linux could do this.


It's nice that KDE has support for what's been asked... for gnome, perhaps someone has had success with [g-scripts for nautilus]("http://g-scripts.sourceforge.net/")?

---

### Post by bone2006 on 2007-02-01
Thanks for the replies.  Kind of disappointing that gnome doesn't have support for this.  I'm running ubuntu on three systems and the system that I run md5 and sfv checks often, I'm using gnome.   
Hopefully one day gnome will see why it's desirable to have this capability.  I'll look into the scripts that were posted.
Thanks again everybody

---

### Post by bone2006 on 2007-02-02
It seems it does know the difference between one asci text file and another one.  Just not sfv files.

I have a file called playlist.m3u and if I rename it to playlist.m3u.txt and double click on it, the text editor will open the file, if I keep it with the extention m3u then the audio player will play with it.  I'm guessing it's part of natilus, but I am seeing that it does determine the difference between a file that ends with txt and one that ends with m3u, regardless if they are both asci files.

---

### Post by detyabozhye on 2007-02-03
AFAIK, Gnome partly relies on both mimetype and extension, but not fully on either one. They try to find a good balance between both. Personally, I'm an Xfce person though, and Thunar seems to do the job a tiny bit better than Nautilus for me, so I don't really have that problem. AFAIK, there should be a way for it to detect by the contents of the file (maybe the first few lines) that it is a svf and not a *plain* plain text file, the way it does for shell scripts, but I dunno how it's done.

---

### Post by steve.horsley on 2007-02-03
There is a mime type editor in gnome. I've seen it, but I can't find it again now. It gave you the ability to add new mime types, including using the extension to identify it (it recognises .log for instance).

Does anyone know how to find this mime type editor?

---

### Post by bone2006 on 2007-02-05
I'm too much of a newbie to even know what mime really is, but when doing a search I found this

freshmeat.net/projects/mime-editor/

---

### Post by steve.horsley on 2007-02-05
That's the thing. Either that or a very close relative (with the same fields) was included in an early Ubuntu, because I remember trying to figure out WTF to put in the mime type. I never did find how to use it.

There is a package gnome-mime-data that puts what looks like a database in these two files:
file:///usr/share/mime-info/gnome-vfs.keys
file:///usr/share/mime-info/gnome-vfs.mime
but these aren't the whole story (if they are any part of the story at all) because if you look at the open with dialog for a .log file, it says it is type "application log", but none of those files contain that string.

---

### Post by bone2006 on 2007-02-05
I tried downloading that editor, but couldn't figure out even how to install it LOL

After searching for info about mime, I see that others have posted similar questions.  I saw this post about an nfo viewer, but the how to isn't working for me

[http://www.ubuntuforums.org/showthread.php?t=83499&highlight=edit+mime](http://www.ubuntuforums.org/showthread.php?t=83499&highlight=edit+mime)

---

### Post by bone2006 on 2007-02-05
glad to know I'm not the only one who thinks all asci files should be opened with a text editor or the same text editor.
I hope there will eventually be a release that makes it much easier to tell ubuntu that I'd like to open an sfv with one program, an md5 with another, a text with another, a nfo with another and even a cpp with yet another one.  
Or at least offer a decent mime editor that we can use.  I guess the original thought was just to right click and go to properties and that would take care of it, which is kind of fustrating if you have an ascii file you want to view or run with another application.

---

### Post by steve.horsley on 2007-02-06
I thought I had found it for a minute.
try man **update-mime** and then look at /etc/mailcap.

But this doesn't list even half the file types I know Ubuntu can recognise. I dunno - it's all too difficult. You're right - there should be a simple editor for this kind of thing. I'd write one, but I haven't a clue what files it should be modifying.

---

### Post by detyabozhye on 2007-02-07
Gnome does detect the mime type fine in shell scripts, python scripts, various source code files, etc. and they are all ascii files. There has to be a way for it to detect other special ascii files as well.

---

### Post by bone2006 on 2007-02-12
detyabozhye it seems to be predetermined.   Because if you change the extension to something it knows, it will understand the file.  But if I put a new extension on the end of the file, it will only think it's a text file and if you change the association with the new extension, then all text files are going to be associated with that application.

To be honest, it's disappointing that there isn't an easier way to change ascii associated files in gnome.

---

### Post by detyabozhye on 2007-02-12
> **bone2006 said:**
> detyabozhye it seems to be predetermined.   Because if you change the extension to something it knows, it will understand the file.  But if I put a new extension on the end of the file, it will only think it's a text file and if you change the association with the new extension, then all text files are going to be associated with that application.

To be honest, it's disappointing that there isn't an easier way to change ascii associated files in gnome.

Hmm, that's messed up. I guess we could file a bug report then.

---

