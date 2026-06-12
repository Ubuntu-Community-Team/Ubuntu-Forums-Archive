---
title: "mozilla https"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by ozPATT on 2007-04-11
Hi all, 

I *still* have a problem with my mozilla not being able to access secure sites. I have searched these forums and done everything they suggest, but still no joy. I have completely removed, reinstalled, and whatever else is possible to do to mozilla, and still no better. 

I see other people have managed to fix theirs, so would love to find out how to go about it, as I am using Opera for secure sites, and Mozilla for everything else

Thanks

Patrick

---

### Post by LaurelLynn on 2007-04-11
Dear ozPATT,

Are there any error messages at all.  It is real hard to figure out what is wrong when the only symptom is that it doesn´t work.

Since firefox is an application.  The mozilla website will have forums where I would also ask the question. You might find more people with the same problem there. If helps to look at a problem from several perspectives.

---

### Post by ozPATT on 2007-04-11
Hi Laura, thanks for the fast response. This is the error I get:
> Unexpected response from server

Firefox doesn't know how to communicate with the server.

    *   Check to make sure your system has the Personal Security Manager
          installed.

    *   This might be due to a non-standard configuration on the server.

I will see what I can gather on mozilla forums too, however as it was working until an update a couple of months ago, I am assuming it is something to do with ubuntu.

Thanks

Patrick

---

### Post by LaurelLynn on 2007-04-11
Depends on if only Ubuntu was updated, or firefox was also updated at the same time.

Sounds like it might be a missing firefox update, try:

$ apt-get update firefox

I would bet someone on a Mozilla forum will have seen the error message before (if not on Ubuntu then on another os).  Even if you find a post that refers to another os, it should give you more clues where to look next.

---

### Post by josephus on 2007-04-11
i've read on another forum that this is related to nss.  

try reinstalling libnss3 and then uninstalling and reinstalling firefox

---

### Post by ozPATT on 2007-04-11
hi there, I just did as you suggested, installed libnss3, then uninstalled firefox and then installed it... but still not working :( also looked on mozillazine forums and still no help from there yet, but continuing the search...

---

### Post by josephus on 2007-04-11
I don't think I can be of much help hrere but in case you haven't seen these pages:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/90376](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/90376)
[http://www.fedoraforum.org/forum/showthread.php?t=120631](http://www.fedoraforum.org/forum/showthread.php?t=120631)
[http://ubuntuforums.org/showthread.php?t=374232](http://ubuntuforums.org/showthread.php?t=374232)

If you've already reinstalled everything, I would try removing your mozilla profiles directory, since that can survive an uninstall.

---

### Post by ozPATT on 2007-04-11
where is the profiles directory? thanks for the links, looking now

---

### Post by josephus on 2007-04-11
all the mozilla preferences are in /home/<user>/.mozilla  try:

```
mv ~/.mozilla ~/.mozilla-old
```

---

### Post by ozPATT on 2007-05-17
hi all, 4 weeks on I still have no secure sites.. almost at the point of learning to live with it :-s 

this morning, i thought id have another go. i used 

```
sudo rm -r ~/.mozilla
```

to get rid of it - but that didnt seem to because when I clicked on the mozilla link it still worked... 

then i downloaded the zip from mozilla, unzipped it and then put the unzipped folder contents into a newly created .mozilla folder. 

and still no joy...

any help? am i the only one who hasnt been able to fix this yet? i ave tried removing in snaptic, and that didnt work either...

thanks

pATRICK

---

