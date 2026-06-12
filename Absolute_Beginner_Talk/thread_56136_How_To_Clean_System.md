---
title: "How To Clean System"
date: 2005-08-11
forum: Absolute Beginner Talk
---

### Post by Kapre on 2005-08-11
Hiyall!

Could someone please help me on how to clean up the ubuntu system. I did some install but cannot make it work (is there a way to know if the prgs are still in my system). Also how do I check for broken dependencies (to avoid getting the message when I try to install a new program)?

Thank you very much.

K

---

### Post by KingBahamut on 2005-08-11
[QUOTE=Kapre]Hiyall!

Could someone please help me on how to clean up the ubuntu system. I did some install but cannot make it work (is there a way to know if the prgs are still in my system). Also how do I check for broken dependencies (to avoid getting the message when I try to install a new program)?

Thank you very much.

K[/QUOTE]
 Can you give the output you recieve in console when you experienced the error from before? 

You can always run apt-get clean and apt-get autoclean to clear out your apt cache.

---

### Post by Buran on 2005-08-11
It is recomended ?
In the Win era it was allmost a daly drill, now? when I was converted to Linux , is it neccesery ?

---

### Post by Kapre on 2005-08-11
[QUOTE=Buran]It is recomended ?
In the Win era it was allmost a daly drill, now? when I was converted to Linux , is it neccesery ?[/QUOTE]

KingBahamut - Thanks for the info. I can't post the error(s) anymore because I stopped installing (dont want to do it again). 

Buran - I dont know if this is necessary but I just would like to be sure that hard disk space is alway OK. Thanks.

K  O:)

---

### Post by az on 2005-08-11
If you cannot install anything anymore because of errors, tell apt to cerrect them (one way or the other) by running:

sudo apt-get -f install

---

