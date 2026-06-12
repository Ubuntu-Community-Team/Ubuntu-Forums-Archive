---
title: "Debian: File Copy from Terminal not working"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Madman6510 on 2008-03-10
This one is really bugging me. I'm trying to move some files I burned onto a CD into the www directory, so I can host them.

I do
```
mount cdrom
cd /media/cdrom
sudo cp website /var/www/
```
and it gives me
```
cp: omitting directory 'website'
```
So I'm thinking "Cool, it just put all my files it the /var/www directory, I can live with that". So I look, nope, no files. So I try
```

sudo mkdir /var/www/website
sudo cp /media/website/* /var/www/website
```

Now, it moved all the files from the main directory of my website, but left out the other directories that contain all of the files that make my site... work.

This one is starting to mess with my brain. Can someone tell me how to make cp copy the files AND directories?

---

### Post by talsemgeest on 2008-03-10
Try cp -r . That will make the cp command work recursively, going into all of the subdirectories as well.

That should do it. :)

---

### Post by Madman6510 on 2008-03-10
Ok, that worked. Thanks dude.

---

### Post by talsemgeest on 2008-03-10
No problem. Glad to help.

Don't forget to mark this thread as solved

---

