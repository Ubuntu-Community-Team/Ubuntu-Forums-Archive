---
title: "Managed to break it already..."
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Delameko on 2006-08-29
Hi,

I'm new to Linux.  I installed Opera through Firefox and selected to open it with the relevant program rather than save it to disk.

Now I get an error saying Opera isn't installed properly and it can't find the install package.

I tried to reinstall it using deb file, but it says Opera is already installed.

It doesn't appear in the Add/Remove Programs list.

So how do I go about fixing this?

Thanks for your time.

---

### Post by Anonii on 2006-08-29
> **Delameko said:**
> Hi,

I'm new to Linux.  I installed Opera through Firefox and selected to open it with the relevant program rather than save it to disk.

Now I get an error saying Opera isn't installed properly and it can't find the install package.

I tried to reinstall it using deb file, but it says Opera is already installed.

It doesn't appear in the Add/Remove Programs list.

So how do I go about fixing this?

Thanks for your time.

Open the terminal.
Type _sudo apt-get remove --purge opera _
Then _sudo apt-get install opera_

Report any errors back here, since there will probably be an error in the first step.

---

### Post by Marsolin on 2006-08-29
If the purge and install suggestion doesn't work, it may be because the /usr/bin/opera file doesn't get installed correctly. I had that problem on a couple different computers. I had to copy it from the deb file using Ark and manually put it in /usr/bin. For some reason the install was only creating a symlink.

---

### Post by Delameko on 2006-08-29
Thanks for the help guys.

@Anonii
The first line brings up the error "E: The package opera needs to be reinstalled, but I can't find an archive for it.'


@Marsolin
I have no opera file in the /usr/bin/ directory, so I'm thinking this might be the problem.  I couldn't get the deb file to open so I downloaded the tar.gz version.  In the archive there is a bin folder with a file called opera in it.  Is this the file I need to copy over?

---

### Post by Delameko on 2006-08-30
Anyone?

I don't want to break it further ;)

---

### Post by lazyd2 on 2006-08-30
Have you tried with aptitude instead of apt-get?

---

### Post by John.Michael.Kane on 2006-08-30
This should remove problematic packages.
```
sudo aptitude -f **name of package here**
```

Run:
```
sudo gedit /etc/apt/sources.list
```

Add this line to your source.list:
```
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

You should be able to run:
```
sudo aptitude install **name of package here**
```

---

