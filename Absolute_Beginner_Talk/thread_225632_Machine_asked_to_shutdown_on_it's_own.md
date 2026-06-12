---
title: "Machine asked to shutdown on it's own?"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by Scintillement on 2006-07-30
Whilst using my machine, browsing the web, suddenly the prompt box with choices that shows up when I go to shut down appeared on it's own.

I was startled so I started to futz around looking at logs and stuff for the first time. Under "messages" there was an entry about some "cron.daily" thing as well as one for "exit at 15" or close to that.

I don't know what any of this means.

Whilst browsing the web I was asked what I wanted to do with a .php file, as though I were trying to download one. I was not. I don't even know what a .php is. I hit cancel on that.

Any ideas what this is all about?

---

### Post by Scintillement on 2006-07-30
A bump before bed.

---

### Post by Scintillement on 2006-07-30
An afternoon bump. (I hope it's okay to bump my topic if it falls a few pages down)

---

### Post by Scintillement on 2006-07-31
Bump-o-rooni.

---

### Post by scxtt on 2006-07-31
cron jobs are the result of the cron daemon running commands at a specified time according to how it's set up ... basically, you can 'program' your computer to perform specific tasks at certain times as if you were sitting there running the commands yourself ... there's generally cron.daily, cron.weekly, and cron.monthly folders in /etc where you can put scripts while will be run accordingly ...

so if you haven't 'messed with' your crons, chances are this has nothing to do w/ your random 'do you want to logout' problem ...

i have "exiting on signal 15" in my /var/log/messages file, and i don't have your problem - so i doubt that's related ...

as for the php thing, i could only see that happening as the result of you vising a website where apache/php isn't configured properly, which is a problem w/ their server, not your box ...

---

