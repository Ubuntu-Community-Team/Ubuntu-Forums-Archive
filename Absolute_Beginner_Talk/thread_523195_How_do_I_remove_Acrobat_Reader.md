---
title: "How do I remove Acrobat Reader?"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-08-11
Hey guys,

I installed Adobe Acrobat 7.0.9 with the tar.gz file from Adobe's main site. I know there's a install script, but I looked everywhere for an uninstall script...Can someone tell me how to remove Acrobat?

---

### Post by ron999 on 2007-08-11
Hi
You could just use Synaptic.
Or type into the monitor **sudo apt-get remove acroread**

---

### Post by isaacj87 on 2007-08-11
Thanks for the response...

It isn't possible for me to do it that way. I installed it with the downloaded tar.gz file from adobe's website.
Not the repos (doh!! Which is why I want to remove the other one, so I can install the repo version). Any other suggestions?

---

### Post by ron999 on 2007-08-11
Well, I don't have so much experience, but on my setup there's an Adobe folder in /usr/lib
Perhaps you just need to delete this.
There's also an acroread link in /usr/bin
that would probably need to be deleted too.
Or maybe someone else will come up with a better suggestion.

---

### Post by isaacj87 on 2007-08-11
Yeah, that's what I was considering doing...pretty hackish...:) but thanks for the suggestion.

---

