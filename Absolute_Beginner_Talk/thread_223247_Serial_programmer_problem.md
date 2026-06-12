---
title: "Serial programmer problem"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by Laston on 2006-07-26
I'm new to linux, I have it installed about a week ago and I find helpful programs like Synaptic, but I need a way to make the software PonyProg for Linux to work, and I do not know how, can anybody help me installing it?
thx

---

### Post by moma on 2006-07-26
It seems to me that the Linux version of PonyProg is utterly old. It support 2.4 kernels only?? 

An idea:
You may try to run Pony using wine.  Do this:

1) Add this repostory line into your /etc/apt/sources.list 

[COLOR="Purple"]deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/[/COLOR]

$ sudo gedit /etc/apt/sources.list 

Save the file.

2) Update package index (list of packages)
$ sudo apt-get update 

3) Install wine
$ sudo apt-get install --reinstall wine
-----------------

4) Download ponyprogV117h.zip (Windows version) and Unzip it.

5) Run setup.exe in wine.
$ wine setup.exe 

Run Pony in wine
$ wine $HOME/.wine/drive_c/Program\ Files/PonyProg/PONYPROG.EXE
-------------------

BTW: This is the de-facto libarary for serial-programming in Linux
[http://sourceforge.net/projects/ezv24/]("http://sourceforge.net/projects/ezv24/")

---

### Post by patpaa on 2006-08-03
I've been struggling with the very same problem for a couple of days now, and I just got ponyprog2000 to work... 

Here's what I did:
[LIST=1]
[*]Downloaded ponyprog-2.06c-rh70.tar.gz
[*]'su root' and untar the file
[*]When i tried to run 'ponyprog2000', it complains about some missing file. I used google to find the missing package needed (libstdc++ ...something, sorry can't remember the exact name). Installed the package.
[/LIST]

Now it runs. Good luck!

---

### Post by Endolith on 2008-01-04
> **patpaa said:**
> 'su root' and untar the file

I guess you have to put the files in the directories that are inside the tar.gz for it to run when you type "ponyprog2000".  (/usr/local/...)

> When i tried to run 'ponyprog2000', it complains about some missing file. I used google to find the missing package needed (libstdc++ ...something, sorry can't remember the exact name).

"ponyprog2000: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory"

To find the package, you can do "sudo apt-file update" and then "apt-file search libstdc++-libc6.2-2.so.3":

> libstdc++2.10-dbg: usr/lib/debug/libstdc++-libc6.2-2.so.3
libstdc++2.10-glibc2.2: usr/lib/libstdc++-libc6.2-2.so.3

So I installed the second one and the program runs now.  Not sure if it works, but it runs.  ;-)

(Still have to build the hardware...)

---

### Post by locutus42 on 2008-03-26
I just downloaded and built PonyProg v2.07c Beta on Gutsy and it runs. Here is what I did to get it running:
NOTE: I've already installed build-essential so that might be needed( sudo apt-get install build-essential ).

```

cd /tmp
wget http://downloads.sourceforge.net/ponyprog/Pony_Prog2000-2.07c.tar.gz
tar -xzf Pony_Prog2000-2.07c.tar.gz
cd PonyProg2000-2.07c

sudo apt-get install gcc-3.4 g++-3.4
sudo apt-get install libxt-dev libxaw7-dev

NOTE: edit v/Config.mk and add the following line after the other HOMEV lines:
HOMEV   =       /tmp/PonyProg2000-2.07c/v

make

```

you should now have a running PonyProg v2.07c beta and can test it with this:
bin/ponyprog2000

To install it into your system, run:
sudo make install

---

