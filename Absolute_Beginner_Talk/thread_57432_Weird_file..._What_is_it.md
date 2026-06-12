---
title: "Weird file... What is it?"
date: 2005-08-16
forum: Absolute Beginner Talk
---

### Post by pmjdebruijn on 2005-08-16
Hi,

I've got this wierd file, I'd like to know what it is? A broken symlink maybe?

[IMG]http://www.xs4all.nl/~bruijn9/images/weird-file.png[/IMG]

When I scan it with my own program built upon libclamav... it crashes... So I'd like to know how to avoid that... But first I need to know what to avoid...

Regards,
Pascal de Bruijn

---

### Post by jasmuz on 2005-08-16
I think its a FIFO

---

### Post by heimo on 2005-08-16
[QUOTE=jasmuz]I think its a FIFO[/QUOTE]

Seconded. "named pipe"
[http://www2.linuxjournal.com/article/2156]("http://www2.linuxjournal.com/article/2156")

There may be a switch / flag for clamav to avoid scanning these special files.

 > 
When I scan it with my own program built upon libclamav... it crashes... So I'd like to know how to avoid that... But first I need to know what to avoid... 

Oh. Re-read that. I think I'm not in position to give you advice. :) You'll figure it out.

---

### Post by pmjdebruijn on 2005-08-16
Oh, that's what the 'p' means... lol...  :-? 

Thank you...

Regards,
Pascal de Bruijn

---

