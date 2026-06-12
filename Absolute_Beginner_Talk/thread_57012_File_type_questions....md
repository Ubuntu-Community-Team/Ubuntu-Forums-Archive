---
title: "File type questions..."
date: 2005-08-14
forum: Absolute Beginner Talk
---

### Post by YourSurrogateGod on 2005-08-14
How do you open a .ace file and what's a .ogm file? I'm working under the assumption that a .ogm file is a video file, how would you play that?

---

### Post by nad on 2005-08-14
[http://filext.com/](http://filext.com/)

You _open_ a file by using an application that is written to manipulate the data in the specific format of the file type.

Having said that, unix/linux systems use file extensions only as a last resort and as a matter of fact are unnecessary. These systems are usually configured to first check for a file type using _magic_. Magic is really nothing more than a peek at the data contained in the file to try to match it to a known file type. This is one reason that these systems are inherently more secure than operating systems from other vendors. You can not spoof a file type.

---

### Post by cwaldbieser on 2005-08-14
Try using the "file" command on the file to find out more information about it.

---

### Post by YourSurrogateGod on 2005-08-15
[QUOTE=nad][http://filext.com/](http://filext.com/)

You _open_ a file by using an application that is written to manipulate the data in the specific format of the file type.

Having said that, unix/linux systems use file extensions only as a last resort and as a matter of fact are unnecessary. These systems are usually configured to first check for a file type using _magic_. Magic is really nothing more than a peek at the data contained in the file to try to match it to a known file type. This is one reason that these systems are inherently more secure than operating systems from other vendors. You can not spoof a file type.[/QUOTE]
That's great, but how do you open it? What commands do I use?

---

### Post by YourSurrogateGod on 2005-08-15
[QUOTE=cwaldbieser]Try using the "file" command on the file to find out more information about it.[/QUOTE]
Thanks.

---

### Post by Kyral on 2005-08-15
ogm is indeed a video file try installing both the w32codecs package and the ogmtools package

Ace is an old file compression format (like bzip2, gzip, rar, zip, etc) that is really a pain in the ass to use. Best way I've found so far is to install WinRAR with WINE and let it uncompress ACE

---

### Post by nad on 2005-08-15
What is the problem here?

You clearly have the capability to do your own search for information.

Are your questions merely rhetorical or do you really expect someone to make the effort for you?

---

### Post by YourSurrogateGod on 2005-08-15
[QUOTE=nad]What is the problem here?

You clearly have the capability to do your own search for information.

Are your questions merely rhetorical or do you really expect someone to make the effort for you?[/QUOTE]
Someone else to do the effort for me? No, I don't. The reason why I asked is because I was utterly stumped as to what those types of files were. I did my fair share of research by looking into synap in order to figure out whether there was an app that could open/read those files and since I didn't find any, I asked.

---

### Post by Kyral on 2005-08-15
[QUOTE=nad]What is the problem here?

You clearly have the capability to do your own search for information.

Are your questions merely rhetorical or do you really expect someone to make the effort for you?[/QUOTE]

Jeez... stifle the RTFM crap. Its called the Absolute Beginners Forum for a reason. We are a welcoming warm Ubuntu community. We live by the expression "There is no such thing as a stupid question"

---

### Post by YourSurrogateGod on 2005-08-15
Just for the record, I still consider myself somewhat of a n00b when it comes to Linux. If one thinks that I'm more advanced than a n00b simply because of my post count, well that's because I've been hanging around the Community Chat for some time (hey, what can I say, I like the anime fans here.)

---

### Post by Kyral on 2005-08-15
And How!!! :d

---

### Post by az on 2005-08-15
Let's just all be excellent.

---

