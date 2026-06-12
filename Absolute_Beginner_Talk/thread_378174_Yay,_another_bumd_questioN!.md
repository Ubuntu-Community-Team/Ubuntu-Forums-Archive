---
title: "Yay, another bumd questioN!"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Burst404 on 2007-03-06
Alright... I'm setting up a dedicated web server using ubuntu 6.06 server for x86 intel. It's installed... and I'm following a quide... So far so good... Except...

I type
vi /etc/network/interfaces

and make the necessary changes... But... How do I save said changes?

Yes, I know, stupid.

---

### Post by 23meg on 2007-03-06
You'll need to use sudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You may also prefer a simpler editor such as nano to do simple edits to configuration files. 

```
sudo nano /etc/network/interfaces
```

Make the required changes, and hit Ctrl + O to save, and then Ctrl + X to exit.

---

### Post by maniacmusician on 2007-03-06
why are you using vi to edit a simple text file?

I have to say, that for a newbie, vi is a bit overkill. You should wait until you get more comfortable before taking that step. I've been using linux for a year, and I still haven't touched vi/vim...so I can't really answer your question.

In the future, I recommend using the nano text editor: sudo nano /etc/network/interfaces

With nano, you press Ctrl + X to exit and save the file.

---

### Post by Burst404 on 2007-03-06
I thank both of you.

---

### Post by sloggerkhan on 2007-03-07
My first programming class in college, never had done any real coding before, we all had to SSH into some sort of *nix server to write code in vi from the command line. I think if you have a guide it's not so intimidating.

---

