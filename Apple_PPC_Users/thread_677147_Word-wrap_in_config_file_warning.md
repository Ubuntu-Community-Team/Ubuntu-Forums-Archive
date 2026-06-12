---
title: "Word-wrap in config file warning"
date: 2008-01-24
forum: Apple PPC Users
---

### Post by stream303 on 2008-01-24
I thought I'd mention something that has bitten me in the past when editing config files.

I like to turn OFF wordwrap to make sure that long lines don't get wrapped and the syntax of config files throws up an error, or worse yet just ignores the the syntax of wrapped lines.

This used to bite sometimes until I actually cat'ed the file since I wouldn't notice it when using the same editor to review my changes with word-wrap on.  It looks normal.  Nice catch-22.

I guess it all depends on how your editor word-wraps, but that is one reason I use things like
```
nano -w <filename>
```

out of habit.

---

### Post by schaumkeks on 2008-01-24
Linewrapping normally is ok, but nano does a hard wrap by inserting newlines into the file and this can be a real pain. So I simply included
```
alias nano='nano --nowrap'
```
in my ~/.bashrc

Bye, Sven

---

