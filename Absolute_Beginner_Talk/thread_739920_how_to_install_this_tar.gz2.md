---
title: "how to install this tar.gz2"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by giovanni90 on 2008-03-30
Hi, i'm trying to install this file streamerone.0.3.tar.bz2 but i can't seem to install it.
Anybody can please help me?
Thank you!

---

### Post by 505 on 2008-03-30
If you already downloaded the file, open it and it should open in the archive manager, from where you can unpack it. Extract it to any location. Then just open the folder and double click on 'streamerone' and a firefox window should open.
Alternatively you can run it from a terminal by going to the directory and typing './streamerone' If there are errors you will see them in the terminal.

---

### Post by seshomaru samma on 2008-03-30
also read [this]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by giovanni90 on 2008-03-30
no, it doesn't work.
any other way?

---

### Post by shirilover on 2008-03-30
Some simple steps can be found here -> [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Well, first thing to do is to extract the contents of the archive.
From the console(gnome-terminal), assuming the file is located on the Desktop
```

cd ~/Desktop
tar -xjvf streamerone.0.3.tar.bz2

```
This should result in a folder named streamerone.0.3 being created with the contents of the archive contained within. This can also be accomplished by opening the file and choosing extract.

Next, if the archive contained a pre-compiled binary, to run the executable file, either:
~/Desktop/streamerone.0.3/nameofbinary , from the terminal or Run dialog.
or, if the binary has the execuatable bit set, double-click the binary file from within nautilus.

Should this not be the case, as most often occurs. You will have source code which needs to be compiled. In most cases you will need to install development files so that the program will compile successfully.
Once you have the necessary -dev packages installed, it usually becomes a simple matter of three commands. From within the source code directory:
```

./configure
make
sudo make install

```
If you receive errors during the configure script, you will need to install the appropriate -dev package(s) before running configure again.

---

### Post by giovanni90 on 2008-03-30
can anybody download the file from [www.streamerone.com](www.streamerone.com) and try to make it install and work.then, tell me how to do it?
Thank you!

---

### Post by bumanie on 2008-03-30
I'm on a windows machine at work, so can't do that. Is the tar.gz2 file on your destop?

---

### Post by 505 on 2008-03-30
I just did, before posting my original reply. Running the program opens Firefox with the address [http://127.0.0.1:6777](http://127.0.0.1:6777) and then the channels are displayed after some time of loading.

---

### Post by jocko on 2008-03-30
> **giovanni90 said:**
> can anybody download the file from [www.streamerone.com]("http://www.streamerone.com") and try to make it install and work.then, tell me how to do it?
Thank you!

I just downloaded it to see what it is, and as far as I can see it will not require any installing.
Just download the file to yor desktop, then right click it an select "extract here".
That will create a folder called "Streamerone.Beta.0.3" on your desktop.

To start it, just open up a terminal and type these commands:
```
cd ~/Desktop/Streamerone.Beta.0.3/
./streamerone
```Notice that I have no idea how to actually use the program or set it up to work properly, so for me it just hangs at "connecting to <some IP address>" and does not open up any firefox window... might be because I'm behind a router and would need to open up some ports..

---

### Post by giovanni90 on 2008-03-30
> **505 said:**
> I just did, before posting my original reply. Running the program opens Firefox with the address [http://127.0.0.1:6777](http://127.0.0.1:6777) and then the channels are displayed after some time of loading.

when i click on streamerone, it doesn't open any firefox page
did you do anything to firefox or any programs that is related to the correct functioning of streamerone?

---

