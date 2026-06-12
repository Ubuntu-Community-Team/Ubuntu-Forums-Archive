---
title: "deleting files"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by santiagorf on 2008-03-23
Hi,
Im using xubuntu, and i'am trying to delete the file:

/etc/firefox/profile/mimeTypes.rdf, 

Since I cannot, I tried using the command:

chmod -w mimeTypes.rdf

to get more permissions, but I cannot since I get the following message:

chmod: changing permissions of `mimeTypes.rdf': Operation not permitted

Any idea how can I erase this file?

Thanks in advance
()Santiagorf

---

### Post by wolfen69 on 2008-03-23
```
sudo thunar
```
then navigate to file and delete.

---

### Post by Joeb454 on 2008-03-23
If you're using the command line just use ```
sudo rm /etc/firefox/profile/mimeTypes.rdf
```

You'll need *sudo* because it's outside your /home directory, still, you should always be careful when using sudo :)

---

### Post by santiagorf on 2008-03-23
thanks!!

---

