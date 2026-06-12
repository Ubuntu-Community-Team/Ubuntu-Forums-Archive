---
title: "Runaway process (?) on a G4 Mini"
date: 2008-06-06
forum: Apple Hardware Users
---

### Post by gphaze on 2008-06-06
I'm experiencing  a process (or something) which is making the G4 Mini's fan go full blast, and the system monitor shows a 100% CPU load, yet the window which shows processes in list form shows nothing consuming more than about 35%.  I don't have any CPU-intensive processes going that I know of, but something is making the mini work hard.

Restarting doesn't clear things up.

I appreciate any suggestions.

Thank you!

gphz

---

### Post by gphaze on 2008-06-06
I believe I found the culprit in Top:

 4496 lp        20   0  106m 100m 3204 R 87.8 10.0  24:46.68 pdftops -level2 -paperw 612 -paperh 792 /va


the %cpu has been between about 87 (above) and as high as 91/92


anyone know what this is?

it looks like either a print job or maybe a pdf job??

gphz

---

### Post by stream303 on 2008-06-07
I don't know what started that print job, but can you just try killing it outright:

Can you just kill it outright with any of the following:  (where <pid> is the process id on the left, ie 4496?

```
kill -15 <pid>
or
kill -9 <pid>
or
kill <pid>
```

You may have to preface these commands with *sudo* possibly.

Also check out one of my favorites to download as an alternative to the regular top, HTOP.  Nice!

Did you try to print something, or does this always show up?  Btw, what version of Ubuntu are you running?

---

### Post by gphaze on 2008-06-07
> **stream303 said:**
> I don't know what started that print job, but can you just try killing it outright:

Can you just kill it outright with any of the following:  (where <pid> is the process id on the left, ie 4496?

```
kill -15 <pid>
or
kill -9 <pid>
or
kill <pid>
```

You may have to preface these commands with *sudo* possibly.

Also check out one of my favorites to download as an alternative to the regular top, HTOP.  Nice!

Did you try to print something, or does this always show up?  Btw, what version of Ubuntu are you running?


thanks for the response, stream303,

I am running hardy heron 8.04 (plus whatever updates it did right after my installation 3 days ago!)

Now, while I believe that I tried to kill the process, I'm not sure 100% that I did the command properly. I typed what you suggested the other day, and the terminal simply returned a cursor prompt.

The process in question, I believe a PDF job, has seemingly stopped of its own, or "gone away." It had stopped on its own, then resumed (with the same high CPU demands, 92% or so) a couple of times.

Hasn't resumed since yesterday evening.

I did make, or try to make a pdf of a help file, so that's where that came from, but I do not get why it was so relentless, or why it took so long to do its business; I don't yet know whether I actually now HAVE a pdf as result of all that!

I believe it was called pdf-tops in the command column.

I'm going to copy the examples of typing the kill command from your response and keep that handy.


gphaze

---

