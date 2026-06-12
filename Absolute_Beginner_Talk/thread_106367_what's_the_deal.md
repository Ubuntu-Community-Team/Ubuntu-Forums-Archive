---
title: "what's the deal?"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by cbeshears on 2005-12-20
What's the deal?  I'm logged in as root and type in the command "makewhatis" at the command prompt.  It's telling me the command is not found.  Can anybody tell me what I'm doing wrong?  Also when I type in "man makewhatis" I'm told that it's not found.  Thanks. :confused:

---

### Post by bscbrit on 2005-12-20
Well the deal is there is no such command as 'makewhatis' and therefore there is no man page to explain how to use it.
But that is not very helpful to you.  What are you trying to do?

---

### Post by cbeshears on 2005-12-20
Well, I'm trying to create a database that reads all the manual pages and inserts the name of the command with a short description.  

Below is a link that describes the makewhatis command I was referring to:
[http://www.die.net/doc/linux/man/man8/makewhatis.8.html](http://www.die.net/doc/linux/man/man8/makewhatis.8.html)

---

### Post by Swab on 2005-12-20
I think the database already exists... as you can use the whatis command..

---

### Post by bscbrit on 2005-12-20
The command you are using is possibly not used in Ubuntu.  Have a look at

man whatis

to see if that is what you are trying to achieve, and in particular the following from that man page:

"  Index databases are used during the search.  To produce  an  old  style
       text  whatis  database from the relative index database, issue the com&#8208;
       mand:

       whatis -M manpath -w &#8217;*&#8217; | sort > manpath/whatis  "


EDIT:  Swab is correct, it is not required, but if you want to do it, I think this command is what you were looking for.

---

