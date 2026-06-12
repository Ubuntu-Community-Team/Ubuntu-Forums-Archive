---
title: "Remap Caps Lock to Be Backspace"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by mlissner on 2007-02-24
Hi, I'm trying to remap my keyboard so that the caps lock button works as a backspace, but I'm getting stumped. From what I can tell there are three steps to the process:
1. Tell caps lock to do the backspace button's action: xmodmap -e 'keycode 66 = BackSpace'
2. Tell caps lock not to turn on caps lock anymore: xmodmap -e 'remove Lock = Caps_Lock'
3. Make caps lock auto-repeat when held down: xmodmap '**????**'

It's that number three that's getting me. I know it can be done, but from what I can tell, the documentation for this kind of thing is completely lacking. It took me a lot of work just to figure out that backspace is properly capitalized in xmodmap as BackSpace....but I can't figure out the autorepeat thing.

I've looked at xset as well, but it doesn't seem to work.

Any ideas? 

Thanks in advance.

---

### Post by MrKlean on 2007-02-24
Did you tye going thru System...Preferences...Keyboard ?  You can make a bunch of changes there..not sure what's all in there though ; )

---

### Post by mlissner on 2007-02-24
Yeah. Tried that. No dice.

---

### Post by mlissner on 2007-12-15
Bump...it's been eight months now, and I still haven't solved this issue...anybody have any ideas on how to make it autorepeat?

Thanks.

---

### Post by rmockler on 2007-12-15
I believe this is the answer to your problem. at least it works for me.
In a terminal I entered the first two xmodmap commands exactly as you showed in your post.  Then, I entered two xset commands as follows:
xset -r 22
xset r 66

BINGO!  Auto-repeat on backspace from the Caps Lock key works great.
Try it and post your results please.

---

### Post by mlissner on 2007-12-15
Very cool. You're the man. So, now that these combinations all work, what's the easiest way to get them to all run when the computer boots? 

I have the commands in my original post in a file called Xmodmap, but I don't imagine I can put the xset commands in there. Is the usual technique for this kind of thing to put them in the gnome-sessions preferences?

---

### Post by jordank on 2007-12-15
Might i ask why?

---

### Post by rmockler on 2007-12-15
Well, my response to that question would be so that when I reboot my system those commands discussed wiil be in effect.  Right now, that doesn't happen.
I am interested in hearing the the best way to accomplish that.

---

### Post by mlissner on 2007-12-15
Yep, that's exactly why. The xset commands are only as good as your gnome session, so if they aren't run when you start your session, they don't happen...any thoughts out there?

Also, I just realized that I don't need to run xset -r 22, because I still want my old backspace to have autorepeat, so I shall leave that be.

---

### Post by rmockler on 2007-12-15
mlissner, I agree with you completely about not entering the -r 22 command, I also want the Backspace key to function as normal.  I tested with your suggestion and it's good.  Also, I did a file search on my system, and I cannot find an Xmodmap file or .Xmodmap file anywhere.  Is that where you said that you put the xmodmap commands to run on startup?  If I can get that working I have an idea on the xset statements, and I will test it as soon as I solve the xmodmap situation.  If it it works, I will post it here.

---

### Post by mlissner on 2007-12-15
I made the Xmodmap file by running xkeycaps (which you'll need to install). xkeycaps is a bit buggy, but it seems to work OK. The contents of my Xmodmap file (which lives in my home directory) are:```
!
! Make the caps lock button a backspace button
!
remove Lock = Caps_Lock
keycode 66 = BackSpace

```

---

### Post by rmockler on 2007-12-15
OK mlissner, this may be what you want.  I installed the xkeycaps program, set it up to match yours, rebooted and the Caps Lock key worked as Back Space.  So, then I did the following:

sudo gedit /etc/X11/Xsession.d/50x11-common_determine-startup

and added the line   xset r 66   to the bottom.
Really be careful with spelling that path, upper cases, -, and _ characters.
Awfully easy to miss one and not get the file.
Then I rebooted and auto-repeat was added!
Give it a try.

---

### Post by mlissner on 2007-12-16
Like a charm. That's a bit of an odd file. Why did you choose it? I'm just asking because it looks like precisely the kind of file that will get overwritten the next time I update versions. 

In any event, thanks for the help.

---

### Post by rmockler on 2007-12-16
I had saved a note that I took a while back that it's a good place to put xset commands.  I don't recall now where I came across it.  I also pondered the possibility of that file being overwritten with an upgrade, but decided it would be one of the quickest and simplest fixes that I would have to make. Although they have been ultimately worth it, the two upgrades that I have made have involved considerable time spent making fixes.

---

### Post by mlissner on 2008-05-03
I just wrote these steps up in a tutorial over on my blog, in case people are interested. [http://michaeljaylissner.com/blog/remap-caps-lock-as-backspace](http://michaeljaylissner.com/blog/remap-caps-lock-as-backspace). Windows XP instructs are there too, since *some* of us need to use XP at work.

---

