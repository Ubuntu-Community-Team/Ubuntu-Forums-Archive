---
title: "Warning from top of forum tarbomb"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by wawadave on 2008-04-16
Tarbomb: Someone asks you to extract a tar archive into an existing directory. This tar archive can be crafted to explode into a million files, or inject files into the system by guessing filenames. You should make the habit of decompressing tars inside a cleanly made directory

Ok here is my newby question.

What exactly is a cleanly made directory?Would a new folder count?
How would i create one?
Would i need a new one with each new tar file?

---

### Post by nvteighen on 2008-04-16
> **wawadave said:**
> Tarbomb: Someone asks you to extract a tar archive into an existing directory. This tar archive can be crafted to explode into a million files, or inject files into the system by guessing filenames. You should make the habit of decompressing tars inside a cleanly made directory

Ok here is my newby question.

What exactly is a cleanly made directory?Would a new folder count?
How would i create one?
Would i need a new one with each new tar file?
A "cleanly made directory" would be a new directory made specially for extracting that tarfile... After you've seen the tarfile isn't harmful, you're free to move its contents wherever you want to.

The idea is that a tarbomb needs to know where it is being extracted in order to be really effective and harm your system.

(And never extract a tar using sudo!!)

---

### Post by wawadave on 2008-04-16
ok then how does one create a new directory?

---

### Post by neurostu on 2008-04-16
right click in Nautilus and click "Create folder"

open a terminal and type:
```

mkdir <dir name>

```

---

### Post by lswest on 2008-04-16
```
mkdir [path to new folder]
``` is all you need.  if creating the folder anywhere but your home folder, it will require a sudo prefacing that command.

---

### Post by stchman on 2008-04-16
> **wawadave said:**
> Tarbomb: Someone asks you to extract a tar archive into an existing directory. This tar archive can be crafted to explode into a million files, or inject files into the system by guessing filenames. You should make the habit of decompressing tars inside a cleanly made directory

Ok here is my newby question.

What exactly is a cleanly made directory?Would a new folder count?
How would i create one?
Would i need a new one with each new tar file?

You can use Archive Manager to open the tar archive without actually decompressing the archive.  For the CLI folks you can use the -t argument.

```
sudo tar -tvzf <.tar.gz archive>
```

The -t just lists the archive while -x decompresses.

---

### Post by wawadave on 2008-04-16
ok thank you!!!

---

