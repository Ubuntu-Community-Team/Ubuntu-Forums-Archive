---
title: "[SOLVED] StarDict"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by al.adab on 2007-08-31
Hello. I've downloaded StarDict (successfully). I don't really understand what I should do to use it to consult dictionaries. Here is what I've tried to do: 

1) downloaded **stardict-freedict-eng-deu-2.4.2.tar.bz2** on **/home/XXXXXXX** (successful)
2) used the command **~$ tar -xjvf stardict-freedict-eng-deu-2.4.2.tar.bz2** (successful)

At this stage, another folder appeared at **/home/XXXXXXX** : inside there is another folder called **dictd_www.freedict.de_eng-deu.dict.dz** which looks like an archive, but cannot be opened. 

3) double-clicked on the folder **stardict-freedict-eng-deu-2.4.2.tar.bz2** 
4) double-clicked on **stardict-freedict-eng-deu-2.4.2**
5) found the following three files: 

- dictd_www.freedict.de_eng-deu.ifo
- dictd_www.freedict.de_eng-deu.dict.dz
- dictd_www.freedict.de_eng-deu.idx

I then tried the command 

**sudo mv dictd_www.freedict.de_eng-deu.dict.dz /usr/share/stardict/dic**

and got the following error: 

**mv: cannot stat `dictd_www.freedict.de_eng-deu.dict.dz': No such file or directory**

Can anyone help me? Thank you!!!

---

### Post by s26c.sayan on 2007-08-31
You should simply move the entire folder  **stardict-freedict-eng-deu-2.4.2 **that you have just uncompressed, with all its contents (i.e. the 3 files) to the location  /usr/share/stardict/dic.

First, make sure the specified directory exists. If not, create it :
```
sudo mkdir /usr/share/stardict/dic
```Next move the uncompressed folder there :
```
sudo mv /home/XXXXXXX/stardict-freedict-eng-deu-2.4.2/ /usr/share/stardict/dic/
```This should do the trick!

---

### Post by al.adab on 2007-08-31
It did the trick!!! THANK YOU!!!

---

