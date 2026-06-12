---
title: "running a .py file"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by 7SEALS on 2007-11-12
Hey guys. I use to run ubuntu awhile ago, and got back into windows for gaming. I am now back to ubuntu to further my programming education, but I have seem to hit a brick wall. I have python files on my desktop (.py) and, its been so long that I have forgotten how to run them in the terminal :(

I think I am suposed to type python, and then what do I do to run the files? These files are all on the desktop btw, so thanks for the help!

---

### Post by Arwen on 2007-11-12
Does [this ]("http://www.onecore.net/how-topython-programming-under-ubuntu.htm")help?

---

### Post by 7SEALS on 2007-11-12
thanks a ton! I didn't think anyone would be up this late, and figured I would have to wait till tomorrow. Thanks a lot!

---

### Post by erginemr on 2007-11-12
I am also enthusiastic about Python, its power and versatility, and started learning it a few days ago. So far, I have very good fellings towards Python, it seems to be a good investment in terms of time and effort. So, good luck to both of us in our quest!

Regarding your question, and on the following simple Hello World program:

hello.py:
#!/usr/bin/python
print 'Hello World!'

You can do it in two ways:

1. Either you can run it using the Python interpreter:
python hello.py

2. Or the line "#!/usr/bin/python" causes it to act like a shell program. You just need to give user executable permission to it:
chmod u+x hello.py

Then, you can run python programs directly by:
./hello.py

---

### Post by steve.horsley on 2007-11-12
> **7SEALS said:**
> thanks a ton! I didn't think anyone would be up this late, and figured I would have to wait till tomorrow. Thanks a lot!

Hah! That depends where you are. I'm eating my lunch right now.

---

### Post by Arwen on 2007-11-12
U welcome! There are so many users in this forum and from all over the world so you can post anytime and expect an answer.Good luck with python!

---

