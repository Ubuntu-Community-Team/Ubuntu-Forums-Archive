---
title: "WinRar or WinZip similar app"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by palemmo on 2007-11-29
Hi, i'm looking for a simple program that is similar to winzip/rar/ace of winzoz.
A need a simple gui that permits to: 
[LIST=1]
[*]compress files
[*]uncompress files
[*]compress/uncompress to multiple archives
[*]compress with a password
[/LIST]

For example for now I have a linux application that is divided into 11 packets, I don't know how to unpack it...and put all in one....
file.r00
file.r01
file.r02
.......
file.r11
that should be only one file, file.rar
I have to open it via microsoft because I don't know how to uncompress....
Thanks
(PS I'm relatively new... Excuse me if I wronged section)

---

### Post by alienexplorers on 2007-11-29
You could try p7zip. It can be found in the repositories.

---

### Post by regomodo on 2007-11-29
make sure you install unrar. From then on any (at least ark and squeeze) will be open rar's spread over many files.

I just open any of them and tell it to extract the contained file, when it's done it has combined the lot.

---

### Post by komputes on 2007-12-07
This is extremely simple in linux with the rar and unrar utilities. But since gzip and tar are the preferred "open source" compression utilities, making rar with passwords are not supported by default. For that you will need to get rar (the oposite is unrar, but I never needed that because archive manager works well). In the terminal window:
```

sudo apt-get install rar
```

Once it is installed you could make a password protected encrypted archive using the following comand (note that you should be in the same directory as file you want to compress is, this is accomplished by using the "cd /directory/"). Once you are in the correct directory, do the following to compress 2 files "files_that_I_want_to_compress.txt and_another_one_too.doc":

```
rar a -hp archive_name.rar files_that_I_want_to_compress.txt and_another_one_too.doc
```

It will ask you to set a password, then add and encrypt the files and headers.


If you want to do a directory instead of files, do this:

```
rar a -hp archive_name.rar Pictures/
```

If you need to open an archive, you can do it from the archive manager GUI. 


Arr maitee, yall are been able to rar, drive a car, and open a jar at the bar!

8-)

---

### Post by stchman on 2007-12-07
> **palemmo said:**
> Hi, i'm looking for a simple program that is similar to winzip/rar/ace of winzoz.
A need a simple gui that permits to: 
[LIST=1]
[*]compress files
[*]uncompress files
[*]compress/uncompress to multiple archives
[*]compress with a password
[/LIST]

For example for now I have a linux application that is divided into 11 packets, I don't know how to unpack it...and put all in one....
file.r00
file.r01
file.r02
.......
file.r11
that should be only one file, file.rar
I have to open it via microsoft because I don't know how to uncompress....
Thanks
(PS I'm relatively new... Excuse me if I wronged section)

Archive Manager (aka File Roller) will do everything you want.  You will need to install some restricted packages.

```
sudo apt-get -y install rar unrar p7zip p7zip-full
```

This will allow Arhive Manager to now deal with .rar and .7z archives.

---

### Post by palemmo on 2007-12-24
the solution was krusader :D

---

### Post by erginemr on 2007-12-24
> **palemmo said:**
> the solution was krusader :D

Although Krusader is a top-notch double-panel file manager in its own right, it still is a KDE app and requires KDE libraries to run (thus more hard disk space & memory usage).

And it does not deserve to be the "only" solution. The above suggestions were also correct solutions, and were more valuable IMHO because they either involve CLI (command line interface) or native GTK+ apps (unless you are using Kubuntu).

---

### Post by ~LoKe on 2007-12-24
```
sudo apt-get install unrar
unrar x *.r00
```

That will unpack the file from the split archives.

---

