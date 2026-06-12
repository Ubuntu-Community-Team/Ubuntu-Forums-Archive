---
title: "Compiled Transmission (tar.gz) and it disappeared... also, no GTK?"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by zachws on 2006-07-02
Hello All,
I just compiled transmission (my fav bittorent client) from source (tar.gz). everything went well but I don't know where it went and I would like to run it.

Also, while running 'make', it said I didn't have GTK+, which I though I did?

any ideas?

```
zachws@zachws-laptop:~/Desktop$ cd Transmission-0.6.1
zachws@zachws-laptop:~/Desktop/Transmission-0.6.1$ ./configure
System:  Linux
OpenSSL: yes
GTK+:    no

Now use GNU make to build Transmission.
It may be called 'make' or 'gmake' depending on your system.
zachws@zachws-laptop:~/Desktop/Transmission-0.6.1$ make
Checking SVN revision...
* Building libtransmission
Checking dependencies...
Cc transmission.o
Cc bencode.o
Cc net.o
Cc tracker.o
Cc peer.o
Cc inout.o
Cc metainfo.o
Cc sha1.o
Cc utils.o
Cc fdlimit.o
Cc clients.o
Cc completion.o
Cc platform.o
Cc ratecontrol.o
Cc choking.o
Library libtransmission.a
ar: creating libtransmission.a
* Building Transmission CLI client
Checking dependencies...
Cc transmissioncli.o
Link transmissioncli

```

---

### Post by taurus on 2006-07-02
First, you need to install the developing package for GTK if you want to build something from source that requires GTK!  Use synaptic and search for it.  Then.
```

./configure
make
sudo make install

```
Chances are it will be installed in /usr/local/bin so look in there first...

---

### Post by zachws on 2006-07-02
[QUOTE=taurus]First, you need to install the developing package for GTK if you want to build something from source that requires GTK!  Use synaptic and search for it.  Then.
```

./configure
make
sudo make install

```
Chances are it will be installed in /usr/local/bin so look in there first...[/QUOTE]

Thanks a lot! it was where you said it would be. I built it again according to your guide after I got the GTK libs (there are a lot, i went for what looked important). It installed, now I just have to get it to my internet menu. 

It looks a LOT different under linux than OS X.

---

### Post by taelatus on 2006-11-06
When I try to install the gtk dev libraries, I get the following message:

```
chris@cminetti:~/Transmission-0.6.1$ ag libgtk2.0-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.8.17-1ubuntu5) but 2.8.20-0ubuntu1 is to be installed
                 Depends: libglib2.0-dev (>= 2.8.5) but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.6.1-2) but it is not going to be installed
E: Broken packages
```

I have libgtk2.0-0 already.

---

