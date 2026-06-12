---
title: "BitchX channel switch"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by bartkl on 2007-07-07
Hi,

I'm using BitchX as IRC client and I found out I can be at multiple channels at the same time and to switch between them I seemingly have to use /channel #<channel_to_switch_to>

It works, but there's one disadvantage I _seem_ to have noticed, namely that I cannot see everything other people have said in the room I wasn't in at the moment.
Example: I'm in #room1 reading a discussion between two people. Simultanuously I'm asking for help about Ubuntu in #ubuntu. While i'm in #ubuntu asking something, I can switch back to #room1 using /channel but I can't read what's been said during while I was away.

What can I do about this?
Thanks

---

### Post by bartkl on 2007-07-07
Sorry , I now see that while I would be inside #ubuntu I can see the discussion inside #room1 through <user:#room1> ....
Nice feature. Still it could get messy while in a lot of rooms, right?

I think it's possible to run two BitchX clients simultanuously right? With the same username?
Well, I can easily try of course :).

---

### Post by 11touche on 2007-07-12
Well on bitchX to work on multiple channels, you should use the /window command.
you can create a new window by typing ```
/window new double on hide
```
This will create a new window, and hide it. If you don't specify the "hide" parameter, it will split your screen in two (which is also great sometimes when you want to watch 2 or more channels at the same time)
Then to switch between windows, you can use ctrl+w "window number", or /window next.
Once you're in an empty window, you can join a new channel and it will appear in that window. That's the best way to work under bitchX.

---

