---
title: "Help!! Ubuntu just killed itself  ; ;"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by skrimpy on 2007-06-15
I tried to install a deb package which had a dependency I didn't have.  After attempting to get the dependency my terminal told me it conflicted with an installed package and it wasn't going to get it.

After this I noticed my update icon come up.  I clicked it and was given an error message.  It told me to run sudo apt-get install -f

I ran that and I watched with a hugely sinking feeling as Ubuntu removed everything from my system.  

What happened and how the heck do I fix it?

---

### Post by swoll1980 on 2007-06-15
Where did you get the pacage from? What was the Package?

---

### Post by kevinlyfellow on 2007-06-15
Can you still log in (even if via terminal)?

If so, pick a package the it removed (like nautilus or anything) and try to reinstall it.

```
sudo apt-get install nautilus
```

Hopefully it will try to resolve the dependencies by removing that package you installed.

---

### Post by brooksbp on 2007-06-15
What package are you trying to install? Post the errors / dependencies please.

PS - try using Synaptics under System -> Administration. It would probably be easier to visualize the package management.

---

### Post by skrimpy on 2007-06-15
the package I tried to install was wavbreaker;

I am trying to reinstall nautilus right now - I can't open a new terminal window but it is allowing me to use the one I had open

---

### Post by skrimpy on 2007-06-15
nautilus is back but I don't know what to do from here :(

---

### Post by vasiliymeshko on 2007-06-15
Try
```
sudo apt-get install ubuntu-desktop
```

---

### Post by skrimpy on 2007-06-15
I can't even see everything it took off anymore because the terminal window wont scroll back up that far >.<

this has got to be the most incredibly horrible thing...

what the heck does sudo apt-get install -f do?  Everything I'm looking at online says it fixes broken dependencies...not removes everything from your system!

---

### Post by ts51 on 2007-06-15
Very odd.... 

Sounds to me like you'd be better off just re-installing.

---

### Post by bobplano on 2007-06-15
i did this once and i ended up reinstalling because for me synaptic and aptitude broke after this. where did you get this .deb file from? my guess is it might've been a debian .deb file and that would probably mess up your system if you tried to install. but that's just my guess

---

### Post by skrimpy on 2007-06-15
> **bobplano said:**
> i did this once and i ended up reinstalling because for me synaptic and aptitude broke after this. where did you get this .deb file from? my guess is it might've been a debian .deb file and that would probably mess up your system if you tried to install. but that's just my guess

it was a .deb from debian.  should I not use those >.<?

the install desktop seems to be working somewhat.  I may end up reinstalling, it's just a royal pain to recustomize everything.  At least I keep good backups :(

---

### Post by skrimpy on 2007-06-15
reinstalling the ubuntu desktop seems to be restoring most things.  my localhost apache2 server is also functioning, though I don't know if anything else (php or mysql) is...

Synaptic is back so it looks like I can probably restore what didn't get picked up in the generic ubuntu-desktop and nautilus installs.

Thank you guys so much for the quick help.  I have to go out of town to a wedding in the morning and I would have been one unhappy gal if I'd left a totally broken system.

---

### Post by ryanVickers on 2007-06-15
Weird.  I'm surprized Ubuntu would do that.  It reminds me of this product - you didn't ahpen to be trying to install *this*, were you? :p

My suggestion would be just to save everything and re-install.  Even if it did get working again, I wouldn't trust it by that point...

---

### Post by skrimpy on 2007-06-18
> **ryanVickers said:**
> Weird.  I'm surprized Ubuntu would do that.  It reminds me of this product - you didn't ahpen to be trying to install *this*, were you? :p

My suggestion would be just to save everything and re-install.  Even if it did get working again, I wouldn't trust it by that point...

lol that comic made me laugh.  It seems to be stable right now - I've just come back into town and I'm going to watch it for a couple of days and decide if I want to reinstall or not.

---

### Post by Anicka on 2007-06-18
I don't know if it has anything to do with it, but after I updated to Feisty, if I did "sudo aptitude install", Aptitude wanted to remove more or less all my packages. I did "sudo aptitude reinstall packages_on_the_list" for all ~150. After that no problems, but it was not very fun doing it... There probably was some unresolved dependency, but I don't know what. There was a similar post about it [http://ubuntuforums.org/showthread.php?p=2531309](http://ubuntuforums.org/showthread.php?p=2531309), but as I said, might be totally unrelated.

---

