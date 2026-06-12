---
title: "running Thunderbird addressbook independently"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by qpackard on 2006-04-23
How can I access the tbird addressbook without running tbird? In win this is accomplished by adding a switch to the shortcut: thunderbird.exe -addressbook. Is there anything similar for ubuntu/linux?

---

### Post by htinn on 2006-04-23
It's basically the same thing, only you invoke it like this:

mozilla-thunderbird -addressbook

---

### Post by qpackard on 2006-04-24
Wow! It really worked. Thanks for the help. This is the first time anything straightforward has worked the first time. Most linux setup requires many commands and file edits. I was even able to create a launcher for it and send it to the panel at the top of the screen, even set up an icon for it.

For those who are wondering how, 
right-click the desktop, 
select Create Launcher..., 
select Basic
enter whatever you like for Name, Generic Name and Comment,
for Command enter mozilla-thunderbird -addressbook
or Browse to the file/command you want,
for an icon click the No Icon button (don't ask),
select an icon and click OK,
click OK.

Test your new launcher link.
To put it in the top panel left click the link and drag and drop it on the panel.

---

