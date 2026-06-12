---
title: "what is easiest way to search for folders?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by willfriedwald on 2008-02-11
is there a graphical / desktop program that allows you to easily search for folders?

am trying catfish - but there doesn't seem to be a way to tell it to just look for folders ...  I mean, it's finding all the folders I want, but also listing all the files in them - which is way more info than I want or need.  

How can I tell it to just list the folder names & not the contents thereof?

w

---

### Post by asmoore82 on 2008-02-11
the `find` command line search can be told only to show directories with the option ``-type d''

so the full syntax for a basic, case-insensitive search for folders would be:
**find *<where_to_look>* -type d -iname "**<what_to_look_for>**"**

examples:
```
**asmoore@pickles:~$** find /home -type d -iname "*fox*"
/home/asmoore/.mozilla/firefox
**asmoore@pickles:~$** find /home -type d -iname "*local*"
/home/asmoore/Games/wine-cstrike/drive_c/windows/profiles/asmoore/Local Settings
/home/asmoore/.local
/home/asmoore/.evolution/tasks/local
/home/asmoore/.evolution/mail/local
/home/asmoore/.evolution/calendar/local
/home/asmoore/.evolution/memos/local
**asmoore@pickles:~$** find /home -type d -iname "*music*"
/home/asmoore/Music
```

---

### Post by willfriedwald on 2008-02-11
thanks - am trying to do this using a graphical desktop program - find & copy...


"file search" does it - but it doesn't allow me to group the results by type - I click on icon, but it doesn't change, and sort the results by icon - which would be perfect...

w

---

