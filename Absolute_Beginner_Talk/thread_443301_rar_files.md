---
title: "rar files"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by yimmmy on 2007-05-14
yo i just downloaded a RAR file and i dont know how to open it when i double click on it it just  say can not open this fil,   
is there a program that i can download to open and veiw rar files?
thnaks

---

### Post by viciouslime on 2007-05-14
You need to install the package "unrar" then you will be able to just double click it. There is also a free version (i.e. not proprietary software) but that can't handle the very latest rar files so might not be any use to you. I think that is called something like "unrar-free" check in synaptic :)

---

### Post by yimmmy on 2007-05-14
were can i get that UNRAR at 
im not sure how to download things and install them from the internet on linux

---

### Post by Fangthon Funk on 2007-05-14
Type this in the terminal:
```
sudo apt-get -y install unrar 
```

---

### Post by James SoCal USA on 2007-05-14
Go to [http://www.rarlabs.com/download.htm](http://www.rarlabs.com/download.htm) for the downloads available from RarLabs.  I am new to Lx but have used it on Wx with great success.

James

---

### Post by _hawk_ on 2007-05-14
Also, if you get used to the terminal, it actually works great. You can install rar from the repositories by typing
sudo apt-get install rar
and
sudo apt-get install unrar

Then, rar e folder/rarfile.rar

will extract the file into the folder you are currently in.

---

### Post by yimmmy on 2007-05-14
ok thanks guys i got it to work 
thanks alot now i have to go work on the other 5000 problem s i have 

thanksyou:guitar:

---

### Post by neotasic1 on 2007-05-14
> **_hawk_ said:**
> Also, if you get used to the terminal, it actually works great. You can install rar from the repositories by typing
sudo apt-get install rar
and
sudo apt-get install unrar

Then, rar e folder/rarfile.rar

will extract the file into the folder you are currently in.

Quick question - is there a gui for this app or does it only work from the command line?  If only from the command line, is there a man function to explain switches etc?

---

### Post by viciouslime on 2007-05-14
> **neotasic1 said:**
> Quick question - is there a gui for this app or does it only work from the command line?  If only from the command line, is there a man function to explain switches etc?

Fileroller works with it. That is the application you normally use for opening archives, once you have installed the above package, fileroller will detect it and it will just work :)

---

### Post by viciouslime on 2007-05-14
> **yimmmy said:**
> were can i get that UNRAR at 
im not sure how to download things and install them from the internet on linux

You can do as above using the command line, or you can go to System/Administration/Synaptic Package Manager to install software. Applications/Add Remove is also very useful if you want gui applications/games.

---

### Post by neotasic1 on 2007-05-14
> **viciouslime said:**
> Fileroller works with it. That is the application you normally use for opening archives, once you have installed the above package, fileroller will detect it and it will just work :)

Thank you - I will try it

---

