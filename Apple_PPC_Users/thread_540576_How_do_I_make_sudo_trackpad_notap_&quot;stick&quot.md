---
title: "How do I make sudo trackpad notap &quot;stick?&quot;"
date: 2007-09-01
forum: Apple PPC Users
---

### Post by ticopelp on 2007-09-01
I'm on a 15" Powerbook and every time I come back from suspend, the damn trackpad mouse-tap turns back on. It drive me nuts, because my thumb is always hitting the trackpad and making it "click" when I don't want it to. So I type sudo trackpad notap in the terminal, but that only sticks until I close the lid... then it's back. 

Any suggestions very welcome.

---

### Post by kidders on 2007-09-02
Hi there,

I don't have Linux on my laptop, but as far as I'm aware, you can create scripts, and have them executed on resume from sleep by placing them in /etc/acpi/resume.d/. I strongly recommend you do some investigating before taking my word on that ... just to make sure I'm right, and that there aren't any nasty gotchas to be aware of ... but with any luck, I've at least pointed you in the right direction.

---

### Post by ticopelp on 2007-09-02
Well, I've done a lot of investigating, tried a bunch of different things... no luck so far. I can make it work, but the trackpad tap comes right after suspend no matter what I do. I've tried: 

syndaemon -d

Editing my xorg.conf

I even think I've tried that script that's in resume.d, but it didn't seem to take. 

Thanks for the reply though.

---

