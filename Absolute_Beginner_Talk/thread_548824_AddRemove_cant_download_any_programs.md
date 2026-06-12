---
title: "Add/Remove cant download any programs"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by asleekaizoku on 2007-09-11
When I try to get any applications listed on the Add/Remove Applications (for example 7-Zip), it just comes to this part and doesn't download:

[IMG]http://img357.imageshack.us/img357/1397/screenshotir4.jpg[/IMG]


I'm not downloading anything or using up my bandwidth so, I don't really know what is happening.
Anyone knows how to solve this problem??

---

### Post by Clay_Banger on 2007-09-12
are you able to browse the internet with firefox?

also, copy and paste this command into the terminal and then copy and paste the output here. all this command does is install 7zip.
```
sudo aptitude install p7zip-full
```

---

### Post by asleekaizoku on 2007-09-12
> **Clay_Banger said:**
> are you able to browse the internet with firefox?

also, copy and paste this command into the terminal and then copy and paste the output here. all this command does is install 7zip.
```
sudo aptitude install p7zip-full
```

Yes I am able to browse the internet using firefox.
I tried that code and all I got was this:

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
Writing extended state information... Done
0% [Connecting to ca.archive.ubuntu.com (206.167.141.10)]   (It stops right here)

---

### Post by asleekaizoku on 2007-09-12
Hooray I solved the problem!

I went to System > Administration > Synaptic Package Manager
then i did:
Settings Repositories and changed "Download from: " to Main Server

---

### Post by hyper_ch on 2007-09-12
seems like the ca (Candian) server did have some issues...

---

### Post by lisati on 2007-09-12
> **hyper_ch said:**
> seems like the ca (Candian) server did have some issues...

I've noticed that sometimes the (geographically) closest server isn't always the best one to use....

---

