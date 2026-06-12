---
title: "tar.tar file?"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by ph7klw on 2006-06-16
How do I install a file ending tar.tar?

---

### Post by simone.brunozzi on 2006-06-16
[QUOTE=ph7klw]How do I install a file ending tar.tar?[/QUOTE]

Hi there!
You must always take a look at the file extension (letters after the last dot . ),
in this case it is a .tar (abbreviation for Tape ARchive).

Here some useful instructions:

# To unpack tar files, use the following commands:
    * to unpack an uncompressed tar file:
        tar -xf file_to_unpack.tar

    * to decompress and unpack one step at a time:
          gunzip packed_files.tar.gz
          tar -xf packed_files.tar

    * to decompress and unpack all at once:
          gunzip -c packed_files.tar.gz | tar -xf -

# To list the contents of a tar file, use the following command:
        tar -tvf file_to_list.tar


Cheers,

---

### Post by Arndt on 2006-06-16
[QUOTE=simone.brunozzi]Hi there!
You must always take a look at the file extension (letters after the last dot . ),
in this case it is a .tar (abbreviation for Tape ARchive).
[/QUOTE]

Some additional information: in many cases, the command 'file' will be able to tell you what kind of file it is. In the case of a tar file, it will say:

```
% file myfile.tar
myfile.tar: tar archive
%
```

---

