---
title: "[SOLVED] what's that command...."
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2007-11-28
I used this command ages ago which displayed my system specifications in an html file but i cant remeber what it was! can anyone help

---

### Post by Dr Small on 2007-11-28
I didn't know one existed, but if it did, I should like to know too :D

---

### Post by kamitsukai on 2007-11-28
yer it was on the forums i think but i just can remember...lol

---

### Post by jryprt on 2007-11-28
Try sudo lshw

---

### Post by Majorix on 2007-11-28
You mean this one?
```
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
```
? I haven't seen it anywhere, just found out when I was reading man lshw.

---

### Post by Dr Small on 2007-11-28
That is very useful. It can also be dumped into a systemhw.txt file too ;):
```
sudo lshw > systemhw.txt
```

---

### Post by Dr Small on 2007-11-28
Majorix, your's is even better :D

---

### Post by master_kernel on 2007-11-28
Thanks for posting this thread; I didn't know about this cool command!

I uploaded mine for fun: [http://kcheck.sourceforge.net/other/hardware_info.html](http://kcheck.sourceforge.net/other/hardware_info.html)

---

### Post by Dr Small on 2007-11-28
Here is mine :D
[http://php.8ez.com/drsmall/hardware_info.html](http://php.8ez.com/drsmall/hardware_info.html)

---

### Post by master_kernel on 2007-11-28
I think I'll start a thread so people can post theirs... :) I'll post the link back.

---

### Post by Majorix on 2007-11-28
Lol I won't post my hardware info as you would all laugh at the specs.

BTW, I edited out the command twice because of a typo, sorry for the inconvenience. Now it should be working, I tested it on my compi

---

### Post by wesley_of_course on 2007-11-28
> **Majorix said:**
> You mean this one?
```
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
```
? I haven't seen it anywhere, just found out when I was reading man lshw.

  Even'in all .   After trying this out I receive the following response ;
bash: /home/wesley/firefox: No such file or directory
 
   And the other one ;wesley@Ratdog:~$ sudo lshw | system hw.txt
                                                          bash: system: command not found


   What up ?

---

### Post by skyjacker on 2007-11-28
> **Dr Small said:**
> That is very useful. It can also be dumped into a systemhw.txt file too ;):
```
sudo lshw | systemhw.txt
``` I tried this command and here is the return;

skyjacker@skyjacker-desktop:~$ sudo lshw | systemhw.txt
[sudo] password for skyjacker:bash: systemhw.txt: command not found


[1]+  Stopped                 sudo lshw | systemhw.txt
skyjacker@skyjacker-desktop:~$ indy&River
[2] 8231
bash: indy: command not found
bash: River: command not found
[2]-  Exit 127                indy

What did I do wrong?. I copied from the post and pasted into the terminal

---

### Post by Dr Small on 2007-11-28
Pardon me. I made a mistake too :p
It's supposed to be:
```
 sudo lshw > systemhw.txt
```

---

### Post by Majorix on 2007-11-28
> **wesley_of_course said:**
> Even'in all .   After trying this out I receive the following response ;
bash: /home/wesley/firefox: No such file or directory
 
   And the other one ;wesley@Ratdog:~$ sudo lshw | system hw.txt
                                                          bash: system: command not found


   What up ?

You tried the code just before my edit. Lol. What a timing of yours. Try again using the edited code (the one standing there now) and you should be fine.

---

### Post by Dr Small on 2007-11-28
I went back and edited my command too. I had it pipping instead of dumping..... My mistake.

---

### Post by skyjacker on 2007-11-28
> **Majorix said:**
> You tried the code just before my edit. Lol. What a timing of yours. Try again using the edited code (the one standing there now) and you should be fine.

COOL! Tried it and it works great. Thanks

---

### Post by master_kernel on 2007-11-28
Here's the new thread: [http://ubuntuforums.org/showthread.php?t=626057](http://ubuntuforums.org/showthread.php?t=626057)

---

### Post by teryowen on 2007-11-28
Wow very nice, thank you.

---

### Post by wesley_of_course on 2007-11-28
Good Grief !, thorough too ! ,  Thanks again !
   One of these days I'll be able to catch these things ! (typo's )     :lolflag:

---

### Post by qpieus on 2007-11-28
> **Majorix said:**
> 
```
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
```

too cool, thanks.

---

### Post by kamitsukai on 2007-11-30
Yer thnx everyone its a really useful command!!

---

