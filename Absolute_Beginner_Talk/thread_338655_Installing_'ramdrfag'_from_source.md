---
title: "Installing 'ramdrfag' from source"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by andrew222 on 2007-01-14
Hello,

I downloaded a multi-platform ram-defrag utility from sourceforge called 'ramdefrag'

//here's the link to the download
[http://sourceforge.net/projects/ramdefrag/](http://sourceforge.net/projects/ramdefrag/)

I changed the directory to the folder with the code as per instructions, then typed './configure' 
and then typed 'make' also per instructions.  I got a message telling me no makefile was found

........Here are the last lines from the ./configure command



>>
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.0.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the PACKAGE_CFLAGS and PACKAGE_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
andrew@Ubuntu-one:~/Desktop/ramdefrag$ make
make: *** No targets specified and no makefile found.  Stop.
andrew@Ubuntu-one:~/Desktop/ramdefrag$ 
>>>>>>>>>>>>>


Apparently this line from the above says there is a problem with gtk+-2.0,  I checked in the Synaptic package manager and gtk+-2.0 is installed
..............................................................
configure: error: Package requirements (gtk+-2.0 >= 2.0.0) were not met.



Also this message points to changing some environment variables
.........................................................
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the PACKAGE_CFLAGS and PACKAGE_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.




Is there a solution to  fixing these issues ?

Andrew

---

### Post by andrew222 on 2007-01-14
OK,  I did not mention which of the files I downloaded,  I downloaded:   ramdefrag-0.4.0-1.src.rpm

I did try to install this one:  ramdefrag_0.4.0_i386_debiantesting.deb    and that did work out well, but I would like to install this application from the source.

I do hope in the next step I can access and run the source from the SVN....

Yes, I am new to sourceforge and the SVN and that is partly why I am here...

Thanks again,

Andrew

---

### Post by rabid9797 on 2007-01-14
why install the source when you have a perfectly good deb install file?:-k 

anyway, you can convert the rpm to deb with alien.

```

sudo apt-get install alien
sudo alien [file] -d -i

```

---

### Post by andrew222 on 2007-01-14
Thank you for the alien commands rabid9797.

I wanted to install from the source because I hope to start working on it from SVN as well...

---

### Post by rabid9797 on 2007-01-14
no problem, hope it works for you

---

