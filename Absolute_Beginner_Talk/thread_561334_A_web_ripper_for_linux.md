---
title: "A web ripper for linux?"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by l337a on 2007-09-27
I am in need of a website crawler that will crawl php, html, etc in search of various media like jpeg, png, avi, mpeg, etc.

Is there such a thing? And where can I get my hands on it? :D

---

### Post by rich.bradshaw on 2007-09-27
wget is what you need. Already installed. No GUI, but very very powerful.

---

### Post by l337a on 2007-09-27
I'm still quite a novice when it comes to the *nix tools. Could you guide me in doing such a function?

---

### Post by rich.bradshaw on 2007-09-27
For instance:

get -A.jpg -r -l1 --no-parent [http://www.website.com/](http://www.website.com/) 

will get all images from that [www.website.com](www.website.com)

---

### Post by l337a on 2007-09-27
So let me get this clear...
'
sudo wget -r -p -U Mozilla [http://mysite](http://mysite)



So where does the search for jpeg, png, and other media types fit into this? (Sorry, Im a bit thick today XD)

Also, I notice that it only saves index files, no images. Is there any fix to this? oO

---

### Post by Steveway on 2007-09-27
Don't use sudo!
And for all the information you need:
man wget

---

### Post by l337a on 2007-09-27
Sorry, I use sudo out of habit. Now when I use wget it creates a folder and locks it. I cant even remove this under sudo. Any ideas?

---

### Post by hyper_ch on 2007-09-27
howabout httrack? I used that on windoze and it's also in the repos.

---

### Post by gnudoc on 2007-09-27
> **l337a said:**
> Sorry, I use sudo out of habit. Now when I use wget it creates a folder and locks it. I cant even remove this under sudo. Any ideas?

do you mean it creates a new inaccessible folder every time you use sudo, or just when you used sudo?
Could you please, in a terminal, go to the folder in which this inaccessible folder lives and type ```
ls -al
```

or even better, type ```
ls -l stupidfolder
``` but swap stupidfolder for the name of the annoying folder.

paste the results here, and we may have a better idea of whats happened.

i suspect wget created a folder owned by root because you used it with sudo. we'll soon find out.

thanks,
gnudoc

---

