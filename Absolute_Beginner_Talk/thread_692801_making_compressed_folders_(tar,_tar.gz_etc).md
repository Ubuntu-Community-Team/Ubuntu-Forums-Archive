---
title: "making compressed folders (tar, tar.gz etc)"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2008-02-10
hello, ive been trying to make some zipped folders and ive run into a little trouble.

basically ive been trying to create an archive of a folder thats a theme for the awn window navigator, but im having some problems with it.
the format for the themes is .tgz, every theme file ends like that .tgz now how do i create an archive with that extension ? ive tried various times and i can get tar.gz but not .tar
i did try just changing the folder name but it didnt work (worth a shot i thought)
i did have ago at using gzip, but couldnt figure out how to create an archive using the command line.
any help will be appreciated.
cheers

---

### Post by LaRoza on 2008-02-10
tar is an archive format, it doesn't compress anything.

```

man tar
man gzip

```

.tgz or .tar.gz is a tar file that has been gzipped.

Right click the file/directory, and select "Create Archive'.

Create a .tar.gz then change it to .tgz.

(Or you can tar it, then gzip it)

---

### Post by techno-mole on 2008-02-10
i meant an archive.
ive tried to create an archive like you said

"  Right click the file/directory, and select "Create Archive'.

Create a .tar.gz then change it to .tgz.  "

but there isnt an option to change it to tgz, i can create a tar.gz and then change the extension to .tgz, but its not the right format, because its still tar.gz

ive tried using gzip, but i have no idea how to use it, even after messing with it and reading the manual.
cheers

---

### Post by The Cog on 2008-02-10
I think .tar.gz and .tgz are two interchangeable extensions for the same file format - a gzipped tar file. So renaming the file should not be an issue.

---

### Post by TheBoat on 2008-02-10
I am also pretty sure that .tar.gz and .tgz are equivalent and interchangeable.

---

