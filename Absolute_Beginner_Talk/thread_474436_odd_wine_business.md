---
title: "odd wine business"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-06-15
I have installed wine on two different pcs, both with the same version of feisty.  Then, on running the same windows app, I get radically different results on each- one is perfect, the other is unusable.
The windows app is screenwriter, a WYSIWYG word processing program specific to screenplays. It's a bit like word or OOo Writer, but with special page formatting.  On one PC it behaves very badly and on the other, very well. 

On the pc with problems, this happens:
a) the app seems to load and run happily until I write a line that is longer than the width of the formatted page on screen. Instead of doing CR + LF it just carries on to infinity. Once the characters leave the on-screen page they disappear, but are retained: ctrl-c finds them, and ctrl-v spits them out again. 
b) the programme periodically decides to invent a system error- usually "No printer is installed". This is true- there is no printer on the PC, only on the network - but I am totally unable to close the system error window, because every time I do it opens again, ad infinitum. Any work done in the program is unsavable, and so lost.

any ideas, anyone?

---

### Post by trinaryouroboros on 2007-06-28
> **ginestre said:**
> I have installed wine on two different pcs, both with the same version of feisty.  Then, on running the same windows app, I get radically different results on each- one is perfect, the other is unusable.
The windows app is screenwriter, a WYSIWYG word processing program specific to screenplays. It's a bit like word or OOo Writer, but with special page formatting.  On one PC it behaves very badly and on the other, very well. 

On the pc with problems, this happens:
a) the app seems to load and run happily until I write a line that is longer than the width of the formatted page on screen. Instead of doing CR + LF it just carries on to infinity. Once the characters leave the on-screen page they disappear, but are retained: ctrl-c finds them, and ctrl-v spits them out again. 
b) the programme periodically decides to invent a system error- usually "No printer is installed". This is true- there is no printer on the PC, only on the network - but I am totally unable to close the system error window, because every time I do it opens again, ad infinitum. Any work done in the program is unsavable, and so lost.

any ideas, anyone?

Sure thing, first, start going down the list here (while using the baddie PC):

[http://www.winehq.org/site/docs/wineusr-guide/bug-reporting](http://www.winehq.org/site/docs/wineusr-guide/bug-reporting)

Most important to note on that list, is the following terminal commands if the program is crashing:

```
echo quit | WINEDEBUG=+relay wine [other_options] program_name >& filename.out;
tail -n 100 filename.out > report_file
```

In the above, you would remove "other_options", then replace program_name with the actual screenwriter's exe file. As well as replace report_file with whatever file name you want as the dump file (like winedump.txt for example)

Report the results (or the report file) back here.

Sidenote: It might also be a wise course of action to bring this file to the attention of the people at [http://winehq.com](http://winehq.com) and perhaps even [http://launchpad.net](http://launchpad.net) if there's any additional support base.

I only mention the two additional sites for expedited resolution. More eyes on the problem means faster results, as always.

:popcorn:

---

### Post by marpstar on 2007-06-28
Check and make sure you are running the same version on both.  I ran into a problem running DVD Shrink in Wine.  It worked perfectly in Wine 0.9.33 but wouldn't even launch an installer in 0.9.37-38.  After trying to troubleshoot it, a downgrade was necessary for me to get the program working.  Just food for thought, I suppose...

---

