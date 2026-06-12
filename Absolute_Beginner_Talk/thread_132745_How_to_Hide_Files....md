---
title: "How to Hide Files..."
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by xXx 0wn3d xXx on 2006-02-18
How do I hide files ? I want them to be able to still be used, just not able to be seen. How can I do this ? Thanks

---

### Post by nalmeth on 2006-02-18
put them into a folder, call it hidden, for example.
put a decimal in front of the folder like so:
.hidden
to see the folder in nautilus, choose VIEW --> SHOW HIDDEN FILES

---

### Post by majikstreet on 2006-02-18
this is what I did to get files hidden from my deskop, I'm sure it will work in any folder (if you're using nautilus or a gnome application to view the folder) 
here's what I did:

```

cd ~/Desktop
touch .hidden
ls -x > .hidden
gedit .hidden

```
In gedit remove the files you want to see
That will make all files other than the ones you removed be hidden from view.. But, since firefox downloads to ~/Desktop, I changed firefox to download to ~/ffoxdownloads

Also: any files added after you did the ls will be shown! you will need to do this to make it again:
```

cd ~/Desktop
rm .hidden
touch .hidden
ls -x > .hidden
gedit .hidden

```
and in gedit remove the files you want to see then save and close,
then you are done :)

---

### Post by 5-HT on 2006-02-18
If you simply place a period before the file, it will be hidden from a ls.
You can still see it though if you use the ls -a switch though.

so to hide foo, simply rename it to .foo like so: ```
 mv foo .foo 
```

Was that what you were looking for?

*EDIT: Wow, little slow off the gun with both nalmeth and majikstreet already responding.

---

