---
title: "Compiz Closes When Terminal Does"
date: 2008-01-20
forum: Apple PPC Users
---

### Post by Wizzel on 2008-01-20
I sucessfully installed Compiz and then AWN and have run them. I have a few questions though. I start Compiz through the terminal. When I close the terminal, things get screwy. Why does the terminal need to remain open. I am trying to run AWN dock with the least amount of strain on this computer. I have an iBook G4. Any ideas on why Compiz closes when I close the terminal and is Beryl any faster/more lightweight? Thanks.

---

### Post by luisromangz on 2008-01-20
If you launch Compiz from a terminal, then the Compiz program becomes a children process of the terminal's own process. When you terminate a process (as in you close the terminal) then you close all its children processes.

You can avoid it launching the command with an & at the end, that way compiz will behave as a background process and will be unlinked to the terminal.

Beryl may be faster but it is obsoleted by Compiz Fusion, so no new developments happens for Beryl.

---

### Post by ssam on 2008-01-20
you may also need to run the command 'disown' after running it with the '&'.

is there any reason not to use system->preferences->apperence to enable compiz?

---

### Post by Wizzel on 2008-01-20
Thanks guys. Good explanations.

---

