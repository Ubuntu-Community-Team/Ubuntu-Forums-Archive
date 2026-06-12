---
title: "Quick, Easy, Question"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by nonpareilpearl on 2007-11-19
I am trying to figure out how to use an FTP type of service from command line/terminal, and I just can't seem to get the syntax right. Hypothetically I want to:
ftp /home/me/movethisfile.ext -> /school space/movethisfile.ext

What is the appropriate syntax for this (either ftp or sftp)?

---

### Post by Sarteck on 2007-11-19
I don't know about the CLI syntax...  But could I ask why you don't use a GUI interface instead?

---

### Post by stomponthis on 2007-11-19
You can install 'gFTP' with:
```
sudo apt-get install gftp
```
you can use it from the command line, eg:
```
 gftp [options] [[proto://][ user : [pass] @] site [: port ][/ directory]]

```

---

