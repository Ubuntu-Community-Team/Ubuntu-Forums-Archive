---
title: "[SOLVED] Adobe Reader libgtkembedmoz puzzle"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by malty on 2007-12-17
Adobe reader 8.1.1 ...............
"unable to find HTML rendering library (libgtkembedmoz.so.0d" then a blank "Beyond Adobe Reader window".
Using Konquerors file browser and ARs edit/prefs/internet...
   Browser executable = /usr/bin/firefox
   libgtkembedmoz folder = file:///usr/lib/firefox/lib etc  (also tried without "file://"
Prefrences window closes, no warnings.
Restart AR same problem as before.
I have tried all sorts of combinations as the browser (I am using Gran Paradiso) so Firefox 3.0, and Mozzilla 
Using the Konqueror browser I can clearly and easily select the correct file, after all it is there.
Using the AR prefs  browser (is it Nautilus?) the list of files including libmoz  are greyed out so the browser is unusable, why?
I have once had the warning "file does not exist or you do not have  permissions etc".
If the file is there on my computer then what gives? Do I really need to be root just to tell an application where a particular file is ?. I have tried logging in as root and this makes no difference, same result.
I have totally lost Firefox,although it is still installed on my system, see earlier post,Firefox disaster, if in the course of trying to resolve the problem I had ditched the libgtk file why is it showing in the Konqueror browser?
Ihave also tried the Acroread route, also greyed out.
I am the only user.
Hoping for an answer to the puzzle.
Hurry flash, we only have 48 hours to save the world
                                            Malty
PS  I have Reader 5.0 installed, it has ran 100% for 6 months.

---

### Post by nowshining on 2007-12-17
system - administration - synaptic package manager

at top click search and look for libgtkembedmoz

if not try libgtk and look thru there and find what u think u need, right-click and click and select for install - then once ur done at top click apply and review ur options, okay it to contineu and let it do it's thing, then after that try again.

---

### Post by malty on 2007-12-18
Nowshining..........
Thanks for the info, I did that already, its not in Synaptic.
                                    Kind regards               Malty

---

### Post by philinux on 2007-12-18
[http://ubuntuforums.org/showthread.php?t=585615&highlight=libgtkembedmoz](http://ubuntuforums.org/showthread.php?t=585615&highlight=libgtkembedmoz)

---

### Post by nowshining on 2007-12-18
do u don't like evince if u don't like evince u can download and try kpdf (k is for kubuntu and can run kubuntu apps on gnome and vise versa) it won't integrate well with the gnome desktop via looks, etc but it should work great. Example scollbar will be diff..

---

### Post by malty on 2007-12-18
Philinux......I tried that thread (the French connection),  did not work.

Nowshining...Evince OK but very basic, I will stick with AR 5.0 untill Adobe decides to fix the bug in 8.0.

I am still in the dark however, over why the greying out of files in Nautilus, and why a file should show in Konquerer but be greyed out in Nautilus, if indeed the browser ARs prefs uses is Nautilus. What a find a bit frustrating is the fact that Ubuntu is obviously a very good OS but the documentation, (I spent hours trying to resolve the above puzzle, nothing) both on screen and in book form is, putting it mildly, all over the place,

I bought 4 books..
                            Linux desktop pocket guide (OKish)
                            Ubuntu hacks  (pass)
                            Beginning Ubuntu linux    (pass)
                            Hacking Ubuntu  (not the current one though, its out of date)
In the time that I have been plodding through them I have read and thoroughly understand Learning Autodesk Maya 8.0 (obviously running it in windows)
Thanks for your response
                             Malty                 (confused but content)

---

### Post by viranaso on 2008-01-06
The answer to your problem is to be found at: [http://blogs.adobe.com/acroread/reference/](http://blogs.adobe.com/acroread/reference/)
I had the same message: Unable to find...libgtkembedmoz
The command given in the adobe blog showed that the required folder on my Ubuntu setup is: /usr/lib/firefox/
so I set it to that and it works.

---

### Post by BattleKat on 2008-01-21
> **viranaso said:**
> The answer to your problem is to be found at: [http://blogs.adobe.com/acroread/reference/](http://blogs.adobe.com/acroread/reference/)
I had the same message: Unable to find...libgtkembedmoz
The command given in the adobe blog showed that the required folder on my Ubuntu setup is: /usr/lib/firefox/
so I set it to that and it works. 

Thank you so much!  THAT worked perfectly.  :)

---

### Post by malty on 2008-01-22
Viranaso,
                  had not checked this post for a while, thanks, it works.
                                         Regards
                                                        Malty

---

