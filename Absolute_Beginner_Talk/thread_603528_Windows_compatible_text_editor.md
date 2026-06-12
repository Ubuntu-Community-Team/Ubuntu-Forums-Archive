---
title: "Windows compatible text editor"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Dwood108 on 2007-11-05
Could anyone suggest a simple text editor (for linux/ubuntu) that formats line breaks in the same way that Windows does, so that I don't have to convert all my files (html, php) that I created with mousepad in ubuntu so that I can read them correctly in windows?

cheers.

---

### Post by lisc998 on 2007-11-05
> **Dwood108 said:**
> Could anyone suggest a simple text editor (for linux/ubuntu) that formats line breaks in the same way that Windows does, so that I don't have to convert all my files (html, php) that I created with mousepad in ubuntu so that I can read them correctly in windows?

cheers.

JEdit is a good one:
[http://www.jedit.org](http://www.jedit.org)
It runs on all platforms. All the devleopers I know who have been forced off Unix on to PCs tend to use it as it's fully transportable.

Of course, you need to have Java installed to run it.

Tim

---

### Post by Dr Small on 2007-11-05
I just use gEdit.

---

### Post by so7777777os on 2007-11-05
May be Kedit can do it...

---

### Post by Dwood108 on 2007-11-05
Thanks I shall try jedit.

I think gedit is the default ubuntu text editor. I have tried that to no avail.

---

### Post by Orbital75 on 2007-11-05
I like gedit a lot.... I think that Metapad works on both Linux and Windows, it's a nice
text editor as well.

---

### Post by svalding on 2007-11-05
I use Notepad ++ I can't remember if it's ported to Unix or not, but I believe it is.

---

### Post by carlosjuero on 2007-11-05
Well, the OP's issue is with how the line breaks are formatted, not necessarily ease of use/functionality. Windows uses \r\n for its line breaks (Carriage Return, New Line); *nix systems use \n for its line breaks (New Line). I think the *nix way is best, but I have run into the same sorta issue (I created a file viewer for .nfo files on Windows and had to explicitly instruct it how to handly *nix line breaks :/).

I think JEdit might work out well - Most of the others use the *nix defaults (though some might be configurable)

---

### Post by LowSky on 2007-11-05
if you install Wine it come with Windows compatable Notepad.

---

### Post by carlosjuero on 2007-11-05
> **LowSky said:**
> if you install Wine it come with Windows compatable Notepad.
Oh yeah - theres that!

That will work for the OP indeed - it is the actual Windows notepad (from Win2k I believe)

---

### Post by Dwood108 on 2007-11-05
I did think about using wine as you can use notepad with it, but would like to keep my system as simple as poss. Also having to use windows programmes kind of defeats the idea of using linux.

---

### Post by carlosjuero on 2007-11-05
Well, the options are pretty limited - most *nix text editors save in *nix format; you could always write a simple Perl script to parse the files after you work on them in Linux.. but that becomes more complication than is worth it.

The Java one might be the best bet in this scenario for you.

---

