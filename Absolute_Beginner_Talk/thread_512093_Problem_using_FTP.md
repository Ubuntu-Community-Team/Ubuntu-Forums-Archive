---
title: "Problem using FTP"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by peterhf on 2007-07-28
Hello All,

Running Ubuntu 6.10.

Have created an ftp-only account on a Mac 10.4.9 which is on my lan. The ftp server is running.

All the other machines on the lan, another Mac, the Ubuntu machine and a Windows XP machine, can ping the Mac machine.

However, when I try "ftp <username>@<the IP of the Mac>" from the Ubuntu machine, this message appears: "ftp <username>@<the IP of the Mac> Unknown Host". "ftp <username>@<the IP of the Mac>" works from the other Mac but it does not work from the Windows XP machine!!

Any Thoughts? Thanks for any help offered.

Peter -

---

### Post by nitro_n2o on 2007-07-28
is port 21 open in your mac machine? check the machine and the router or firewall on the Mac machine

---

### Post by Warren Watts on 2007-07-28
try it without the user@

ftp <the _IP_of_the_MAC>

it should then prompt you to enter the username and password

---

### Post by peterhf on 2007-07-28
Thanks Warren, works perfectly!

I have little experience with FTP from the system prompt and did not know of any reference to an alternative syntax for the program

Five stars to you for the response.

Peter -

---

### Post by Warren Watts on 2007-07-28
We have all been there, struggling to solve the simplest of issues.
I am far from an expert, but I really enjoy helping out when I see an issue I think I can help with.
That's what makes the Ubuntu Community such a wonderful thing; it really is a Community.

BTW, if you you are looking for an easier to use FTP tool, you might consider installing an FTP client like gFTP (its in the repositories)...

Long live the Ubuntu Community!

Warren

---

