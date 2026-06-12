---
title: "A Real Beginner Question"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-11-21
What does "%u" mean in a launcher's command, as in "firefox %u"?  Where could I find that information so I wouldn't have to ask?  I just realized I don't know where there's a general manual for the command line.  Putting just "man" in a command doesn't work.  I supposed it meant "user's home directory" but that doesn't seem to be it.

Thanks in advance.

Buck

---

### Post by CatKiller on 2006-11-21
I think that would be a [URI]("http://en.wikipedia.org/wiki/Uniform_Resource_Identifier"), by context. I don't know where you would find out about things like that in a general sense. Certainly **man firefox** doesn't say.

---

### Post by steve.horsley on 2006-11-21
I believe it's best to remove the "%U" - that stops firefox from opening on some university's home page.

---

### Post by tocleora on 2006-11-21
A %u is a "single URL".  Here's how to get information about what these codes mean (there's probably an easier way but this is how I found it).

1. Right mouse click on your desktop and select "Create Launcher".
2. In the bottom left corner, click "Help".
3. Scroll down to the 6th box, labeled "CODE".

It doesn't make sense that this code would stop firefox from going to some university's web site as this is a command line option, unless that universities web site is what you're trying to access with %u.  I would leave it in there until you have that problem, then take it out then. :)

---

### Post by Buck2348 on 2006-11-21
Thanks very much for the replies.  I hope you'll be patient when I say I still don't understand.  That Help section does give the meaning of such codes, but it doesn't explain how they're used.  It says the codes will be replaced with the value specified in the table, which in this case is "A single URL."  Replaced when, by what or whom, and what URL?  It doesn't seem to affect the launcher when I remove the code==it still launches Firefox.  And how does that work?--the launcher contains no path to the Firefox executable.  Thanks for your patience while I'm trying to learn.

Buck

---

### Post by CatKiller on 2006-11-21
> **Buck2348 said:**
> Replaced when, by what or whom, and what URL?

The freedesktop spec linked to from that help page describes it thus:
> Each Exec field may take a number of arguments which will be expanded by the file manager or program launcher and passed to the program if necessary.
So if that launcher is used by the system to interpret a URL when clicked somewhere (which **is** likely), it can be passed to Firefox in the form it needs by modifying that variable. If it turned out that you needed quotes around a URL for Firefox to interpret it correctly, you could have **firefox "%u"**. But since Firefox can take a URL as an argument, it just gets stuck on the end.
> And how does that work?--the launcher contains no path to the Firefox executable.
It doesn't need to. You've already defined the standard place to look for executables with the PATH variable. The Firefox executable is in the path specified by the PATH variable (as is **cd**, **ls**, **nautilus**, and so on), so you don't need to specify the path directly. You'd only need to if you wanted to launch an executable that **wasn't** in your PATH.

---

### Post by steve.horsley on 2006-11-22
> **tocleora said:**
> 
It doesn't make sense that this code would stop firefox from going to some university's web site as this is a command line option, unless that universities web site is what you're trying to access with %u.  I would leave it in there until you have that problem, then take it out then. :)

No, it's the other way round - I see people complaining that their browser always goes to some university when launched and they think it's been hijacked, whereas it's really just that the %U has been interpreted as a seach for "university" and they have been taken to a university web site. Last I heard, it was University of Alabama.

Removing the %U from the launcher stops this happening, and doesn't seem to affect firefox's ability to open URLs.

---

### Post by tocleora on 2006-11-22
%u is a variable (I guess?) that when the launcher is launched by (I have no idea), linux(? ubuntu? gnome?) will look at the launch string, see the %u and if it has a url will replace %u with that url.  It could be in a case where firefox is your default web browser and an app was to open "http://www.google.com", it would say what is the default application for opening those?  Found firefox... Now how do I pass this value to firefox?  Oh, I see the %u so I'm going to pass "firefox http://www.google.com".  Based on my years of programming that's kind of a hoaky educated guess but hopefully it makes sense. :)

---

### Post by tocleora on 2006-11-22
> it's really just that the %U has been interpreted as a seach for "university"

Oh I see that now. I typed %U in the address bar and got arizona.edu.  Catkiller's suggestion to use quotes might resolve the problem, or it could be case sensitive and you need a lower case u instead of an upper case u, although the help full says upper case u is multiple url's, I would think that would work too.  Or take it out until you hit a moment you realize why the %u was there in the first place! :)

---

### Post by Arvoitusmies on 2007-10-31
This is what I tested:

1) Saved two web pages to my hard drive.

2) Selected those pages and dragged'n'dropped them over the firefox shortcut (%u on)
     ->It said Firefox is already running and it only opened one of them.

3) Tried the same with nothing (no %u of %U)
     -> This time it opened nothing.

4) And now tried with the %U and now it opened both pages in one window and two tabs.

So like the holp said %u is for one URL and %U for more URLs

---

### Post by meindian523 on 2007-10-31
Experimentation is the path to the truth and knowledge.:)

Hey,kewl,I don't know where that came out from......I'm not known for creativity at any rate!

---

### Post by Arvoitusmies on 2007-10-31
If you type ```
firefox "URL"
``` then it opens the URL.

---

