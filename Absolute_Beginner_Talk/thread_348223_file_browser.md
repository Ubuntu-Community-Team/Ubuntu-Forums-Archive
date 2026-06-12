---
title: "file browser"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by bailey_jatt on 2007-01-28
ok .. a very lame question.. you can guess my knowledge of linux frm this as being absolutly zero...

i have newly installed ubuntu edgy eft. have a bunch of partitions. basically a / partition - where i figure ubuntu system files are. a /home where my documents should be and another partition which is fat32 where i want to store my other data. 

Pray tell me how do i browse from partition to another windows explorer style. At present all i can i do is goto menu>places>home ... i cant seem to find a way to go to the other drive...:confused:

---

### Post by highneko on 2007-01-28
Konqueror is the best file browser in my opinion. To install it type "sudo apt-get install konqueror", or install kde.

---

### Post by taurus on 2007-01-28
With Ubuntu, use nautilus.

---

### Post by bailey_jatt on 2007-01-28
hmm .. i would want to stick with gnome because somehow it's more appealing to my taste.. so guess i would have to go for konqueror. So you mean there no default gui type browser which can display the partitions and all?

---

### Post by jvc26 on 2007-01-28
You can use nautilus with gnome. Its already there: you could create a launcher via right clicking the top menu bar add to panel custom application launcher, under the command put nautilus. Then you can just click to open it.

Another method: Places -> Computer and you can navigate around the filesystem tree from that (which opens a nautilus window)

Il

---

### Post by Pobega on 2007-01-28
If you want to use Konquerer you could install it, but I don't know how many Qt dependencies you'd have to install alongside it. You're probably best sticking with a GTK file browser in Gnome, and you already have Nautilus installed anyway.

---

### Post by bailey_jatt on 2007-01-28
sorry to bugger you .. but the thing is when i hit computer under places it opens up this window which says two options.. Filesystem or dvdrom. i look arnd under filesystem but cant find a way to reach my fat32 partition. so is there a way to do that or i would have to mount it before i can take a look at it?

---

### Post by Sqwishy on 2007-01-28
when the thing opens goto tools>>prefrences or something maybe edit>>prefrences or something. then the first checkbox under the 2 radio things i can't remember what it says. but i think if you press that, when you goto places home it will open it in an 'explorer' type ting

---

### Post by taurus on 2007-01-28
> **bailey_jatt said:**
> sorry to bugger you .. but the thing is when i hit computer under places it opens up this window which says two options.. Filesystem or dvdrom. i look arnd under filesystem but cant find a way to reach my fat32 partition. so is there a way to do that or i would have to mount it before i can take a look at it?

Yeah, you have to mount it first before you can use or access it.  Have you mounted your fat32 partition?

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by kerry_s on 2007-01-28
> **highneko said:**
> Konqueror is the best file browser in my opinion. To install it type "sudo apt-get install konqueror", or install kde.

Please, don't do that! It's not nice to suggest applications that will pull a ton of dependencies from another desktop environment. What if some newby did that on dial up because you suggested what you prefer. We never suggest something like that unless asked. Please try and answer the questions corresponding to the environment there using, if you can't help, don't. New people have a blind faith in the people to help, something like your suggestion could bring more problems than the original problem. Thankyou.

---

### Post by bapoumba on 2007-01-28
> **bailey_jatt said:**
> 
Pray tell me how do i browse from partition to another windows explorer style. At present all i can i do is goto menu>places>home ... i cant seem to find a way to go to the other drive...:confused:
The windows partitions, if you did not do anything special, are mounted in /media file. So just check in there.
In any case, **cat /etc/fstab** will show ou were your partitions are mounted. Post it here, if you're not sure.

---

### Post by bailey_jatt on 2007-01-28
Thanks mates. I had to mount the darn fat32 partition. I was under some kind of impression that fat32 was automatically mounted and it was the ntfs partitions that one had to mount. :) got the thing right where i want it to be. 

Thank you all

---

### Post by taurus on 2007-01-28
Just add an entry in /etc/fstab and that thing will be mounted where you want it to be every time you boot Ubuntu.

---

### Post by bailey_jatt on 2007-01-28
yepp did just that. found a lot of helpful information in ubuntuguide.org :D  ... danke

---

