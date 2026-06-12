---
title: "Could not download all repository indexes"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by AnyKeyButShift on 2007-10-21
Hi, I have just upgraded from 7.04 to 7.10 with no major problems except when I use the Software Sources. I get the following error message;

"Could not download all repository indexes"

And the following in the message window;

"http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release: Unable to find expected entry  main/debian-installer/binary-i386/Packages in Meta-index file (malformed Release file?)"

I have tried changing servers.

I read a thread from May this year instructing to hash out the back ports repository lines. Are the back ports required? Or is it safe to just do this?

Cheers

---

### Post by pdlethbridge on 2007-10-21
It just may be that the servers are overloaded with work with the new release. Maybe wait a couple of days

---

### Post by Hospadar on 2007-10-21
you don't really need to hash anything out in the sources file, you can just uncheck it in Administration->Software Sources.  Probably just busy servers, but try unchecking some stuff.  you don't really need backports to my knowledge.

---

### Post by jniebles on 2007-10-22
Has your problem been solved? I've been getting a similar message after the upgrade. I initially thought it might be because of server overload, but several days have passed and the message still comes up.

this is the exact complain i get:
```

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release: Unable to find expected entry  main/debian-installer/binary-amd64/Packages in Meta-index file (malformed Release file?)


```

---

### Post by Maestro23 on 2007-10-22
> **jniebles said:**
> Has your problem been solved? I've been getting a similar message after the upgrade. I initially thought it might be because of server overload, but several days have passed and the message still comes up.

this is the exact complain i get:
```

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release: Unable to find expected entry  main/debian-installer/binary-amd64/Packages in Meta-index file (malformed Release file?)


```

That is commented out in my default sources.list for 7.10

Try editing you sources.list and comment those entries out.

---

### Post by jniebles on 2007-10-23
is this the file to change?

/etc/apt/sources.list

I commented the lines with the string 'gutsy-backports' in it. Still getting the same error. Am I changing the wrong file? is there any other file where this configuration is stored?

thanks

---

