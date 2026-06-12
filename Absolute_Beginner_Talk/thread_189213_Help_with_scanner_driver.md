---
title: "Help with scanner driver"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by Matt0001 on 2006-06-04
After a succesful Ubuntu install on my laptop, I've moved onto my old desktop. I have an old parallel port Artec scanner--Artec AS6E. I found a linux driver for the scanner on scource forge, but I think I might be in over my head with installing it.

Here are the install directions provided with the driver. I tried running the ./configure and it did not seem to work correctly. Is there something unique to Ubuntu that I need to do? Thank you for your help.

"To install the AS6E driver do the following:
 type:

./configure
make
make install  (as root)

Edit the file /etc/as6e.conf if you are not using parport0.  You can get
information about your parallel ports by typing "dmesg" at the command line.
If you have a conventional 2.2.X, 2.4.X or 2.6.x kernel which stores parallel port information
in the /proc directory, uncomment the appropriate port (parportX).  If not, uncomment
the numerical port address assigned to the port.  This can be read from
"dmesg" as above.


By default it installs into the /usr/local/bin directory.  If you want it to
install in a different directory, configure it with the --prefix= option (eg.
./configure --prefix=/usr will install it in the /usr/bin directory).  Make
sure it is installed in a directory in your path if you want it to work
with SANE.  It will set the suid root flag so the driver can be used without
being root, so if you are installing this on a server, check the permissions
carefully.

To make it work with SANE you will have to do the following:

1.  Read the SANE instructions, compile and install as directed.

2.  Download and install the xsane frontend package. (recommended, but not required)

3.  Link the xsane binary to your GIMP plugins directory.

4.  Make sure the file /etc/sane.d/dll.conf contains a line that reads "as6e",
and that it is not commented out."

---

### Post by Peter76 on 2006-06-05
Hi, I didi some searching around, and came up with this:
I expect you did a standard Ubuntu install ( Dapper; latest release ), so the sane package ( = scanning gui ) is already installed. This already contains part of the files needed to setup your scanner. Go to a terminal and type:

```
man sane-as6e
```

Get the as6edriver thing from here:

[http://prdownloads.sourceforge.net/as6edriver/as6edriver-0.5.tar.gz?download](http://prdownloads.sourceforge.net/as6edriver/as6edriver-0.5.tar.gz?download)

But you probably already have that.

Now you need to install the packages to build it:
Go to Synaptic and install the following:

- build-essential
- checkinstall

Unpack the driver package, open a terminal and go to the directory where the package is unpacked.

Once there, type: ./configure

If that finishes without errors, type: make

Once that is finished, type: sudo checkinstall

You'll probably run into some errors here about missing packages; post the output and I'll help you out.

If everything goes ok, theoretically you should be able to scan now, but we'll see.

Good luck

Peter

---

### Post by richbarna on 2006-06-05
Hi matt001,
Firstly, before trying to build/make/install, you should download build-essential.(this will install all the necessary tools for command line installs)
Open your terminal/console and type :-
> sudo apt-get update
then :-
> sudo apt-get install build-essential

Once this is done, go to the folder that contains the "./configure" file.
Right click on your mouse and click open terminal here.
Now type ./configure
That should work, then do the "make" command followed by "make install".

Any problems, post back :)

Edit: Peter76, you got there while I was typing ;)

---

### Post by Matt0001 on 2006-06-05
Thank you both. I've got the driver installed and the scanner is working beautifully-- faster than it did in XP.

---

