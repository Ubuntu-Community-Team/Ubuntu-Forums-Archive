---
title: "Stuck at the first try"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by Jeroen V on 2006-04-28
Hi there, I'm new at these forums.
I bought a laptop, a dell inspiron 6400, and I would like to run Ubuntu on it.
I downloaded the Dapper CD, and installed it via the nice new Express installer.

After that I want to install 915resolution and ipw3945, needed for WLAN and VGA.
I downloaded these packages and burned them on a cd, copied them on my home folder of my laptop, and then started the problems:

Starting with ipw3945 (my wlan-driver) because I want to get internet working.
I got the packaged un-tarred, and in my home dir, now I need to "make" it, but when I follow the instructions in the INSTALL, the command "make" seems not "installed" in the default Dapper install. I can't get it via Synaptic because I'm not on internet yet.

So I downloaded "make 3.81" (via my other computer)  and when I try to install "make" it seems that "GCC" is needed, and isn't installed by default.

So I downloaded "GCC" but it seems that to install GCC you need Make :-# 

I find it very weird that it says that make isn't installed, because it should be in the Dapper beta install.

I hope you guys can help me installing GCC and/or Make, so that I finally can install my drivers! Thanks in advance!

---

### Post by OffHand on 2006-04-28
I think you need build-essential if you want to compile stuff.
Can anyone confirm this?

---

### Post by Jeroen V on 2006-04-28
OK, just downloaded build-essential (via other computer), and when I try to open it (from my home folder) with the default "Package Installer", the status is:
[COLOR="Red"]Error: Dependency is not satisfiable: libc6-dev|libc-dev[/COLOR].. so I can't install build-essential neither...

---

### Post by mentallysilent on 2006-04-28
yes you need build-essential...it includes cc/gcc etc and certainly make. This is one of the weird things about Ubuntu, it does not come with compilers included...also don't count on building kernel moduels since the kernel source is not there....unless of course you compile and install the kernel yourself...

---

### Post by Sef on 2006-04-28
To compile, you need build-essential, as was stated in the post above.

Open the Terminal (Applications > Accessories > Terminal)

then type 

sudo apt-get update

Next type

sudo apt-get install build-essential

---

### Post by gingermark on 2006-04-28
Ok, right now you don't have a net connection on your Ubuntu box - which is fine.

Many packages depend on others, this is why you get your error.

[http://packages.ubuntu.com/dapper/devel/build-essential](http://packages.ubuntu.com/dapper/devel/build-essential) shows you what build-essential depends on. So you need to grab those packages too. And if any of them depend on something else, you'll have to get them too. (but keep in mind you will have many of the packages that they depend on already)

Once you're net connection works this will become far easier - the process is automated.

I guess this sort of thing is why these packages should really be included by default...

EDIT: I was bored.

You'll need to download the following:

build-essential
dpkg-dev
g++
gcc
libc6-dev
make

Download the .debs and put them in the same folder (say /home/yourusername/debs)
Then do
```
cd debs/
sudo dpkg -i *.deb
```

And hope. If that doesn't work, you'll have to chase up more of the dependencies.

I know this seems like a lot of effort - but when you have your net connection working the installation of such packages really is a breeze.

---

