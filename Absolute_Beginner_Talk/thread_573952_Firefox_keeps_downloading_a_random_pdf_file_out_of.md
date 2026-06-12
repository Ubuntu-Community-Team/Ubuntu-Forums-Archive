---
title: "Firefox keeps downloading a random pdf file out of nowhere!"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by Protagonistics on 2007-10-12
So I'm using my StumbleUpon button, which I'm sure many of you are constantly clicking, and every once in a while a PDF opens- without warning, and COMPLETELY unrelated to the site I am stumbling to (it has happened three times now). I saved it once but changed the name. The pdf is a rather useful set of commands for the terminal in linux, only one page long. I have the firefox download toolbar or whatever its called, and I have ended up closing the download each time I get it so I haven't gotten a chance to see the source address of the file.

has anyone experienced anything like this?


or am I just crazy...

---

### Post by por100pre1 on 2007-10-12
You are not insane, but it seems the extension actually is. Try disabling the extension or clean its settings. Backup your settings first ( just in case):

```
cp -R .mozilla .mozilla_backup
```

---

### Post by Protagonistics on 2007-10-12
I just deleted FF's download bar and reinstalled it. Oddly, as SOON as I reinstalled it, the pdf reappeared in it. I didn't even change pages!

the source url is this:
[http://fosswire.com/wp-content/uploads/2007/08/fwunixref.pdf](http://fosswire.com/wp-content/uploads/2007/08/fwunixref.pdf)

wtf??

---

### Post by por100pre1 on 2007-10-12
Look inside the ~/.mozilla/firefox folder check if there are settings for that extension and try removing them. If the problem persists, Make a new profile:

```
firefox -ProfileManager
```

and move the most important settings to the new profile. :-k

---

### Post by Protagonistics on 2007-10-12
How am I supposed to know what settings might set it off? btw, what are the "Chrome" folders in FF for? I can't read code so I don't know how to know if something is wrong in the plethora of files...


also. "firefox -profilemanager"  doesn't do anything except open a new browser of FF.

---

### Post by por100pre1 on 2007-10-12
> **Protagonistics said:**
> 
 "firefox -profilemanager"  doesn't do anything except open a new browser of FF.

I didn't post "firefox -profilemanager" I posted this:

```
firefox -ProfileManager
```

uppercase and lowercase matters a lot here. ;)

---

### Post by Protagonistics on 2007-10-12
damn caps. problem seems to have dissapeared... for now.

And I Pasted that into Terminal and it just opens a browser.

---

### Post by por100pre1 on 2007-10-12
> **Protagonistics said:**
> damn caps. problem seems to have dissapeared... for now.

And I Pasted that into Terminal and it just opens a browser.

Weird, it should open the profile manager... :-k

---

### Post by jordanmthomas on 2007-10-12
The problem is with stumbleupon.  It preloads the pages you're going to stumble onto I believe, and when it comes across a pdf it loads it up.

Whenever this happens you can stumble a few times until you actually stumble across the pdf that keeps being downloaded and the problem will go away for a little while at least.  Not a solution, but I'm just letting you know you're not crazy.  This is the main reason I no longer use stumbleupon.  (Well, that and the hours upon hours I wasted with it)

---

### Post by Jerry N on 2007-10-12
OK - what the heck is a "stumbleupon"? I have been using Firefox for years and I have never heard of "stumbleupon".

Jerry

---

### Post by Malibu Illusion on 2007-10-12
[http://www.google.co.uk/search?hl=en&q=stumbleupon&btnG=Google+Search&meta=](http://www.google.co.uk/search?hl=en&q=stumbleupon&btnG=Google+Search&meta=)

Google first, post after.

---

### Post by Protagonistics on 2007-10-12
Stumbleupon is better than youtube. just go to stumbleupon.com and read up on it.

thanks for the help everyone.

---

