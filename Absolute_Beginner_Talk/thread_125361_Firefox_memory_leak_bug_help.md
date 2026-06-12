---
title: "Firefox memory leak bug help"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by towsonu2003 on 2006-02-03
I need someone to translate this weird stuff into english...

This is about this bug: [https://bugzilla.mozilla.org/show_bug.cgi?id=319262](https://bugzilla.mozilla.org/show_bug.cgi?id=319262) which is about memory leak in firefox. Comment #25 wants me to do the following:
> In reply to comment #24)
> (In reply to comment #23)
> > Check the URLs. The tools *are* on mozilla.org pages:
> > [http://lxr.mozilla.org/mozilla/source/tools/footprint/leak-gauge.pl?raw=1](http://lxr.mozilla.org/mozilla/source/tools/footprint/leak-gauge.pl?raw=1)
> > [http://lxr.mozilla.org/mozilla/source/tools/footprint/leak-gauge.html?raw=1](http://lxr.mozilla.org/mozilla/source/tools/footprint/leak-gauge.html?raw=1)

> help might be available from the link given in bug #320915 comment #28, but that server is unaccessible to me.

Sorry for my lack of care on environment where access is controled.
1. How to install
  - "Save Link As" at above link(leak-gauge.html?raw=1),
    then save it in your local hard disk.
2. How to reach help
  - Open the saved HTML, then read the page.
3. How to run the tool.
  - Open the saved HTML and click link of "enter the filename",
    then specify file name of NSPR log.
And wtf? it's confusing to me. I don't wanna turn the bug filing procedure into a newbie help forum, but it's frustrating like this. These ppl (everyone for that matter) know about the memory leak, but the bug filer gets the job done? anyway: First, whenever I open the damn terminal and set and export the variables, the variables go awol after closing the terminal. Second, I can't figure out whether to do this stuff in which order???? this: 
1. open file
2. set export variables
3. run the script (which is assumed to be safe as it's hosted by mozilla)
4. browse web for some time
5. run the script again
or 2-4-3 or what... :confused: :confused: :confused: :confused: 
And of course, I have no idea whether this is safe (although I already **did** it... :evil: :mad: )

I hate filing bugs...

PS. Now I will try to run firefox from the same terminal I export the variables in. Again, I hate filing bugs.

---

