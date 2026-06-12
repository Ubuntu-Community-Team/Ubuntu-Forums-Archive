---
title: "Siemens CX65 and Ubuntu"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by wolfshark on 2006-06-01
I have Ubutu Dapper and i want to connect my mobile phone Siemens CX65 to the computer. I want to browse the phone content and to see some photos. I have usb cable but no software for Linux. I tried KMobile tools, but with this application, i cannot browse my mobile. Can somebody help me? :confused:

---

### Post by wolfshark on 2006-06-01
Please somebody help me :(

---

### Post by misho_cg on 2006-06-02
I have siemens C65.
I download siefs from  [http://chaos.allsiemens.com/siefs/]("http://chaos.allsiemens.com/siefs/")
next i install these pakages with Synaptic:
libfuse2
libfuse-dev
unzip downloaded file (in your home dir for example)
cd to unziped directory and type:

```
./configure
```

if you not get errors type:

```
make
```

and next

```
sudo make install
```

try to load fuse module:

```
sudo modprobe fuse
```

if not get any messages the module is loaded

make your own dir in /media

```
mkdir /media/mobille
```

and try to mount phone with flowing command:

```
sudo mount -t siefs /dev/ttyUSB0 /media/mobille
```

if all is good in /media/mobille/ is your's phone

enjoy :)

---

### Post by wolfshark on 2006-06-02
I tried this, but when I click on the mounted folder my Nautilus freezes
** (nautilus:7470): WARNING **: Hit unhandled case 6 (in/out error) in fm_report_error_loading_directory

---

### Post by Klemik on 2006-07-18
I've installed all accordint to inctruction included here, and...
```

klemik@Klemik:~/fuse-2.5.3$ sudo mount -t siefs /dev/ttyUSB0 /media/mobile
fuse: failed to exec fusermount: No such file or directory
klemik@Klemik:~/fuse-2.5.3$ sudo fusermount /dev/ttyUSB0 /media/mobile
fusermount: old style mounting not supported

```

wtf ?
I also copied fusermount from /usr/local/bin to /bin but it gives me same error ](*,)

---

### Post by Klemik on 2006-07-19
ok I copied fusermoun to /usr/bin and it works now. Thanks for this instruction :)

---

### Post by Klemik on 2006-07-19
Uhm, I thought it works, but data on mobile is read only even if I call -o rw options :( Any ideas ?

---

### Post by dangerous666 on 2006-07-26
In my case, both the installation and mounting were sucessful. But when I try to access the mounted point, it gives me an I/O error... Even accessing as root. Any ideas?

---

