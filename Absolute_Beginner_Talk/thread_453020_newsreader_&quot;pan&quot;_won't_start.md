---
title: "newsreader &quot;pan&quot; won't start"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by dbvanhorn on 2007-05-23
Well, that's it in a nutshell, when I try to launch pan, nothing seems to happen at all. 
It's installed, and it has run in the past, but apparently it's on strike.

No error messages that I can see, nothing at all.

---

### Post by dbvanhorn on 2007-05-24
anyone.... anyone at all?

---

### Post by andyclaxn on 2007-05-29
What can I tell you? exactly the same thing happened to me, so i backed up everything to an external hard drive and re installed Fiesty Fox and Pan. That worked, but a bit of a pain!
If anyone can find a quicker fix I too would be very grateful.
Aye
Andy

---

### Post by mpitt on 2007-07-08
I just experienced this exact problem.  Pan seemed to crash and close out of the blue and it will not restart.  After restart and an uninstall and reinstall.  It still will not start up.  I came here to search the posts assuming it might be a common problem and to hope a sophisticated solution was found by someone much more adept at Ubuntu and linux than I.   The solution found so far is not what I consider sophisticated. 

[no offense andyclaxn.  The reply with a working solution is still very appreciated.  i hold out hope for a better solution]

---

### Post by confused57 on 2007-07-08
If you're using Pan from the repositories, you might try installing the latest beta version:
[http://ubuntuforums.org/showthread.php?t=223779&highlight=Pan](http://ubuntuforums.org/showthread.php?t=223779&highlight=Pan)

---

### Post by mpitt on 2007-07-08
Thanks confused57, that did the trick.

You have restored my faith in the power of the collective community knowledge base.  That was a great idea.

---

### Post by ferieguru on 2007-07-11
> **dbvanhorn said:**
> Well, that's it in a nutshell, when I try to launch pan, nothing seems to happen at all. 
It's installed, and it has run in the past, but apparently it's on strike.

No error messages that I can see, nothing at all.


Had the same problem. Solved it this way.

Did show hidden files in my home directory, and found a folder named ".pan2", opened that one, opened the folder "article-cache" and deleted all the files in that folder. Started Pan as normal again.

---

### Post by mpitt on 2007-07-19
Wow, that's awesome.  When I encountered the problem, I figured that it was leaving behind a corrupt file even after an uninstall but I had no clue how to find it.  Great Job!!!

This forum is fan-freaking-tastic!

---

### Post by rmd6457 on 2008-03-22
My Pan newsreader would start briefly and then immediately shut down. 

I tried deleting the cache files in pan2 but it didn't fix the problem.

I uninstalled Pan with Add/Remove, and then completely deleted pan2.

I re-installed Pan, and it now started correctly. 

I had to re-enter my news-servers and newsgroups.

Ross

---

