---
title: "Capturing shell script error messages"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Teleboy on 2007-05-12
Hi, I'm running GCALDaemon via a shell script that calls various java bits'n peices - it errors with probs with my java - I think - trouble is the command window disappears so fast I cannot capture the messages - the GCALDaemon.log doesn't seem to be populated (0 bytes) - I know this is a GCALDaemon/Java prob but I need to understand the principle of terminal message/shell script error capture as an object lesson - this will surely happen again with another program so I may as well get it sorted in my head now - thank you.

---

### Post by heimo on 2007-05-12
Most of the time it's sufficient for me to scroll back - yes, this also works in text-mode virtual consoles - just hit shift+page up. Sometimes I want to capture standard out or standard error, in which case redirecting is what I want.

For example:
```
1>output.log 2>errors.log ls -l
```
About standard streams:
[http://en.wikipedia.org/wiki/Standard_streams](http://en.wikipedia.org/wiki/Standard_streams)

And about redirection:
[http://en.wikipedia.org/wiki/Redirection_%28Unix%29](http://en.wikipedia.org/wiki/Redirection_%28Unix%29)

---

