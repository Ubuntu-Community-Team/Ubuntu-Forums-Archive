---
title: "help compiling gtwitter 1.0 beta"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by fiziks on 2007-07-07
hello, long time lurker.

i was wondering if someone could steer me in the right direction here.  as you guessed i'm apart of the masses of new linux users.  i have recently started compiling programs from source, and i'm having a little trouble getting the gtwitter 1.0 beta working.

i have found a .deb package for an earlier version of gtwitter, but i was having all kinds of problems with it.

i used the standard compiling process,

1.  created the directory.
2.  make.
3.  and make install.

everything works until i use the 'make install' command.

```
fiziks@fiziks-box:~/gtwitter-1.0beta$ make install
Making install in gtwitter
make[1]: Entering directory `/home/fiziks/gtwitter-1.0beta/gtwitter'
make[2]: Entering directory `/home/fiziks/gtwitter-1.0beta/gtwitter'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
 /usr/bin/install -c './bin/Release/gtwitter' '/usr/local/bin/gtwitter'
/usr/bin/install: cannot remove `/usr/local/bin/gtwitter': Permission denied
make[2]: *** [install-binSCRIPTS] Error 1
make[2]: Leaving directory `/home/fiziks/gtwitter-1.0beta/gtwitter'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/fiziks/gtwitter-1.0beta/gtwitter'
make: *** [install-recursive] Error 1

```

any help would be awesome.

thanks!:p

---

### Post by ajgreeny on 2007-07-07
Make sure you have the **build-essential** package installed and then **"make"** should go as you want.

---

### Post by fiziks on 2007-07-07
i just checked my package manager and and **build-essential** is installed..

any other suggestions?

---

### Post by tassoman on 2007-09-19
How to compile and keep all stuff into /opt/gtwitter?

Or package into a .deb easily ?

---

### Post by Steveway on 2007-09-19
If you want to create a .deb then install checkinstall and instead of make install do this:
sudo checkinstall

make install only works of you have superuserrights, so the command should be:
sudo make install
But I would prefer to make a .deb with checkinstall if possible.

---

### Post by tassoman on 2007-09-19
Go to the GetDeb page: [http://www.getdeb.net/app.php?name=gTwitter](http://www.getdeb.net/app.php?name=gTwitter)

:popcorn:

---

