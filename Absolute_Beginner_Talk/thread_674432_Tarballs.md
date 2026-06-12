---
title: "Tarballs"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Mitchlb on 2008-01-21
I can't work with tarballs... It's killing me. 

# tar xvzf package.tar.gz (or tar xvjf package.tar.bz2)
# ./configure
# make
# make install

I try to do this every time. It runs the ./configure fine in the terminal, but won't make. What's my problem?

---

### Post by dstew on 2008-01-21
Have you installed the **build-essential** package yet?

---

### Post by emarkd on 2008-01-21
Do you have the build-essential package installed?  It's got make and a few other things you'll need in it.

sudo apt-get install build-essential  <-- if you needed it.

---

### Post by ice60 on 2008-01-21
you also have to make sure you have a file called **configure** in the directory you are running ./configure from.

so you unpack, then run **cd the_name_of_the_decompressed_directory**
then run ./configure

EDIT: i didn't read your post lol. i'm the world's worst at helping, i normally don't waste anyone's time with it. :-\"

---

### Post by Sef on 2008-01-21
Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by bodhi.zazen on 2008-01-21
> **Mitchlb said:**
> I can't work with tarballs... It's killing me. 

# tar xvzf package.tar.gz (or tar xvjf package.tar.bz2)
# ./configure
# make
# make install

I try to do this every time. It runs the ./configure fine in the terminal, but won't make. What's my problem?

Well, a few comments.

First a tar.gz is just an archive , you need to look at the contents, perhaps a README ? Some archives contain python or other install scripts ...

Second, most, but not all, compile errors are due to dependencies. In Ubuntu you may need to install a few *-dev packages.

Third, it would help if you gave us a link to what you are trying to install and an exact error message.

---

### Post by Mitchlb on 2008-01-21
I don't have internet access on that particular computer right now so i haven't installed anything that didn't come with my installation of gutsy gibbon (7.10)

---

