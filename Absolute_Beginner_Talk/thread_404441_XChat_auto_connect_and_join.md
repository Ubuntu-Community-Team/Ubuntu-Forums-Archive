---
title: "XChat auto connect and join?"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2007-04-08
I have XChat and it is getting annoying connecting and joining the same channels every time.

How do I make it so it auto connects to Quaknet server and joins my favourite channels, namely #ubuntu !!

I don't know a great deal about IRC in general.

---

### Post by Bachstelze on 2007-04-08
Ctrl+S will give you the networks list. Choose the network you want to change settings for and click Edit. Here's a screenshot to help you if needed.

[http://itsuki.fkraiem.org/stuff/xchat.png](http://itsuki.fkraiem.org/stuff/xchat.png)

---

### Post by tommy1987 on 2007-04-08
Thanks, although simple, you wouldn't believe how long I have been looking for that!

---

### Post by xdefconx on 2008-01-03
hehehe i also looking for this solutions. Thanxs HymnToLife! u help us a lot :)

---

### Post by Bachstelze on 2008-04-02
Link updated.

---

### Post by Walc on 2008-04-02
thx m8
but can any1 explain 2 me how can i set it up when lets say:

-im tryin to axx 3 channels on a server
-1 of the channels needs to be axx by : msg chanserv invite 'chan.name'
-plus i have 2 use nickserv identify 'pass' command too since im willing to use vhost

if any1 would show me how and where to type that chanserv invite command and where in that case should go msg nickserv identify?

thx

---

### Post by Bachstelze on 2008-04-02
Put your commands in the 'Connect commands' box and they will be executed when you connect.

---

### Post by Walc on 2008-04-02
so like...: msg nickserv identify 'pass', msg chanserv invite 'chan' ?

sadly...its not working

---

### Post by bitumen on 2008-07-01
Google search found the answer

[http://mailman.linuxchix.org/pipermail/techtalk/2007-June/022039.html](http://mailman.linuxchix.org/pipermail/techtalk/2007-June/022039.html)


> In xchat, you click on Xchat ->
Network List, then select the server you want.  Then click on "Edit"
and put the following in the "Connect command" text box:

LOAD -e ~/.xchat2/linuxchix_commands

Then put the commands in that file (you can put the file wherever you
want, I just put mine in .xchat2/ because it makes sense).  The
permission on my file are standard 644, so no execute bit needed.  The
commands are:

/msg nickserv identify <password>
/msg chanserv invite #invite-only
/msg chanserv info #invite-only
/join #invite-only

You should probably take out anything duplicated from the other
fields, like "Nickserv password".  I just moved all of that stuff,
including the channels to join, into my commands file - mine looks
like this:

/msg nickserv identify <password>
/msg chanserv invite #admin
/msg chanserv info #admin
/join #admin
/join #linuxchix
/join #grrls-only
/join #volunteers
/join #devchix


---

