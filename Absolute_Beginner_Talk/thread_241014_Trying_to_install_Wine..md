---
title: "Trying to install Wine."
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Matt827 on 2006-08-21
I've been to Winehq.org and tried their source files and binary files but they are out of date and the addresses don't work when i make them into a custom repository.

So, i've saught out how to download the .deb file to my computer and install it that way. However... 1386 is an improper format so it comes up with an error and never installs. the 32-bit program isn't running on my 64-bit chip. However on the site there is a "work-around" procedure. As follows:
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Building Wine on Ubuntu / Kubuntu 6.06 (Dapper Drake)

First one must install the necessary libraries: Finding the correct set may take a few minutes and several tries.

configure will find several omissions, but a few will only be noticed by the 'make' steps.

Make sure you have libc6-i386 and the libc6-dev-i386 library installed. It is need to compile 32 bit on a 64 bit operating system.

The following add links, that the library install does not make:

# Do this as *root* by hand, it won't work as a script as written.
cd /usr/lib32
ln -s libX11.so.6 libX11.so
ln -s libXext.so.6 libXext.so
ln -s libfreetype.so.6 libfreetype.so

Run configure, build and install with:

LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32"  ./configure
make depend
make all
sudo make install

If all needed libraries are present there will be no missing-library warnings or errors anywhere.

wine seems to work (installed in /usr/local) 
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Yeah... i'm new to this and that looks like ALOT of stuff. How do i make sure the necessary libraries are installed as it tells me to do in the first few sentences? I'm lost in this.:-#

---

### Post by jrjr on 2006-08-21
.

---

### Post by taurus on 2006-08-21
If you want to run 32bit binaries in 64bit environment, you need to install the 32bit libraries on your system first.  Otherwise, they're just going to bomb you right now.

---

### Post by Matt827 on 2006-08-21
how do i install the 32 bit libraries. Keep in mind i no..NOTHING! :P

---

### Post by Matt827 on 2006-08-21
i installed the two it mentioned now. They are working (i guess). Now what is the next section referring to?

++++++
The following add links, that the library install does not make:

# Do this as *root* by hand, it won't work as a script as written.
cd /usr/lib32
ln -s libX11.so.6 libX11.so
ln -s libXext.so.6 libXext.so
ln -s libfreetype.so.6 libfreetype.so
++++++

when i do those i am getting a "permission denied" error.
How do i work around that?

---

### Post by Matt827 on 2006-08-21
anybody?

---

### Post by The Mekon on 2006-08-21
Try [Automatix]("http://www.getautomatix.com/")

---

### Post by Shortgeek on 2006-08-21
Are you doing it as root?

---

### Post by Matt827 on 2006-08-21
i get every thing to work fine except for the last section...

 LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure

that code doesn't work..lol

I get 

bash: ./configure: No such file or directory

---

