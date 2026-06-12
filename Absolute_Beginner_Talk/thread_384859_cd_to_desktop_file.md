---
title: "cd to desktop file?"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by Toadmund on 2007-03-15
I am understanding this 'cd' command, or 'change directory' thing more and more, 
-good tutorial:
[http://www.linux.org/lessons/beginner/l4/lesson4b.html]("http://www.linux.org/lessons/beginner/l4/lesson4b.html")

but when download instructions instruct me to navigate to a file (usually they say to put it on the desktop) 
cd /desktop doesn't work, 

cd /home/my_name/desktop/filename 
doesn't work.

How do I navigate to a file on my desktop? Am I pointing in the wrong direction, is there a folder called desktop that is not on the desktop.

I am sure there are those here who can answer this, this seems to me a major roadblock to downloading files and getting on with it, I'm also in the process of turning 3 other people on to Ubuntu and I've got to know this stuff.

Thanks!

---

### Post by taurus on 2007-03-15
Try

```
cd ~/Desktop
```
Linux/Unix is case sensitive so ~/desktop is not the same as ~/Desktop.

---

### Post by aktiwers on 2007-03-15
Did you remember to type Desktop with a capital "D". Remember the Terminal is cAsE SenSeTive...

---

### Post by Toadmund on 2007-03-15
I am understanding this 'cd' command, or 'change directory' thing more and more, 
-good tutorial:
[http://www.linux.org/lessons/beginner/l4/lesson4b.html]("http://www.linux.org/lessons/beginner/l4/lesson4b.html")

but when download instructions instruct me to navigate to a file (usually they say to put it on the desktop) 
cd /desktop doesn't work, 

cd /home/my_name/desktop/filename 
doesn't work.

How do I navigate to a file on my desktop? Am I pointing in the wrong direction, is there a folder called desktop that is not on the desktop?

I am sure there are those here who can answer this, this seems to me a major roadblock to downloading files and getting on with it, I'm also in the process of turning 3 other people on to Ubuntu and I've got to know this stuff.

Thanks!

---

### Post by taurus on 2007-03-15
> **Toadmund said:**
> I am understanding this 'cd' command, or 'change directory' thing more and more, 
-good tutorial:
[http://www.linux.org/lessons/beginner/l4/lesson4b.html]("http://www.linux.org/lessons/beginner/l4/lesson4b.html")

but when download instructions instruct me to navigate to a file (usually they say to put it on the desktop) 
cd /desktop doesn't work, 

cd /home/my_name/desktop/filename 
doesn't work.

How do I navigate to a file on my desktop? Am I pointing in the wrong direction, is there a folder called desktop that is not on the desktop?

I am sure there are those here who can answer this, this seems to me a major roadblock to downloading files and getting on with it, I'm also in the process of turning 3 other people on to Ubuntu and I've got to know this stuff.

Thanks!

:confused:  :confused:  :confused:

---

### Post by Toadmund on 2007-03-15
Thanks!
I did not know about the case sensitivity.

So, It would be like ~/Desktop/home/my_name/filename
to point to a particular file on the 'D'esktop.

Right?

(Previous post was due to a bad connection, it would not delete)

PS, personal note, do NOT hit 'Post Reply' when editing posts, hit 'save'

---

### Post by taurus on 2007-03-15
Actually, ~ stands for your $HOME directory so if your login name is john, then ~ is the same as /home/john.

Therefore, if you want to change to your Desktop directory in your $HOME, then you would do

```
cd Desktop 
-or-
cd ~/Desktop
(since ~/Desktop is the same as /home/john/Desktop)
```

---

### Post by MrKlean on 2007-03-15
Yeah,.... what Taurus said ; )

---

