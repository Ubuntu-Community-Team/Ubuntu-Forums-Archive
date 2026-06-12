---
title: "Unable to get into Ubuntu Forums"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-08-20
The main computer I use--my laptop--suddenly became unable to access the Ubuntu support forums around two days back. Since then, I've been unable to get into any Ubuntu support forum page with it. I can do so with any other computer. And my laptop, which cannot open any Ubuntu support forum page for the last two days, is able to open any other page on the web without any problem. So what's going on? Why can't my laptop open any Ubuntu support form page?

---

### Post by Dr Small on 2007-08-20
Somebody lynched yor browser, sonny.
Did you try another browser?

---

### Post by swarup on 2007-08-20
> **Dr Small said:**
> Somebody lynched yor browser, sonny.
Did you try another browser?

What does that mean, "lynched my browser"? Does it mean someone hacked my computer?

And by "browser", do you mean my Firefox? Does this mean the Firefox application has been corrupted by someone?

So by "another browser", do you mean another browser application besides Firefox? If so, which one do you suggest I try?

---

### Post by Hobo Joe on 2007-08-20
Are you using firefox?

---

### Post by alienexplorers on 2007-08-20
By lynching your browser I think he meant your browser bit the big one.  Try Opera if you have it installed.  If that works try reloading firefox.

---

### Post by swarup on 2007-08-20
> **Hobo Joe said:**
> Are you using firefox?

Yes.

---

### Post by g2g591 on 2007-08-20
try reinstaling ff

---

### Post by Dr Small on 2007-08-20
Well first off, in order to effectively solve a problem, we must know facts, as to what you might have done before hand to have the browser ruined. No, I don't think someone hacked you, Ubuntu is tight.

But, try Opera or Konqueror, or some other browser, and see if you can access Ubuntu forums, if you can, it is the browser. If you can not, we must look more effectively at your system, because it is a system problem, rather than a browser problem.

And, just for giggles :p

---

### Post by swarup on 2007-08-20
> **alienexplorers said:**
> By lynching your browser I think he meant your browser bit the big one.  Try Opera if you have it installed.  If that works try reloading firefox.

Please instead of using vernacular like "bit the big one", use a straight term so I can understand what you are saying. Do you mean you think my Firefox is "corrupted"? If so, are you suggesting it spontaneously became corrupted on its own, or that someone else did it (is that what the other fellow meant by "lynched your browser"?)? 

It seems odd that the Firefox browser is corrupted, since it can go just fine to any other site on the entire web, besides the Ubuntu support forum pages. 

If I reload Firefox, am I going to lose all the bookmarks I've created since May when I started using this operating system?

---

### Post by Dr Small on 2007-08-20
Just make a backup of all your bookmarks, which should be located under $HOME/.mozilla/firefox/*default*/bookmarks.html

Or, before you do that, try installing another browser to see if it is Firefox or a system problem.

---

### Post by swarup on 2007-08-20
> **g2g591 said:**
> try reinstaling ff

Will I lose all my bookmarks?

---

### Post by Dr Small on 2007-08-20
Possibly, although probably not. But please read my previous post, and make a backup of your bookmarks first.

Dr Small

---

### Post by swarup on 2007-08-20
> **Dr Small said:**
> Just make a backup of all your bookmarks, which should be located under $HOME/.mozilla/firefox/*default*/bookmarks.html

Or, before you do that, try installing another browser to see if it is Firefox or a system problem.

Alright, I'll install another browser. If I can get into the Ubuntu support forum using the other browser, I'll write back to this thread from there.

---

### Post by st33med on 2007-08-20
IF you did not get the text image downloaded, it means it 'died'. Someone messed it up, messed itself up on it's own, or haxors got into it (unlikely).

Best to reinstall.

---

### Post by Dr Small on 2007-08-20
> **st33med said:**
> IF you did not get the text image downloaded, it means it 'died'. Someone messed it up, messed itself up on it's own, or haxors got into it (unlikely).

Best to reinstall.
Lol. I'm glad somebody caught on. :p
it took me a whole 10 minutes to draw that :D

---

### Post by g2g591 on 2007-08-20
I am 85% sure you won't lose bookmarks,they are in a hidden folder in your home directory, **but** now I don't think that reinstalling is the answer

---

### Post by Dr Small on 2007-08-20
I don't either. That's why I suggested trying another browser. That will be the ultimate test, to figure out what his problem is.

Dr Small

---

### Post by st33med on 2007-08-20
I've reinstalled apps dozens of times before, and it doesn't remove the configuration files. The only way to remove configuration files is by adding '--purge' to 'apt-get remove'.

---

### Post by swarup on 2007-08-21
> **st33med said:**
> I've reinstalled apps dozens of times before, and it doesn't remove the configuration files. The only way to remove configuration files is by adding '--purge' to 'apt-get remove'.

OK-- I installed another browser: Epiphany. It works fine, I'm able to get into the Ubuntu Support Forums (which I was unable to do with my Firefox). So it sounds like I need to reinstall Firefox. I guess I could just do that from within Add-Remove programs right? I don't need to go into a terminal window to do this, do I? Or by using Add-Remove am I going to have the problem the my configuration files will not be removed, as you mention above?

--(later) I just went to Add-Remove to remove and then reinstall Firefox. But Add-Remove says it cannot remove Firefox because other aplications depend on it. So it says if I want to remove it, I'll have to do it through Synaptic Package Manager. Should I do that, or am I going to ruin other applications by so doing? Anyway, I don't see any option, since Firefox is not working right now. So I guess I'll just go ahead, remove and then reinstall Firefox using the Synaptic Package Manager. If it would be better to do it through a terminal window ie using a "purge" command, then please someone tell me the EXACT and full line command to do the removal, as well as the reinstall using terminal. Thanks.

---

### Post by swarup on 2007-08-21
If someone can just tell me the full command in terminal for purging, removing, and reinstalling Firefix in a terminal window, then I'll just do that.

---

### Post by swarup on 2007-08-21
I'm adding on this reply for the record, so anyone who checks this thread will know that what was suggested yesterday does indeed work just fine. I went into Synaptics Package Manager, instructed it to "reinstall" Firefox, and the job was done. It reinstalled Firefox, and now I can browse again to any website without any problem. Thanks to all who helped me in solving this problem

---

### Post by Dr Small on 2007-08-21
Good. It looks like something just malfunctioned in Firefox, and caused it not to work.
I've had it happen plenty of time to me in the past, so that's why we kept suggesting other browsers to test and see if it was a system problem or browser problem.
But I am glad it was just a browser problem ;)

Dr Small

By the way, the command to clear out the config files, is:
```
sudo apt-get remove firefox --purge
```
I think.

---

