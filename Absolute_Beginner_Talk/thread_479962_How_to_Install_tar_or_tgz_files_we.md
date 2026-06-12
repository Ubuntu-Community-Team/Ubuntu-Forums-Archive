---
title: "How to Install tar or tgz files w/e"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by tridge on 2007-06-20
I am complete nub to linux and I don't know how to install software. helpz.

---

### Post by Clay_Banger on 2007-06-20
[How to install anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

[EDIT] This is what you want on that page. [Link.]("http://monkeyblog.org/ubuntu/installing/#source")[/EDIT]

---

### Post by wormser on 2007-06-20
Most software you can install from the repositories.  You can use apt-get in the command line and Synaptic Package Manager gui application.

This site has a good [guide]("http://www.psychocats.net/ubuntu/installingsoftware").

---

### Post by MonkeyNet on 2007-06-20
TAR and TGZ are compressed files similar to a Zip File.

Generally, I will download a TGZ file to my /temp directory, then extract using;
```
tar -xvf filename-1.01.tar.gz
```

This will extract the contents to /temp/filename-1.01/

Then you go into that directory and follow the instructions for compiling/installing.

Hope this helps

---

### Post by tridge on 2007-06-20
wow, thank you all for the quick links and awesome advice.. i like your method monkey!

---

### Post by MonkeyNet on 2007-06-20
Good luck.

I found that this was the best way to learn :)

You will find that you won't even think twice about extracting files soon enough.

Also would recommend reading the MAN pages for tar. There are a lot of different options that you can use

---

### Post by tridge on 2007-06-20
Yeh, crazy thing is that when i was 13 I ran slackware like a champ... now I'm 23 and I have lost all that information.

---

