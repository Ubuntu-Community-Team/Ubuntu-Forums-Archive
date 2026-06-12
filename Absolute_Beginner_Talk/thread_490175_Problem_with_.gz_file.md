---
title: "Problem with *.gz file"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by jmfa59 on 2007-07-02
After extracting the file I end up with with a file with a lock sign to the top right of the Icon what does it mean and what to do with it.

---

### Post by lisati on 2007-07-02
Did you unpack it as the root user?

---

### Post by jmfa59 on 2007-07-02
No I just right click on it and choose extract here if you think I should unpack it as root how to do it I know how to become root user in the terminal what to do affter that

---

### Post by nitro_n2o on 2007-07-02
to become a root all wht u need to do is to prefix any command you type with the word sudo 

so if your tar.gz file is in a folder called 'files' in your home directory u should do the following: 

cd files
sudo tar -xzvf filename.tar.gz 
Then type your password

sudo: be a root temporarily 
tar: command line program
-xzvf: command line args 
x: extract 
z: for the .gz extension 
v: verbose (useful sometimes) 
f: file name, so ur program expects a file name to extract 

Hope that helps

---

### Post by nitro_n2o on 2007-07-02
i don't use nautilus that much.. but i believe if your right click the folder and open properties then go to the permissions tab you can get rid of the lock sign ;)

---

### Post by jmfa59 on 2007-07-02
nitro_n2o  
Thank you Imanage to get rid of the locck sign.
but I couldn't open by theway it is not tar.gz it i686.gz the file name is tils_d_n.i686.gz any idea

This is the message Igot in terminal 

jasem@ubuntu:~/Desktop$ sudo tar -xzvf tils_d_n.i686.gz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

---

