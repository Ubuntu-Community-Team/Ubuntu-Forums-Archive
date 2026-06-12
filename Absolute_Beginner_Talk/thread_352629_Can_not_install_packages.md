---
title: "Can not install packages"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by dukeofkent on 2007-02-03
Hi I am total non techie n00b so kindly bear with me.

Amongs the host of problems that I am facing w ith Ubuntu, I am not able to install any packages with tar.gz and tar.bz2 extensions.
I change the directory to appropriate one

The trouble starts when i type ./configure
this is what I get 
bash: ./configure: No such file or directory

I read somewhere that we can ignore this and go ahead with make
Now I get this
make: *** No targets specified and no makefile found.  Stop.


I tried this with ABC and another couple of packages. The readme file of this package had nothing but the website address.

Also having read somewhere, I installed the build essential thing but it was already there and  updated too.
Any help will be appreciated.

---

### Post by taurus on 2007-02-03
While in that newly created directory, what's the output of this command then?

```
ls -la
```

---

### Post by Rui Pais on 2007-02-03
have you done:
```
sudo apt-get install build-essential
```?

---

### Post by dukeofkent on 2007-02-03
> **taurus said:**
> While in that newly created directory, what's the output of this command then?

```
ls -la
```


> drwxr-xr-x 4 ******* *******  4096 2003-09-29 03:06 .
drwxr-xr-x 5 ******* *******  4096 2007-02-04 02:04 ..
-rwxr-xr-x 1 ******* *******   297 2003-09-29 03:05 abc.conf
-rwxr-xr-x 1 ******* ******* 16826 2003-09-29 02:05 abcdetailframe.py
-rwxr-xr-x 1 ******* ******* 20230 2003-09-29 02:05 abcengine.py
-rwxr-xr-x 1 ******* *******   418 2003-09-29 02:06 abc.ini
-rwxr-xr-x 1 ******* *******  4478 2003-09-29 02:05 abc.nsi
-rwxr-xr-x 1 ******* ******* 21433 2003-09-29 03:05 abcoptiondlg.py
-rwxr-xr-x 1 ******* ******* 39903 2003-09-29 02:37 abc.py
-rwxr-xr-x 1 ******* ******* 17827 2003-09-29 02:05 abc_tweak.py
-rwxr-xr-x 1 ******* *******  1747 2003-09-29 02:05 aboutmedlg.py
-rwxr-xr-x 1 ******* *******    13 2003-09-29 02:05 announce.lst
drwxr-xr-x 2 ******* *******  4096 2003-09-29 03:06 BitTorrent
-rwxr-xr-x 1 ******* *******  5933 2003-09-29 02:05 btcompletedirgui.py
-rwxr-xr-x 1 ******* *******  2192 2003-09-29 02:05 btcompletedir.py
-rwxr-xr-x 1 ******* *******  7652 2003-09-29 02:05 btmakemetafile.py
-rwxr-xr-x 1 ******* ******* 18175 2003-09-29 02:05 btmaketorrentgui.py
-rwxr-xr-x 1 ******* *******    70 2003-09-29 02:05 clean.bat
-rwxr-xr-x 1 ******* *******  2034 2003-09-29 02:05 filemanager.py
-rwxr-xr-x 1 ******* *******  2073 2003-09-29 02:05 getscrapedata.py
-rwxr-xr-x 1 ******* *******  7496 2003-09-29 02:05 globaluploaddlg.py
-rwxr-xr-x 1 ******* *******  2195 2003-09-29 02:05 guimanager.py
-rwxr-xr-x 1 ******* ******* 70102 2003-09-29 02:05 icon_abc.ico
-rwxr-xr-x 1 ******* *******  4077 2003-09-29 02:05 interconn.py
-rwxr-xr-x 1 ******* ******* 11981 2003-09-29 02:05 license.txt
-rwxr-xr-x 1 ******* *******    92 2003-09-29 02:05 makedist.bat
-rwxr-xr-x 1 ******* *******    82 2003-09-29 02:05 maketest.bat
-rwxr-xr-x 1 ******* *******   141 2003-09-29 02:05 readme.txt
-rwxr-xr-x 1 ******* ******* 51778 2003-09-29 02:05 scheduler.py
-rwxr-xr-x 1 ******* *******   248 2003-09-29 02:05 setupabc.py
drwxr-xr-x 2 ******* *******  4096 2003-09-29 03:06 torrent
-rwxr-xr-x 1 ******* *******     0 2003-09-29 03:06 torrent.lst

Thats what I get for ABC. ******* represnts the username

---

### Post by taurus on 2007-02-03
It's a python language.  Therefore, there are no ./configure or make.  You run it directly as

```
./setupabc.py
```

---

### Post by dukeofkent on 2007-02-03
> **Rui Pais said:**
> have you done:
```
sudo apt-get install build-essential
```?

Yes. Did it again.
> Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by dukeofkent on 2007-02-03
> **taurus said:**
> It's a python language.  Therefore, there are no ./configure or make.  You run it directly as

```
./setupabc.py
```

can you elaborate a bit?
IS it applicable for all such packages? How do I know which one is in this language?

---

### Post by taurus on 2007-02-03
Do you see the .py at the end?  That's usually the extension for python script.  And is that usually the case?  No.  That's why you need to look at the files in the directory to see exactly what they are.  If you see a configure file, then chances are you need to configure and build it.  Otherwise, you just run it directly from a terminal.  Of course, you should always read the README, INSTALL, or in this case, readme.txt.

```
more readme.txt
```

---

### Post by dukeofkent on 2007-02-03
> **taurus said:**
> Do you see the .py at the end?  That's usually the extension for python script.  And is that usually the case?  No.  That's why you need to look at the files in the directory to see exactly what they are.  If you see a configure file, then chances are you need to configure and build it.  Otherwise, you just run it directly from a terminal.  Of course, you should always read the README, INSTALL, or in this case, readme.txt.

```
more readme.txt
```

As I already mentioned this was what I found in readme.txt

"ABC [Yet Another Bittorrent Client] V.2.4.3

			===================================

 Please visit :  http://pingpong-abc.sourceforge.net/"

Now do I use the command that you gave when I enter the directory and thats it?

---

### Post by dukeofkent on 2007-02-07
can anyone help me with this problem?
I am not able to install any packages with tar.gz or tar.bz2 extensions,
Please help.

---

### Post by taurus on 2007-02-07
> **dukeofkent said:**
> can anyone help me with this problem?
I am not able to install any packages with tar.gz or tar.bz2 extensions,
Please help.

Look at section 4 of this guide.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

