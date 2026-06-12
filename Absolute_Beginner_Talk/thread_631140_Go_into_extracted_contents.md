---
title: "Go into extracted contents???"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by writeman on 2007-12-04
Dear Gurus:

I have searched and I still don't understand--you download something like a dictionary to your home and get instructions like: 

all you have to do is use sudo and type in your own password. download the tarball, right click on it, select 'extract here'. then fire up the terminal and go into the extracted contents, then type:
sudo cp * /usr/share/stardict/dic

Please, please...how do I get to the extracted contents via the terminal--I tried cd to home and the file name and it isn't recognized--I constantly (at least in the 24 hours I have been a gnu linux user) keep coming up against this--

Is there an installation tutorial...please help

Dazed, confused and ubunted around,

Thanks in advance.

writeman

---

### Post by hyper_ch on 2007-12-04
Where do you do extract to?
Where on the system are you when you run your "sudo cp..." command?

---

### Post by writeman on 2007-12-04
I download everything to home the default--not sure I know how to specify anywhere else, then  I fire up the terminal from a button on the start bar.

---

### Post by Joeb454 on 2007-12-04
type ```
cd /home/user/thefolderyouextractedto
```

where user = your username

and the last part is the name of the folder the extracted contents are

---

