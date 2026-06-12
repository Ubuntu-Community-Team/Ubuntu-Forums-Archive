---
title: "AIM error"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by Ronaldbain99 on 2007-12-12
I get this error every time I try to run AIM and EVERYONE has told me to use Pidgin...for the love of God, please do not answer my question with "use pidgin or kopete"

How do I fix this?
```
aim: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

---

### Post by t0p on 2007-12-12
> **Ronaldbain99 said:**
> I get this error every time I try to run AIM and EVERYONE has told me to use Pidgin...for the love of God, please do not answer my question with "use pidgin or kopete"

How do I fix this?
```
aim: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

Use pidgin or kopete.

Hehe!!

---

### Post by awthomp on 2007-12-12
t0p is right.  Seriously, use Pidgin.  No ads, it's simple, annnnnnnd you can use neat plugins like "Idle maker."  :-D

---

### Post by spydon on 2007-12-12
Try to do
```
sudo apt-get install libgtk1.2*
```

---

### Post by jken146 on 2007-12-12
Hey, come on guys, don't say that!  It's up to the OP to use pidgin or kopete or AIM (quite why he'd choose AIM is baffling to me too), but please try to offer constructive advice that answers the question.

Perhaps you haven't got libgtk-1.2 installed correctly.  Try ```
sudo aptitude install libgtk-1.2*
``` and post any errors you get.

edit:  beat me to it, spydon!

---

### Post by Ronaldbain99 on 2007-12-12
Says that it doesn't exist...```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "libgtk-1.2*"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done  
```

---

### Post by Ronaldbain99 on 2007-12-12
I doesn't understand!?

---

### Post by awthomp on 2007-12-12
Sorry, I was kidding with the Pidgin statement :)

Maybe if you try to install the .deb file you'll have more success?  Did you try to compile it from source?

[AIM on Linux]("http://www.aim.com/get_aim/linux/latest_linux.adp#deb")

---

### Post by spydon on 2007-12-12
> **Ronaldbain99 said:**
> Says that it doesn't exist...```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "libgtk-1.2*"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done  
```

Then you probably need to activate more repos System>Administration>Sources or something like that(My ubuntu is in swedish).

---

### Post by Ronaldbain99 on 2007-12-12
I did install the .deb file already and it still is giving me the same error...man this is confusing...

---

### Post by Sef on 2007-12-12
1) That package (libgtk-1.2.so.0) is not in Ubuntu's repositories at all.

2) Options

a) Look for it via google or ask.com.   (If you do find it, hope that it does not have other dependencies that you need.  If it does, you will need to find them too. This can lead to dependency hell: always need a new dependency for what you need to install.)  

b) Use pidgin (since you are on Ubuntu.)

c) If you need voice features, use Kopete.  

d) If you have another idea, please use it.

---

