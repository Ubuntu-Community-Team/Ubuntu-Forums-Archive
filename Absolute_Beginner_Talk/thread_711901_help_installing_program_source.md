---
title: "help installing program source"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by HakerDemon on 2008-03-01
Im sorry to bother you all, but whn I go to compile source i run into a barrier,  I can do ./configure, and then Make.  But when I give the command "make Install" I get :

~/Desktop/nmap-4.53$ make install
./shtool mkdir -f -p -m 755 /usr/local/bin /usr/local/man/man1 /usr/local/share/nmap
mkdir: cannot create directory `/usr/local/man/man1': Permission denied
chmod: cannot access `/usr/local/man/man1': No such file or directory
mkdir: cannot create directory `/usr/local/share/nmap': Permission denied
chmod: cannot access `/usr/local/share/nmap': No such file or directory
make: *** [install-nmap] Error 1

Now I am the admin on my computer too.   so can anybody help me?? thank you

---

### Post by amrclutch1 on 2008-03-01
```

cd ~/Desktop/nmap-4.53
sudo make install

```

try this.

---

### Post by PeterJS on 2008-03-01
You are an admin all the time, but you only have admin rights when you explicitly request them with sudo. so you'd want to use:
```

sudo make install

```

---

### Post by LinuxGuy1234 on 2008-03-01
> **HakerDemon said:**
> Im sorry to bother you all, but whn I go to compile source i run into a barrier,  I can do ./configure, and then Make.  But when I give the command "make Install" I get :

~/Desktop/nmap-4.53$ make install
./shtool mkdir -f -p -m 755 /usr/local/bin /usr/local/man/man1 /usr/local/share/nmap
mkdir: cannot create directory `/usr/local/man/man1': Permission denied
chmod: cannot access `/usr/local/man/man1': No such file or directory
mkdir: cannot create directory `/usr/local/share/nmap': Permission denied
chmod: cannot access `/usr/local/share/nmap': No such file or directory
make: *** [install-nmap] Error 1

Now I am the admin on my computer too.   so can anybody help me?? thank you

Use:
```
sudo make install
```
instead.

---

### Post by amrclutch1 on 2008-03-01
beat ya both :)

---

### Post by sisco311 on 2008-03-01
try
```
sudo make install
```
 
You need root privilege to install.
EDIT: D'oh!

---

