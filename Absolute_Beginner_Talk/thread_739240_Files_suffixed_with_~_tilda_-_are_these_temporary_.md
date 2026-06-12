---
title: "Files suffixed with ~ tilda - are these temporary files?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by cheesey_toastie on 2008-03-29
This might be a dumb question but should I be seeing duplicates of my files (e.g. html files) with tilda's?  

I'm finding that they appear in the file browser and in third party software - this means I'm uploading a lot of unnecessary files to my website etc by ftp?

Is this a setting that I have made somewhere!?!

Thank
CT

---

### Post by Joeb454 on 2008-03-29
I think they are :)

You can delete them, it won't do any harm, I always delete them too :)

---

### Post by cheesey_toastie on 2008-03-29
I've turned them off in nautilus(sp?) 
*View - Show Hidden Files *

 though I still see then in Filezilla etc...

---

### Post by cheesey_toastie on 2008-03-29
> **Joeb454 said:**
> I think they are :)

You can delete them, it won't do any harm, I always delete them too :)

It's annoying having them sprayed over my webspace though.... 

i know what you're thinking  OCD......   maybe a little :D

---

### Post by Joeb454 on 2008-03-29
Delete them on your webspace as well then. From a terminal, you can use *cd* to get to the directory you want, and then run ```
rm *.*~
```

I have some in /var/www/ which obviously requires sudo, but then I always double check that I've got it right :)

---

### Post by louieb on 2008-03-29
Certain programs like bluefish and gedit suffix backup files with the ~.
Check the program preferences  of whatever your editing your site with and turn off the backup option if you want.

---

### Post by cheesey_toastie on 2008-03-30
> **louieb said:**
> Certain programs like bluefish and gedit suffix backup files with the ~.
Check the program preferences  of whatever your editing your site with and turn off the backup option if you want.

Thanks - I wondered if the fact I was editing files on an XP mount was also meanign these weren't deleted.  

For the record it was Gedit - I've only just discovered Blue Fish, really impressed with the Regular Expression search accross multiple files and the Advanced Open.  Saved me hours :guitar:

---

### Post by cheesey_toastie on 2008-03-30
I had lots of sub directories : this helped

Find all backup files and delete them!
    find . -name "*~" -exec rm {} \;

From
[http://soledadpenades.com/articles/ubuntu/ubuntu-linux-cheatsheet/](http://soledadpenades.com/articles/ubuntu/ubuntu-linux-cheatsheet/)

---

