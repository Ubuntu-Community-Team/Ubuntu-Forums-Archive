---
title: "Tar.gz"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by That Guy X on 2006-08-29
Hi,how do i install tar.gz files?

---

### Post by LotsOfPhil on 2006-08-29
if you have the file:

potato.tar.gz

It means that you have a gzipped and tar-ed file. You can undo them both with the tar command. Type:

tar -xzvf potato.tar.gz

x means extract
z means unzip
v means verbose, this prints out each file that comes out of the archive
f tells it to look for a file, in this case potato.tar.gz

You can type "man tar" for lots more info and options.

---

### Post by nazgulord on 2006-08-29
Tar.gz files are archives. You usually extract the archive using:

tar xzvf filename

and then do stuff with the extracted files.

I might be able to help you more if you could tell me what it actually was that you downloaded/are trying to install.

nazgulord.

---

### Post by Omnios on 2006-08-29
tar-gz etc are compressed fiels that have to be uncompressed. You can wither double click it to launch the file roller to uncompress them or use the tar terminal commands.
[http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=t/tar](http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=t/tar)

---

### Post by Anonii on 2006-08-29
> **That Guy X said:**
> Hi,how do i install tar.gz files?

.tar.gz are called tarballs, and they are archives, like .zip and .rar are in Windows. 
You can simply open them by using the terminal , going to the directory where they are and typing:
*tar xvf <name_of_tarball>.tar.gz*
You will obviously change the <name_of_tarball> to the name your package has.
Also check "man tar" for more options!
You can also extract them with a GUI, by just double-clicking them and drag and dropping the files/folders inside in a different directory.

After that you will have the folder in which there is the application you have to install. I will recommend you to read the INSTALL or README file thats always in there, to see how to install them.

Finally, you _HAVE_ to read this:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Good Luck :)

---

