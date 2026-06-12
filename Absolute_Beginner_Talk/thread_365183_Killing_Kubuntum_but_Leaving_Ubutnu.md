---
title: "Killing Kubuntum but Leaving Ubutnu"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2007-02-19
Hi, I have both Ubuntu & Kubuntu installed, they where installed at seperate times. I now wish to kill my Kubuntu, but leaving Ubuntu, and all its fikes & settings intact.

I have been told that sudo apt-get purge kubuntu-* Would work. However i get the error that Purge is an invalid operation. Any help?

---

### Post by ShareBuntu on 2007-02-19
> **Captain Kirk76 said:**
> Hi, I have both Ubuntu & Kubuntu installed, they where installed at seperate times. I now wish to kill my Kubuntu, but leaving Ubuntu, and all its fikes & settings intact.

I have been told that sudo apt-get purge kubuntu-* Would work. However i get the error that Purge is an invalid operation. Any help?

Correct me if I'm wrong, but I believe the command is --purge. Also, I might be mistaken, but I think aptitude should be used over apt-get since it picks up on dependencies.

Check out [http://www.psychocats.net/ubuntu/aptitude]("http://www.psychocats.net/ubuntu/aptitude"). I found that article really helpful.

---

### Post by jvc26 on 2007-02-19
Did you install just the kubuntu-desktop desktop package? (I.e. to run KDE on the Ubuntu base) or did you have 2 separate total installs - i.e. one Kubuntu and one Ubuntu? If its the first I'd look [here]("http://www.psychocats.net/ubuntu/kde") and to restore it back if this was the method used, look [here]("http://www.psychocats.net/ubuntu/puregnome") Finally if it was a separate install you just need to remove the partitions with the Kubuntu install on it, and resize your Ubuntu partition to take up the space.
Hope that goes some way to helping I'd take a read and see if those apply to you,
Il

---

### Post by Captain Kirk76 on 2007-02-19
My original installation was Ubuntu, on a downloaded disc (Since then i have got some officials)
About a month later i installed Kubuntu through apt-get commands on Terminal.

I just want to remove the Kubuntu part, keeping Ubuntu.

---

### Post by jvc26 on 2007-02-19
Can you not therefore remove the Kubuntu bit via the instructions on the link I gave you above? [here]("http://www.psychocats.net/ubuntu/puregnome")
Il

---

### Post by Captain Kirk76 on 2007-02-19
Oh, my apologies, i didn't see that :)

---

### Post by jvc26 on 2007-02-19
No problems, hope that works out for you :)
Il

---

