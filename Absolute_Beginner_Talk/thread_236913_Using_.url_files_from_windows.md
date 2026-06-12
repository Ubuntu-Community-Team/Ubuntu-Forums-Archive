---
title: "Using .url files from windows?"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by neocookie on 2006-08-15
I have a lot of .url shortcuts backed up from my windows machine. Is there anyway I can tell ubuntu to use these as links for Firefox?

---

### Post by Kobalt on 2006-08-15
Here is something that might help you out : [Howto Thunderbird/Firefox profile share XP & Dapper]("http://ubuntuforums.org/showthread.php?t=203524&highlight=howto+firefox+windows")

Cheers !

---

### Post by neocookie on 2006-08-17
Nope... doesn't help.

These .url files are essentially text files with a URL inside them. I just need ubuntu to send that URL to firefox.

Any ideas?

---

### Post by bsmith1051 on 2006-10-19
yeah, I have this same problem.  It's really ridiculous that something so simple doesn't work.  As near as I can tell, this is the situation:

1. Windows' .URL files are simple text files with the URL as the only text and, since this is Windows we're talking about, they rely on the file extension to indicate the file-type.
2. Ubuntu sees the .URL extension and treats it as file-type "application/x-mswinurl".
3. Ubuntu then refuses to use the file since it's not formatted the way it expects it.  But since it recognizes it as "MS Win URL" what other format is it expecting?

Basically, I think it's a bug in the "application/x-mswinurl" definition, probably on Gnome's part.

---

### Post by AlanRogers on 2006-10-27
I'm experiencing a similar problem, using my windows machine to do a lot of research during breaks, and saving the URLs as files to my USB stick.

Is there an Ubuntu method of Open With... like there is in Wiindows, with a Always Use This Application check box?

I don't really want to be messing around in code I don't (yet) understand!

---

### Post by nejode on 2006-10-27
What I do is right-click the url icon, copy the address and paste it in Firefox, open the page and then bookmark.  I Then export my Firefox bookmarks to the pendrive... Windows will open the bookmarks file as html and all your links will be listed there.

---

### Post by oomingmak on 2007-09-30
Internet Explorer .url shortcut files **_can_ **be made to work in Ubuntu / Linux.

The following thread contains step by step instructions on how to do it:

[**[COLOR=DarkOrange]http://ubuntuforums.org/showthread.php?t=495131[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=495131")


You can then store your web links in any folder (for example on a USB stick) and use them in both Windows *and *in Ubuntu. This means that you only  have to maintain a single collection of links for both systems.

If you are using Firefox on Windows, then you can create .url shortcuts either by just dragging a tab to the Desktop, or by installing the [**[COLOR=DarkOrange]Create Shortcut[/COLOR]**]("http://www.pikey.me.uk/mozilla/") extension (to add a right-click 'Create Shortcut' menu that allows you to edit the link and  specify the default save location).

[COLOR=Gray]Note: Firefox in Linux creates .desktop files when making shortcuts (unlike in Windows where it will make .url files).[/COLOR]

---

