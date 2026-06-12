---
title: "Command Line option help"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by StRiFe10101 on 2008-04-04
So, I'm running both Dapper Server and Gutsy Destkop at home and have enjoyed experimenting and learning tons.

Today my quesitons is in reference to linux command line options, specifically with the "cp" command.  I was copying a folder with files and I used the "-i" interactive option which worked fine, but now it always asks if I'd like to overwrite regarless if I specify the "-i" option.  It's as though it always uses it now.  

How would one go about fixing that?  I want to use regular "cp -r" with out it asking if I want it to overwrite.

Thank you!

---

### Post by andrewc6l on 2008-04-04
I would bet an .rc file has aliased cp to cp -i.

To check this, at a terminal type:
  alias

If you see something like:
alias cp='cp -i'

you know that's happened. For the session, you can enter:
unalias cp

It's probably aliased in your ~/.bashrc or ~/.cshrc file (depending on your shell) - if so, you can edit that to get rid of it permanently.

---

### Post by FleetAdmiral74 on 2008-04-04
I'm no command line expert, but I know of a tool called "alias" that has to do with adding arguments by default...you might be able to use this to define cp as cp -r

EDIT: curse you andrewc6l!!! always one step ahead of me!

---

### Post by StRiFe10101 on 2008-04-04
Thanks tons guys.  I'll try that.

---

