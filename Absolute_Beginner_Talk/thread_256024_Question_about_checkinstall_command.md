---
title: "Question about checkinstall command"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by podunk on 2006-09-12
I read the how to here:
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

and I started installing all my programs with the "checkinstall" command instead of "make install" so I can remove stuff later on.

As I've been doing this I have built up a lot of directories full of source code and make files in my Desktop directory.

Can I save the uninstall file and delete all these diirectories or will this mess things up?

---

### Post by skymt on 2006-09-12
Once you've installed something with checkinstall, *it's installed*. You can delete the source directories and everything in them, including the .deb that checkinstall generated, with no ill effects. To uninstall a CI package, just use your preferred package manager (aptitude or synaptic).

---

### Post by podunk on 2006-09-12
Way cool - thank you very much! :-)

---

