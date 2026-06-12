---
title: "cannot see images on monitor"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by nsmith on 2006-04-20
I took my computer too work because I do not have an internet connection at home and did some updates to my computer.  I also changed the screen resolution.  I took my computer back home and I cannot see after the login screen.  I tryed the fallowing 

sudo dpkg-reconfigure xserver-xorg

but it was not successfull in resolving my problem.

Any suggestions

---

### Post by pbaehr on 2006-04-20
Did you use a different monitor while at work? Is it a possibility that your home monitor can't support the resolution that you set while you were at work? Maybe try changing it back to what it was before.

---

### Post by nsmith on 2006-04-20
how can I change the resolution without logging on?

I tried sudo dpkg-reconfigure xserver-xorg

and the resolution is selected there but now I am lost and do not know what to do.

---

### Post by pbaehr on 2006-04-20
I think you need to edit /etc/X11/xorg.conf. It has a list of allowed resolutions for each screen mode under the "Screen" section. But if I'm not mistaken that would be the same effect as setting the resolutions using sudo dpkg-reconfigure xserver-xorg. I'll look into this further in case no one else comes along with a solution for you.

---

### Post by pbaehr on 2006-04-20
I looked into it a bit. When you say "the resolution is selected" when you run dpkg-reconfigure xserver-xorg is it the highest resolution selected? Try deselecting anything higher than that and then restart xwindows. That should force it to use the one you want. If that doesn't work maybe it's something other than resolution?

---

### Post by nsmith on 2006-04-20
OK there is a higher screen resolution selected also I will try and deselect it.  Thanks for the help.

---

### Post by pbaehr on 2006-04-20
My pleasure. I'd be curious to hear if that gets it working.

---

### Post by nsmith on 2006-04-20
Thats a negative.

In fact now it is worse.  It is entirely black on the login screen now and I cannot change it back.

Still open for ideas.

---

### Post by nsmith on 2006-04-20
I have switched monitors to verify that I do not have a hardware problem.  The monitor works with windows systems but not with Ubuntu.  As previously stated it was working great.  I did an update with a different monitor at work, enabled multiverse, downloaded acrobat reader and wine.  Could any of those things be the problem?  This happened with another monitor that I had also.  I ended up switching monitors to the one I currently have.  Please help.

---

### Post by pbaehr on 2006-04-20
Damn. I was hoping the resolution thing would work. Silly question, I know, but I've seen it happen before...

Do you have more than one video card in your system? If so, could you have possibly hooked your monitor up to the wrong one when you put it back in? Like I said, probably not the case, but once I was troubleshooting for someone for hours and that turned out to be the problem.

Acrobat and Wine don't seem like the culprits. The most suspicious thing to me is the resolution. I hope someone else can help better than I did. Good luck.

---

