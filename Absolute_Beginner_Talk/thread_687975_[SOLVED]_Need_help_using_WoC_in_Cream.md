---
title: "[SOLVED] Need help using WoC in Cream"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by MountainX on 2008-02-04
I want to have URLs (hyperlinks) in plain text docs. I believe WoC-Vim can provide this. How do I use it with Cream? I'm reading the docs and my head is spinning. 

I would like to have a simple text file with something like this in it that will open the URL in my browser:

Here is a link I want to jump to:
{-http://cream.sourceforge.net/-}

Thanks

---

### Post by MountainX on 2008-02-05
It turns out I don't need WoC for this. Cream will open a URL in my default browser just by typing Ctrl-Enter when the cursor is on the URL.

Here's the full info from a Cream developer:

I just committed an update that might help, copy this file over yours
of the same name:

 [http://cream.cvs.sourceforge.net/cream/cream/cream-lib.vim](http://cream.cvs.sourceforge.net/cream/cream/cream-lib.vim)

It works if you select a URL and press Ctrl+Enter, or without a
selection as long as the link has a char on either side that Vim does
not define as a filename character by &isfname (:help 'isfname). (The
link format you give above is not valid however. :)
--
Steve Hall

---

