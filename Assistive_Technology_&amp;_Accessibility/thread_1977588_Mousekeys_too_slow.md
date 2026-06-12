---
title: "Mousekeys too slow"
date: 2012-05-10
forum: Assistive Technology &amp; Accessibility
---

### Post by brubru777 on 2012-05-10
Hello,

I've enabled mousekeys. However, it's unusable because it's much too slow. I have put the maximum acceleration and sensibility in the config panel but it didn't change anything.

Does anyone know how to make it work properly, please ?

---

### Post by jamesmika on 2012-05-20
Same problem here. Totally unusable as it's too slow. Did not found a solution yet :(

---

### Post by sydneyw on 2012-06-08
I'm having exactly the same problem. Ideas anyone? I tried changing the mouse speed to no avail. The cursor moves at about 9 pixels per second.

I'm using a gamer's keyboard (steelseries). Don't know if that makes any difference.

---

### Post by eronde on 2012-07-10
Here the same problem.

In ubuntu 11 there was an option to increase the speeds of mousekeys,  But I can't find the option in 12.

---

### Post by TODDMAN on 2012-08-09
Same here! Is their a fix yet?

---

### Post by sydneyw on 2012-08-10
You can play around with xkbset for the right settings. Found the answer here:

[http://www.exuro.co.uk/2012/07/114/]("http://www.exuro.co.uk/2012/07/114/")

> Firstly open a terminal window and type the following to install the xkbset package:

    sudo apt-get install xkbset

A simple one line command can then be used to configure the acceleration:

    xkbset ma [delay] [interval] [time to max] [max speed] [curve]

For those new to command-line interfaces, the brackets imply that they need to be replaced by a numerical value, tailored to suite a particular use. I have recently used the following for my configuration:

    xkbset ma 60 10 10 20 10


---

### Post by sydneyw on 2012-08-10
That particular setting turned out to be too fast. A better setting for me was:

xkbset ma 60 10 10 5 2

---

### Post by bogustrumper on 2013-01-08
Sorry to resurrect an old thread, but since the above is relevant to my issue I thought I'd repost.

I'm using mousekeys and a cheap wireless keyboard to use Ubuntu as a living room PC. Works great for most of what I want. However, I'm having a problem with mousekeys that's very closely related to this.

I go through and set up everything using xkbset to get the cursor smoothly moving across the screen. Then I decide "Hmm, I need to right click. OK, press -, then 5 will be right click. OK, now time to press / and make 5 a left click again. Why, oh why, does my cursor jump all over the place now?"

So, basically, after every press of / * - to change which button mouseclicks is simulating, I  have to re-run xkbset. Really, really frustrating. If someone points me to a bugzilla page for this, I'd appreciate it. I'm tracking down all kinds of weird stuff related to mousekeys... seems like it's a neglected feature that's working its way out.

Here's a diff of the results of "xkbset q" before and after changing the button:

```
bogus@trumper:~$ diff xkbq_Working.txt xkbq_AfterButtonChange.txt 
14,17c14,17
< Mouse-Keys Acceleration Interval = 10
< Mouse-Keys Acceleration Time to Max = 10
< Mouse-Keys Acceleration Max Speed = 5
< Mouse-Keys Acceleration Curve = 10
---
> Mouse-Keys Acceleration Interval = 100
> Mouse-Keys Acceleration Time to Max = 1
> Mouse-Keys Acceleration Max Speed = 50
> Mouse-Keys Acceleration Curve = 50
```

Any help with how to get these settings to stick around through normal mousekey use would be appreciated.

---

### Post by wyatt8740 on 2013-01-16
> **bogustrumper said:**
> Sorry to resurrect an old thread, but since the above is relevant to my issue I thought I'd repost.


Well... Since you bumped, i will add that I have this issue too :P

---

### Post by Sef on 2013-01-17
> Sorry to resurrect an old thread, but since the above is relevant to my issue I thought I'd repost.

It's ok because the thread is less than a year old.

---

### Post by bogustrumper on 2013-01-19
OK. So, anybody have a workaround?

I've thought of two. The first (and worst) is to put in a cronjob to run as often as possible to basically run this command:

```

xkbset ma 5 10 10 5 10

```

That would be overkill, though. 

I've also thought about just re-directing the / * and - keys to run a script, but so far I haven't made progress on that. They seem already captured at a pretty low level.

Barring any tips on getting Workaround 2 to work or a suggestion on a 3rd attempt, can anybody offer any insight into which package this should be reported against?

---

### Post by Grandsome on 2013-01-20
> **bogustrumper said:**
> Sorry to resurrect an old thread, but since the above is relevant to my issue I thought I'd repost.

I'm using mousekeys and a cheap wireless keyboard to use Ubuntu as a living room PC. Works great for most of what I want. However, I'm having a problem with mousekeys that's very closely related to this.

I go through and set up everything using xkbset to get the cursor smoothly moving across the screen. Then I decide "Hmm, I need to right click. OK, press -, then 5 will be right click. OK, now time to press / and make 5 a left click again. Why, oh why, does my cursor jump all over the place now?"

So, basically, after every press of / * - to change which button mouseclicks is simulating, I  have to re-run xkbset. Really, really frustrating. If someone points me to a bugzilla page for this, I'd appreciate it. I'm tracking down all kinds of weird stuff related to mousekeys... seems like it's a neglected feature that's working its way out.

[...]

Any help with how to get these settings to stick around through normal mousekey use would be appreciated.

I have that issue too, my solution was to use the "watch" command every second so basically I did:

```
watch -n 1  xkbset ma 60 10 10 5 10
```

You could try to run it at startup, I haven't tested that yet.
For more info in the "watch" command go [here]("http://manpages.ubuntu.com/manpages/lucid/man1/watch.1.html").

---

