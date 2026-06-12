---
title: "Installing cabextract"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by shamreez on 2007-05-21
Hi all,

I know this might sound really stupid but i have no other options...:(

How do i install the cabextract tu ubuntu 6.06

---

### Post by ThinkBuntu on 2007-05-21
Use synaptic, of if you like the Terminal:
```
sudo aptitude install cabextract
```

---

### Post by shamreez on 2007-05-21
i tried that...
but it is giving the error 
"Couldnt find any packaged whose name or description matched "cabextract"

do i have to download the cabextract package seperately

---

### Post by Famicommie on 2007-05-21
cabextract is in the ubuntu dapper repositories, I just checked. Why don't you try downloading and installing the debian file? [http://http.us.debian.org/debian/pool/main/c/cabextract/cabextract_1.2-2_i386.deb](http://http.us.debian.org/debian/pool/main/c/cabextract/cabextract_1.2-2_i386.deb)

---

### Post by shamreez on 2007-05-21
once i downoad the deban file what am i supposed to do...
hope i dont sound real stupid

---

### Post by vtel57 on 2007-05-21
Nothing stupid about cabextract. It's a very useful little tool. You probably don't have all your repos opened in Ubuntu. If you care to, you can just d-load and install it from [HERE](http://www.kyz.uklinux.net/cabextract.php).

Luck!

---

### Post by Famicommie on 2007-05-21
double click on it :D

---

### Post by shamreez on 2007-05-21
i tried that too:(

i think it is not my day...

I am having the .deb file of cab extract in my desktop.

if i double click on it it tells me that "The utility is not in your path"

If i try to install it using kubuntu package menu it gives me error...

am i missing something here

---

### Post by shadwstalkr on 2007-08-14
Don't feel bad about asking questions.  Some of this stuff can be hard to figure out.

To install a package you downloaded, open a console and type
```

sudo dpkg -i file

```
where "file" is the path to the package.  If it's on your desktop you can type
```

ls ~/Desktop/*.deb

```
to find the right path.

Hope that helps!

---

