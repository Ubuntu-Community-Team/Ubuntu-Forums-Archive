---
title: "Wget Problems - Downloading a Directory"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2007-04-07
I want to download everything in this directory "http://www.shmoocon.org/2007/videos/", but when i do:

```
wget -r http://www.shmoocon.org/2007/videos/
```

It downloads [http://www.shmoocon.org/*](http://www.shmoocon.org/*) (basically the entire site.

How can i download i single directory (with its entire content) with Wget? and if this is not possible, Is there another tool that can?

thanks 
James

---

### Post by dreadlord_chris on 2007-04-07
> **Jamesbowden said:**
> I want to download everything in this directory "http://www.shmoocon.org/2007/videos/", but when i do:

```
wget -r http://www.shmoocon.org/2007/videos/
```

It downloads [http://www.shmoocon.org/*](http://www.shmoocon.org/*) (basically the entire site.

How can i download i single directory (with its entire content) with Wget? and if this is not possible, Is there another tool that can?

thanks 
James

Hi....
You need to pass wget a list of files to accept or reject - or else it defaults to accepting all files. You do this with the **-A** or **-R** switches. To only grab certain files use **-A <FILE EXTENSION>**. To specify more then one file type, use multiple -A flags. In your case, for that site, the line would be:

```

wget -r -A mp4 http://www.shmoocon.org/2007/videos/

```

---

### Post by dwblas on 2007-04-07
You might also want to use the -l (level) parameter to limit the number of levels.  Web pages can go on and on and on.  See "man wget"

---

### Post by Jamesbowden on 2007-04-07
Thanks for the help.

so if i do "wget -r -l1" it will just download that directory?

---

