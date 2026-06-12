---
title: "Why does Firefox v1.5.0.5 crash whenever I surf inside www.aljazeera.com?"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-08-03
Hello all!

I have the following problem:

1. I move to the site: [www.aljazeera.com](www.aljazeera.com)

2. I click on the link named "GCC-China wrap up free trade discussions".
(it is lying on the right side of the page - in blue font color)

The problem is the following:

The page does not load completely!
It stops when it has reached around 80% of loading.

I can not scroll down to read the article...

The "stop" & "refresh" buttons in Firefox's Standard Toolbar do not respond.

And in the end Firefox crashes!!!

The only thing I can clearly outline is that there is a java picture somewhere in there, cause I see the java "coffee cup" loading, but no picture loads after that...

Is that the problem?

Any ideas?

Thanks.

---

### Post by jrb114 on 2006-08-03
I had a similar problem with java news headlines going to [www.telegraph.co.uk](www.telegraph.co.uk)

I ahd to remove java (and the plugin for mozilla) and reinstall it. I think I tried reinstalling all the mozilla plugins too. You can check the status of your plugins in firefox by typing:

```

about:plugins

```

In the address bar.

As for solving the problem, I'm not sure what package I had installed, but have you tried BUMPS?

[http://www.ubuntuforums.org/showthread.php?t=181251](http://www.ubuntuforums.org/showthread.php?t=181251)

You can get it to reinstall all the multimedia plugins, and my java now works perfectly.

Good luck!

James

---

### Post by dvarsam on 2006-08-03
Dear "jrb114",

Thanks for your reply!

It took me forever to install "Bumps"...

However, when finally finished installing it, I realized that it did not get me anywhere!

I am still having the same problem!!!

Any other ideas?

Thanks.

---

### Post by eXisor on 2006-08-03
Probably it is an MTU issue. Optimise your MTU using one of the many tools around.

But.... this thread seems ripe for a conspiracy theory, so here goes....

Could it be the page doesn't load because:

1) The CIA watches all traffic to the site and is messing up your Firefox while gathering your details?
2) The CIA doesn't want you to see that page and have messed with the site's certificates?
3) The site knows your on a western based ISP and has blacklisted you?
4) The site is so busy streaming gruesome videos it just cant service another client?
5) v1.5.0.5 is unstable and was replaced today by v1.5.0.6.

---

### Post by yman on 2006-08-03
try configuring the Java consol so it shows up whenever you load a page with java. read what it says and see if there are errors. maybe the problem is in the applet. I dought it, because then they would probably remove it immedietly, but its worth a try. however, I don't remmember how to do. in windows I would go to program files/java/ and search for executables with java icons and run them and search for the option that enables it. but maybe you could left click on the icon of java in firefox (or wherever it is when you load applets) and try the options you get there.

---

### Post by dvarsam on 2006-08-03
Dear "eXisor",

thanks for your reply!

> **eXisor said:**
> Probably it is an MTU issue. Optimise your MTU using one of the many tools around.

Excuse me for my ignorance, but what is an MTU?

And how do I optimize it?

Which tool should I install?
(is it a package I am missing?)

> But.... this thread seems ripe for a conspiracy theory, so here goes....

Could it be the page doesn't load because:

1) The CIA watches all traffic to the site and is messing up your Firefox while gathering your details?
2) The CIA doesn't want you to see that page and have messed with the site's certificates?
3) The site knows your on a western based ISP and has blacklisted you?
4) The site is so busy streaming gruesome videos it just cant service another client?
5) v1.5.0.5 is unstable and was replaced today by v1.5.0.6.

You never know, do you...?

Have you tried loading that page?

Does this happen to you too?

Thanks.

---

### Post by dvarsam on 2006-08-03
Dear "yman",

Thanks for your reply!

> **yman said:**
> Try configuring the Java consol so it shows up whenever you load a page with java.
Read what it says and see if there are errors.
Maybe the problem is in the applet.

How do I configure the Java console, so that it shows up whenever I load a page with java?

Do I need to install a package, or what do I type in the Terminal?


> I dought it, because then they would probably remove it immedietly, but its worth a try.
However, I don't remmember how to do.
In windows I would go to program files/java/ and search for executables with java icons and run them and search for the option that enables it.

Does anybody know how to do this in the Linux Environment?
(Maybe I will try to open the same link from a Windows OS to see whether I get the same problem...)
(Who knows, if it does happen in a Windows OS too, it might be a "CIA conspiracy"...
Besides, if China is limiting what its citizen's can read, what makes you think that the US is more "angelical" oriented...?)

> But maybe you could left click on the icon of java in firefox (or wherever it is when you load applets) and try the options you get there.

I tried to right-click on the icon of java & nothing happened...

...except the crash of Firefox that happened again!

Thanks for all your help,

dvarsam

P.S.> The problem is that every time Firefox crashes, and I perform a "Force Quit". all Firefox's windows close & I need to start everything all over again!

---

### Post by yman on 2006-08-06
try going to a different site with a java applet, like the game ["need for madness"]("http://www.radicalplay.com/madness/pgame.html") for example, and see if it crashes or not.

---

### Post by huggy77 on 2006-12-06
i am surprised this thread has stayed on point...

i was trying to come up with something like "perhaps firefox has a built in "terrorist-blocker" but to no avail....

---

### Post by Chinkostu on 2006-12-06
stayed on point and probably resolved, only to be bumped 4 months later ;)

---

### Post by ropers on 2007-02-17
is this issue still live? 

If yes, then you could try installing the AdBlock Plus add-on and then blocking 
*217.26.193.130/*

I found that somehow Al Jazeera English never stopped loading in Firefox/Ubuntu (apparently it tries to load some advertisements that are unavailable and never gives up), but blocking the above did it for me. 

Of course: Y.M.M.V.

---

