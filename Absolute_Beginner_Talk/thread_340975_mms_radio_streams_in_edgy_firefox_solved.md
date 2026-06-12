---
title: "mms radio streams in edgy firefox solved"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by thom314 on 2007-01-18
When running dapper, I could successfully play my local radio station in firefox. It is an mms stream and it used the mplayer plugin. The mplayer plugin was a bit slow to connect up to the stream but it worked.

When I updated to edgy this ability was broken because firefox tries to use the totem plugin which does not work. If you search the forums here you will find many people with this problem and several different solutions. I tried all the suggested solutions and none worked for me. I don't know why.

This post is an FYI on how I eventually solved the problem in hopes this will help others.

- close down firefox
- open up a terminal window and: cd /usr/lib/firefox
- backup the plugins directory by: sudo cp -r plugins plugins.bak
- go into the plugins directory: cd plugins
- remove the totem plugins: sudo rm *totem*

This removes the totem plugins and firefox reverts to using the mplayer plugin which works just like it did with dapper.

Maybe there are smarter ways to do this but this worked for me and that makes me very happy. :-D

---

