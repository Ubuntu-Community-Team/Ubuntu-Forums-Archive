---
title: "ndiswrapper install, please accept my apologies :)"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by benfinkel on 2006-04-06
Hi all,

Total Linux nub here.  I know there are posts all over this forum about getting ndiswrapper installed for a wireless card but...

None of them seem to addres my issue :P

So here goes:

I just installed Ubuntu 5.10 from the main site.  

I downloaded the latest release from ndiswrapper.sourceforge.net  it's ndiswrapper-1.12.tar.gz

After that, I found out I needed to get Make from Synaptic, which I did.

After that, I found out I needed the kernel headers from Synaptic, so I got those too!

After that, I've tried to 'make install' in my ndiswrapper directory, but this is the response I get:

ben@ben-hp:~/ndiswrapper-1.12$ sudo make install
Password:
make -C driver install
make[1]: Entering directory `/home/ben/ndiswrapper-1.12/driver'
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/ben/ndiswrapper-1.12/driver \
        DRIVER_VERSION=1.12
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[2]: gcc-3.4: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  LD      /home/ben/ndiswrapper-1.12/driver/built-in.o
  CC [M]  /home/ben/ndiswrapper-1.12/driver/hal.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/home/ben/ndiswrapper-1.12/driver/hal.o] Error 127
make[2]: *** [_module_/home/ben/ndiswrapper-1.12/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/ben/ndiswrapper-1.12/driver'
make: *** [install] Error 2
ben@ben-hp:~/ndiswrapper-1.12$


So, it looks to me like I need GCC 3.4, which is not installed with Ubuntu?

I'm d/ling GCC 3.4.6 from GCC right now, but, I want to make sure I'm not missing something stupid.

Thanks all!!

---

### Post by taurus on 2006-04-06
To build or install something from source, you need build-essential so open a terminal, Applications -> Accessories -> Terminal and type it at the prompt,
```

sudo apt-get install build-essential

```
Now, try to build your ndiswrapper again...

---

### Post by Mustard on 2006-04-06
I think you need to do this in terminal to get the system to use 3.4 instead of the default compiler gcc-4.0 (after you install 3.4)..

```
export CC="gcc-3.4"
```

If I recall the command correctly.  Some searches of the forum or via [http://www.google.com/linux](http://www.google.com/linux) should turn up some examples of how the command is used.

---

### Post by lupine_nickt on 2006-04-06
Ubuntu 5.10's kernel is compiled with gcc-3.4, so you need to use that to compile any kernel modules (drivers).

IIRC, gcc-3.4 is in the repositories, just in the Universe repository. So if you enable that (if you're using Synaptic, it's Settings->Repositories, then enable the Restricted and Universe repos). 

Just install it, then try to compile it again. If it still fails, then you need to order it to use the right compiler... I used the rather unwieldy method of renaming /usr/bin/gcc to /usr/bin/gcc-4.0 and then renaming /usr/bin/gcc-3.4 to /usr/bin/gcc (well, Isymlink it); then once finished, move everything back to how it was.

Usually, it does pick it up automatically though.

HTH...

xF,

...Nick

---

### Post by _linux_ on 2006-04-06
You don't need all that. Ubuntu already has ndiswrapper. Go to this wiki page to figure out how to configure it:
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

---

### Post by benfinkel on 2006-04-06
Hey Guys!

Thanks for all of the direction.

I did end up d/ling 3.4 through the universe list in Synaptic.  Learned one thing there! :)


Then I read that ndiswrapper was already installed.  I got the utils and gtk front-end from Synaptic, but I'm still not getting anywhere.

Using the front end I try to add the driver but nothing comes up on screen.  When I try the command line option:

sudo ndiswrapper /xxx/yyy/Driver/BCMWL5.INF

I get:

sudo: ndiswrapper: command not found

So, is ndiswrapper installed or not?? 

Thanks again all!

-Ben

---

### Post by taurus on 2006-04-06
You can find it with this command from a terminal
```

sudo find / -name ndiswrapper -print

```
And by the way, the command to install a driver with ndiswrapper is
```

sudo ndiswrapper -i /path_to_where_it_is/BCMWL5.inf

```

p.s.  This is Linux, not Windows so lower letters are not the same as upper letters, case sensitive!!!

---

### Post by benfinkel on 2006-04-06
Ahh, thank you.

I just forgot to type the -i when I was typing my example.

And I'm proud to let you (and everyone else) know that I already knew *nix was case-sensitive :)

Yayy me!

-Ben

---

### Post by benfinkel on 2006-04-06
Hmm, still no luck.](*,) 

The find returned the following:
/etc/ndiswrapper
/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper
/usr/src/linux-headers-2.6.12-9-386/include/config/ndiswrapper
/usr/src/linux-headers-2.6.12-9/drivers/net/ndiswrapper
/home/ben/ndiswrapper-1.12/utils/ndiswrapper

but, if I try to run ndiswrapper from any of those locations I still get 'command not found'.

Also, in my /etc/ndiswrapper directory is a folder (in blue?) named bcmwl5a with all of my files in it.  It still doesn't show in my ndis gtk program.

What now?

---

### Post by taurus on 2006-04-06
What does it say when you type this command from a terminal then?
```

sudo apt-get install ndiswrapper

```

---

### Post by benfinkel on 2006-04-06
[QUOTE=taurus]What does it say when you type this command from a terminal then?
```

sudo apt-get install ndiswrapper

```[/QUOTE]


Hmm, interesting.  I get this:

```

Reading package lists... Done
Building dependency tree... Done
Segmentation fault

```

---

### Post by benfinkel on 2006-04-06
So I rebooted (I thought you never had to do that with Linux ;))

and I tried again and got this:

```

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ndiswrapper

```

---

### Post by jonj on 2006-07-07
it will be 
```
sudo apt-get install ndiswrapper-utils
```

---
[http://know.homelinux.com/](http://know.homelinux.com/)

---

