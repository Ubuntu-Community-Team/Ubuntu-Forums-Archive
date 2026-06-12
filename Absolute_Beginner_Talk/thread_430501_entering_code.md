---
title: "entering code"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by jackman1275 on 2007-05-02
hi i need to make my sound card work by entering snd-cs4236 BUT WHERE ? the artical in the how to is very ambiguous if you dont know what youre doing . like i can mod games and stuff but at least i know where to start wiith ubuntu im a bit lost can anyone point me in the right direction; like do i enter it at startup or something

---

### Post by overdrank on 2007-05-02
> **jackman1275 said:**
> hi i need to make my sound card work by entering snd-cs4236 BUT WHERE ? the artical in the how to is very ambiguous if you dont know what youre doing . like i can mod games and stuff but at least i know where to start wiith ubuntu im a bit lost can anyone point me in the right direction; like do i enter it at startup or something

Hi and welcome could you post the link to what you are trying to install?:-k

---

### Post by etherior on 2007-05-02
which how to do you refer to?

---

### Post by jackman1275 on 2007-05-02
its at the bottom of the page  'sound' im trying to make 5.04 work on a dell optiplex gx1 dont ask why,but the crystall sound wont work thje help file said that ubuntu wont detect this automaticlyhttps://help.ubuntu.com/community/UserDocumentation

---

### Post by jackman1275 on 2007-05-02
its at the bottom of the page 'sound' im trying to make 5.04 work on a dell optiplex gx1 dont ask why,but the crystall sound wont work thje help file said that  it  wont detect this automaticly  
...[https://help.ubuntu.com/community/HowToSetupSoundCards]("https://help.ubuntu.com/community/HowToSetupSoundCards")

---

### Post by etherior on 2007-05-02
You have to put it in /etc/modules.(it's clearly written in the doc..)
You can simply open a terminal and write:
sudo -s
echo "snd-cs4236" >> /etc/modules

---

### Post by jackman1275 on 2007-05-02
a root terminal or just a terminal?

---

### Post by taurus on 2007-05-02
A terminal, Applications -> Accessories -> Terminal, should do just fine.

---

### Post by overdrank on 2007-05-02
> **taurus said:**
> A terminal, Applications -> Accessories -> Terminal, should do just fine.

The master Taurus    :cool:

---

