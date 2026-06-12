---
title: "firefox dies"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Joseph5000 on 2008-03-21
firefox dies on me constantly. I need to restart my computer at least 3 times per day. I never had this problem under MS. Everybody told me how cool Ubuntu is, (ups, don't wanna go to rants) It's just really frustrating. even if Ubuntu boots faster. What can I do to get a stable computer??? Firefox??

---

### Post by zakirs on 2008-03-21
u explain how is it crashing .. i mean when specifically

---

### Post by Joseph5000 on 2008-03-21
I think it is when I have too many windows open, MS could handle that. I already changed to Deluge away from Azureus and that helped for a while, but now it's all back to slow, slow, slow. to the point where I have to reboot because firefox won't simply load anymore.

---

### Post by Joseph5000 on 2008-03-21
Just right now I had to re-boot. And even then it's like it's s tuck somewhere it took a few minutes and then all of a sudden Firefox starts up. All other applications run fine.

---

### Post by 3rdalbum on 2008-03-21
Why not try something other than Firefox? Epiphany and Konqueror are good web browsers. There's an incompatibility between Flash and Nvidia which occasionally causes me the same problems you describe (but much less often); I switched to Epiphany and I've not had a problem since.

---

### Post by Joseph5000 on 2008-03-21
Alright, is it in my package?

---

### Post by Joseph5000 on 2008-03-21
Are there no other ways, I like firefox and I have tons of bookmarks and all that stuff. Lots of hassle.

---

### Post by Joseph5000 on 2008-03-21
This is the message I get

joseph@ubuntu:~$ sudo apt-get install epiphany-browser
[sudo] password for joseph:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
joseph@ubuntu:~$

---

### Post by Mustard on 2008-03-21
> **Joseph5000 said:**
> This is the message I get

joseph@ubuntu:~$ sudo apt-get install epiphany-browser
[sudo] password for joseph:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
joseph@ubuntu:~$

This usually means that you are attempting to use apt-get in command line while you are running the Synaptic Package Manager GUI.  Close the Synaptic Package Manager and then try the command line again.

The Synaptic Package Manager is the GUI frontend for apt package management, so it doesnt allow you to run both at the same time to avoid conflicts.  The 'lock' file error is telling you that apt-get is locked while another program is using it.

---

### Post by Joseph5000 on 2008-03-21
Beginners luck, but do I have to abandon Firefox?? Epiphany doesn't have a google search box. And I really love that part

---

### Post by Mustard on 2008-03-21
> **Joseph5000 said:**
> Beginners luck, but do I have to abandon Firefox?? Epiphany doesn't have a google search box. And I really love that part

I'm not really sure whether you need to abandon it or not, but the sparse descriptions you are giving don't really give many clues as to what the problem might be.

It sounds vaguely like a problem I have read about people having with systems that just begin to crawl after a while.  This is not a very common problem with Ubuntu, but it does occur.  It would really be necessary to look more deeply into your problem to give any definitive answers.

---

### Post by FreewareFan on 2008-03-21
OK, when I started using Firefox 2 that was installed with Gutsy 7.10, I had the same exact problems when I ran it.  Over a period of time, what I noticed on my system, was that Firefox was most likely to freeze up on me when I was either typing an address on the address bar and it was trying to autocomplete, or when I was typing a search word in the search bar and it was trying to autocomplete.  After I noticed that, I started experimenting around, and found out, that sure enough, it had something to do with the history function of Firefox.

So, because I too really like Firefox, what I did was to disable the history function completely.  And you know what?  Never froze my system or crashed on me again after that!

Now, something else to make note of..  Just yesterday I installed version 3 beta 4 of Swiftweasel, which is Firefox, but specially made to work in linux.  I'm happy to report that now I can use the history function without any freezes, and it is much , much , much faster that Firefox 2 ever was, and the graphics are crisper and cleaner.  And you know how long it takes for Firefox 2 to start running?  Well, Swiftweasel 3 beta 4 starts up almost immediately, like in 3 seconds!

So, all that to say this:  You have two possible solutions...  Disable the history functions both in the address bar and in the search bar, and that will likely take care of your problems.... Or, give Swiftweasel 3 beta 4 a try....  I personally highly reccomend the second option.   When you install it, it will NOT overwrite anything you have in connection with Firefox 2, so you're safe there, and you can import your bookmarks and such...

If you want it, it's here: [http://sourceforge.net/project/showfiles.php?group_id=195473](http://sourceforge.net/project/showfiles.php?group_id=195473)

Hope this helps!

FwF

---

