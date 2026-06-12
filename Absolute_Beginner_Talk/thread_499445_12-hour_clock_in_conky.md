---
title: "12-hour clock in conky"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-07-12
Hello,

I just recently was able to get conky installed and working perfectly on my machine.  I am now in the process of editing the example configuration file i used initially and i have run into a few snags:

1) I do not like reading a 24-hour clock.  Im sure it is a very simple fix but i cant figure out how to change the time from 24 to 12-hour config.

2)toward the bottom of my conky monitor, where it shows me the available space left on my partitions, It shows ROOT:
HOME:
SLACK:

What is slack and if i want to remove it, how do i?  Ive already tried going in and commenting out that part but i cant get it to work, the only thing i got commented out correctly was the  ${offset 240}.  Do i need to put the "#" before or after the "$" to make it not show up?

---

### Post by Seisen on 2007-07-12
Post your conky config file.

---

### Post by corney91 on 2007-07-12
12-hour clock should be something like this:```
${time %I:%M %P}
```

Anything after TEXT is shown, so commenting won't work, you can just delete it though. Unfortunately I have no idea what slack is but you can check the folder it's in in .conkrc

---

