---
title: "Easy Ubuntu ?"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-06-19
Downloaded it, extracted it, how do I start it ????  :confused:

---

### Post by Jagot on 2006-06-19
Instructions are on the website:

[http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)

---

### Post by Drakkor on 2006-06-19
drakkor@drakkor:~$ wget [http://robotgeek.org/eu/easyubuntu-3.01.tar.gz](http://robotgeek.org/eu/easyubuntu-3.01.tar.gz)
--12:34:03--  [http://robotgeek.org/eu/easyubuntu-3.01.tar.gz](http://robotgeek.org/eu/easyubuntu-3.01.tar.gz)
           => `easyubuntu-3.01.tar.gz'
Resolving robotgeek.org... 69.56.131.114
Connecting to robotgeek.org|69.56.131.114|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 111,173 (109K) [application/x-tar]

100%[====================================>] 111,173      277.15K/s

12:34:04 (275.83 KB/s) - `easyubuntu-3.01.tar.gz' saved [111173/111173]

drakkor@drakkor:~$ tar -zxf easyubuntu-3.01.tar.gz
drakkor@drakkor:~$ cd easyubuntu
drakkor@drakkor:~/easyubuntu$ sudo python easyubuntu.in
python: can't open file 'easyubuntu.in': [Errno 2] No such file or directory
drakkor@drakkor:~/easyubuntu$
drakkor@drakkor:~/easyubuntu$

---

### Post by %hMa@?b&lt;C on 2006-06-19
sudo python ./easyubuntu.in

---

### Post by Drakkor on 2006-06-19
drakkor@drakkor:~$ sudo python ./easyubuntu.in
Password:
python: can't open file './easyubuntu.in': [Errno 2] No such file or directory
drakkor@drakkor:~$
I looked in the easy ubuntu folder and it seems I don't have that easyubuntu.in
file.

---

### Post by %hMa@?b&lt;C on 2006-06-19
sudo python ./easyubuntu.py

---

### Post by Drakkor on 2006-06-19
Thanks for bearing with me, jeff, I do have the easyubuntu.py file ,but it seems
it can't find it !!
drakkor@drakkor:~$ sudo python ./easyubuntu.py
Password:
python: can't open file './easyubuntu.py': [Errno 2] No such file or directory

---

### Post by %hMa@?b&lt;C on 2006-06-19
try to wget it again, then tar it again, then see if it works using the ./easyubuntu.py file

---

### Post by Drakkor on 2006-06-19
Wow ! :D  It works now,thanks jeff, one last question, is the only way to start this is through the terminal ? Thanks again !

---

### Post by %hMa@?b&lt;C on 2006-06-19
```
sudo alacarte
```
then add an entry in administration and for the the command do 
```
gksudo python /home/drakkor/easyubuntu/easyubuntu.py
```

---

