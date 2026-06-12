---
title: "Looking for a programme to 'unwrap' blocks of text"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by patrick1314 on 2007-03-29
Hello!

I'm looking for a piece of software to do a specific task. On Windows (shudder) I used a freeware text editor called metapad, which is a very powerful plain text editor, to this effect. It had a handy built-in function for doing it, called 'unwrap lines'. Unfortunately it's Windows only.

Here is a demonstration of what I mean (taken fron a gutenberg ebook):

Original: > It was the best of times, it was the worst of times,
it was the age of wisdom, it was the age of foolishness,
it was the epoch of belief, it was the epoch of incredulity,
it was the season of Light, it was the season of Darkness,
it was the spring of hope, it was the winter of despair,
we had everything before us, we had nothing before us...

There were a king with a large jaw and a queen with a plain face,
on the throne of England; there were a king with a large jaw and
a queen with a fair face, on the throne of France.  In both
countries it was clearer than crystal to the lords of the State
preserves of loaves and fishes, that things in general were
settled for ever.

And after unwrapping the lines with metapad:

> It was the best of times, it was the worst of times, it was the age of wisdom, it was the age of foolishness, it was the epoch of belief, it was the epoch of incredulity, it was the season of Light, it was the season of Darkness, it was the spring of hope, it was the winter of despair, we had everything before us, we had nothing before us...

There were a king with a large jaw and a queen with a plain face, on the throne of England; there were a king with a large jaw and a queen with a fair face, on the throne of France.  In both countries it was clearer than crystal to the lords of the State preserves of loaves and fishes, that things in general were settled for ever.

Metapad also inserts a space between the unwrapped lines.
Is there anything I can use to achieve this on linux?

---

### Post by Outrunner on 2007-03-29
I'm not totally sure about this but you might be able to use wine([http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)) to install and use metapad. Not sure if there's any text editor for linux that does what you need though.

---

### Post by patrick1314 on 2007-03-29
Thanks for your speedy reply!
I had thought of wine, and it should work no bother with it as metapad doesn't install, merely runs from a small .exe, but I thought I should ask for a linux equivalent before installing a potentially cumbersome programme for using a very simple, small programme.
But thanks for the suggestion - I may have to resort to it!

---

### Post by Woody@N87 on 2007-03-29
I played around with gedit and it seems that if you use replace from the search menu, then enter /n in the "search for" line and a space (actual space not the word) in the "replace with line" it might do what you want.  Turned this;

It was the best of times, it was the worst of times,
it was the age of wisdom, it was the age of foolishness,
it was the epoch of belief, it was the epoch of incredulity,

into this:

It was the best of times, it was the worst of times, it was the age of wisdom, it was the age of foolishness, it was the epoch of belief, it was the epoch of incredulity

Good Luck,
  Mike

---

### Post by annda on 2007-03-29
with this gedit replace function you will get double spaces where paragraphs should be separated - have an empty line between them.

you will get your paragraph spacing back if you replace double spaces with \n\n

someone smarter mey be able to tell you a simple command that does this using regular expressions, but unfortunately i'm not that smart - yet ;-)

---

