---
title: "Pidgin synchronisation and log files placement ???"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by fox1 on 2007-07-26
1. Where does Pidgin places log files in Ubuntu?

2. Using msn accounts simultaneously and an ICQ account. When opening Pidgin about 30 little windows open up saying:

" [email]example@homtail.com[/email] on the local list is inside the group 'MSN' but not on the server list. Do you want this buddy to be added? "

There is a pop up of this for each contact on that MSN account. The only recent changes I have made after installing Pidgin is renaming the group "individuals" to "MSN". After that Pidgin makes another group "Individuals" (again) with all the contacts I already have in MSN account (that I made by changing the name of Individuals to MSN)

Does anybody have an answer to this problem?

Thanks

---

### Post by NESFreak on 2007-07-26
logs: ~/.purple/logs

you get the error because your local contact list is out of sync with the server list. This is because you changed the contact list outside of pidgin (probably using live messenger on windows). Just ignore and it'll use the changes you made instead of it's own older list.

---

### Post by fox1 on 2007-07-26
Thanks I found it...

---

### Post by fox1 on 2007-07-29
...........

---

### Post by tony_gustafsson on 2007-10-23
I had the same problem - but like 100 dialogs... it made me wanna switch IM client. But I finally solved it. I did not use any other MSN clients so that was not the problem for me. I gave Everyone full access to ~/.purble/blist.xml, viola! :)

Hope it works for you too

---

