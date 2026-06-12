---
title: "Open Office Base Doesn't work."
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by wvernon on 2006-09-26
I can't get Base to work.  It hangs up on the first screen.

Any ideas, I don't think it's the nvidia drivers as I have the same problem on a non-invidia box.

Regards,

Wayne

---

### Post by Architeuthis on 2006-09-26
Maybe we can help you more if you give us some more information :p 
For example: Put "openoffice" in a terminal and post the output, assuming that openoffice opens base and you were not talking about openoffice database.
Then you will see error logs in the terminal and that should help you further.

---

### Post by wvernon on 2006-09-26
Architeuthis,

Thanks for responding.

I did what you suggested. There was no error log in the terminal.

If I try to open the database application in OOo, it asks me if I want to create a database, and when it goes on to the page that allows you to start creating tables etc. it just hangs.

I have to then force it to quit, and when I try it again, it asks me if I want to recover the file, if I do, it hangs again.

It doesn't make any difference if I ask it to register the database with open office or not.

I've seen threads elsewhere saying it might be linked to nvidia drivers, but I have the problem on a non-nvidia box as well.

I'm stumped.

Wayne

---

### Post by wvernon on 2006-09-26
Whoops, when I force quit it this time, I saw an error message in the terminal I left open earlier:

 *** glibc detected *** free(): invalid pointer: 0xb6197678 ***/usr/lib/openoffice/program/soffice: line 233: 18891 Killed                  "$sd_prog/$sd_binary" "$@"

---

### Post by The Mekon on 2006-09-26
Hi Wayne

I have had problems with Base but found the best advice on the following [link]("http://sheepdogguides.com/fdb/fdb1main.htm")

My main problem was that I had not installed the correct Java environment which Base requires to work properly.

I have a couple of simple databases working to track my financial transactions and contacts' list.

Best of luck and be prepared to bone up on SQL.

Brian

---

### Post by Drevan on 2006-09-26
yea it's a java problem. go to tools > options > java and select sun 1.5.0_6 as the version you are using

---

### Post by wvernon on 2006-09-27
Brian & Drevan,

Problem sorted. Many thanks for your help.

You don't get this sort of assistance on windows.

:D 

Wayne

---

### Post by ColinG on 2006-11-03
I'm running Edgy and base won't work. I'm on Sun Java 1.5_08

Any ideas?
Thanks
Colin

---

