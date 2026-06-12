---
title: "Tried upgrading, oops. .Something's gone wrong.."
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Penguin Fever on 2007-06-14
Yes, I really am such a stupid girl >.> Today I tried to upgrade my ubuntu to 7.04 from 6.10, but I think it may have crashed during the upgrade (I think), my PC has now restarted and instead of any text on the system, there is instead boxes like those that represent invalid characters) I hope that makes sense.. I could take a screencap if you would like to see what I mean..

I'm useless with these things, so I would really appreciate the help, thank you so much in advance to anyone who can help.:)

Edit: [here's a screenshot of the problem (I just used a random screen for an example)]("http://img391.imageshack.us/img391/4886/screenshotproblemue9.png")

---

### Post by REDISISTone.nl on 2007-06-14
Hard to say, maybe the screen cap isn&#8217;t such a bad idea !!

/edit

are you able to get in the command line (ctr+alt+f1 no grapical enviroment)

---

### Post by Penguin Fever on 2007-06-14
[screenshot]("http://img391.imageshack.us/img391/4886/screenshotproblemue9.png")

And I just tried, but I don't think it's working.. :/

---

### Post by REDISISTone.nl on 2007-06-14
Do you got a camera to take a picture of the screen ?? 
**/edit** sorry...didn&#8217;t see you edited your first post...


Or you could try giving some more information about what is going on...(what hardware do you use (most important is your video card) what do you see and what not...)

**I don&#8217;t think I&#8217;m able to help you...someone else got some ideas ??**

---

### Post by REDISISTone.nl on 2007-06-14
What happens when you boot from cd (feisty) (live session)

---

### Post by Penguin Fever on 2007-06-14
My graphics card is an ATI Radeon 9200SE if that's any help, but i don't think it's anything to do with that, as it worked perfectly fine until I tried to upgrade, so I think it's really that something went wrong during that.. :(

And thanks anyway for your help :) I hope someone can help though >.<

---

### Post by REDISISTone.nl on 2007-06-14
If you got your files backupped you can try installing feisty again...but first wait if there is someone else can help you...I think it's fixeble

---

### Post by Penguin Fever on 2007-06-14
> **REDISISTone.nl said:**
> What happens when you boot from cd (feisty) (live session)

I haven't actually tried that.. I'll try and find my CD. :)

---

### Post by Penguin Fever on 2007-06-14
I can't seem to find my CD, but I'll keep looking.. Does anyone else have any other ideas though? :$

---

### Post by Penguin Fever on 2007-06-14
I think it may be an error with the language pack? Is there a way I could download that from somewhere?

---

### Post by Seisen on 2007-06-14
Try booting into recovery mode and type this in the terminal

```
 apt-get -f install
 dpkg --configure -a
 
```

You don't need to add sudo in front of the commands because the recovery mode runs as root.

---

