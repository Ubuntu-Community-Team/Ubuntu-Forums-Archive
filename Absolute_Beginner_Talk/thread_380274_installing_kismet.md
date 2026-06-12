---
title: "installing kismet"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by dhaulk on 2007-03-09
Can somone give me a walkthrough for installing kismet on ubuntu 6.10? I have a dwl-g520 airplus extreme wifi card. I tried to do it once and it seemed like it was going well until I got to make. Here is what I did.

# sudo aptitude install build-essential
# wget [http://www.kismetwireless.net/code/kismet-2007-01-](http://www.kismetwireless.net/code/kismet-2007-01-)
R1b.tar.gz
# tar –zxvf kismet-2007-01-R1b.tar.gz
# cd kismet-2007-01-R1b

all the above was fine no errors
then I put in this
# ./configure
and got this

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... yes
checking how to run the C preprocessor... gcc -E
checking for platform-specific compiler flags... none needed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking whether byte ordering is bigendian... no
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking for unistd.h... (cached) yes
checking for sys/types.h... (cached) yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for an ANSI C-conforming const... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for ANSI C header files... (cached) yes
checking return type of signal handlers... void
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for gettimeofday... yes
checking for memset... yes
checking for select... yes
checking for socket... yes
checking for strcasecmp... yes
checking for strftime... yes
checking for strstr... yes
checking for system-level getopt_long()... yes
checking for stdint.h... (cached) yes
checking for accept() addrlen type... socklen_t
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for main in -luClibc++... no
checking for main in -lstdc++... yes
checking for group 'root'... yes
checking for group 'man'... checking for initscr in -lncurses... no
configure: WARNING: Unable to find libncurses
checking for initscr in -lcurses... no
configure: error: Unable to find libncurses or libcurses

I think the line above is where theres a problem but I don't know where to get the libncurses or libcurses
when I try make i get

make: *** No targets specified and no makefile found.  Stop.

---

### Post by x64Jimbo on 2007-03-09
Did you try adding them with synaptic? curses is required for programs that display semi-graphical output in a command line window. Kismet is similar to nano, vi, lynx, etc in this way.

---

### Post by dhaulk on 2007-03-09
Ok never mind I got it now I found them and then it asked for another program that had to have another program to compile it and a 3rd program to make the second program work. ARRRGGGHHH what a nightmare I have a headache this big and it has kismet written all over it. LOL

---

### Post by x64Jimbo on 2007-03-11
Wait, why did you have to compile anything? You can get all the components for Kismet through Synaptic.

---

### Post by ratmtattat on 2007-04-16
[QUOTE=x64Jimbo;2284218]Wait, why did you have to compile anything? You can get all the components for Kismet through Synaptic.[/QUOTE}

Sorry for being dumb, but how do you do this through synaptic?  I'm not seeing exactly what all I need to have on there.  

I'm basically at the same point the original poster was when they started the thread. 

Any help will be appreciated.

---

### Post by x64Jimbo on 2007-04-16
First, add your universe and multiverse repositories by uncommenting them in your /etc/apt/sources.list

Then...

Open Synaptic
Search for "kismet" 
Mark it for installation
Click Apply
Then you should have it.

---

### Post by ratmtattat on 2007-04-16
I did that and actually saw what you were talking about with the multiverse and universe stuff.  I uncommented those lines (took away the # and the space in front of the urls), saved it, and reran synaptic.  Unfortunately, Kismet did not show up in the list.  I'm not sure what I could be doing wrong, but I was able to install Kismet (albeit an older version) with the command:

sudo apt-get install kismet

It seems to be working ok for me now.

---

### Post by x64Jimbo on 2007-04-18
You sometimes have to settle for an older version to get support under the repositories. They're not always right on top of the CVS or SVN versions of software, but it's nice to know that it always installs cleanly and without any dependency hell. I stick with repo installation whenever possible, even if it means sticking with an older version of a package.

---

### Post by dudestir on 2007-07-27
Hi All

I've only been using Linux since Feisty came out so sorry if this is something that is obvious.

I've installed Kismet through Synaptic.  Once done I don't see it on a menu anywhere.

When I try running it through a terminal window I get

Unable to set up pidfile /var/run//kismet_server.pid, couldn't open for writing: Permission denied[1] + Done(1)                    ${BIN}/kismet_server 

kismet_server.pid doesn't exist in that location so I assume there is a config somewhere that needs tweaking.

Running as root I get

FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.

The man file /usr/share/doc/kismet/README.gz says I should look for the config files in /usr/local/etc/ but they're not there.  Nothing else int here seems to offer a solution that jumps out to me.
 

Where should I be looking.

Dean Crawford

---

### Post by Delirious on 2007-08-08
> **dudestir said:**
> Hi All

I've only been using Linux since Feisty came out so sorry if this is something that is obvious.

I've installed Kismet through Synaptic.  Once done I don't see it on a menu anywhere.

When I try running it through a terminal window I get

Unable to set up pidfile /var/run//kismet_server.pid, couldn't open for writing: Permission denied[1] + Done(1)                    ${BIN}/kismet_server 

kismet_server.pid doesn't exist in that location so I assume there is a config somewhere that needs tweaking.

Running as root I get

FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.

The man file /usr/share/doc/kismet/README.gz says I should look for the config files in /usr/local/etc/ but they're not there.  Nothing else int here seems to offer a solution that jumps out to me.
 

Where should I be looking.

Dean Crawford

I have the same problem, anyone how to fix it? Or what are we doing wrong?

---

### Post by Delirious on 2007-08-08
> **dudestir said:**
> Hi All

I've only been using Linux since Feisty came out so sorry if this is something that is obvious.

I've installed Kismet through Synaptic.  Once done I don't see it on a menu anywhere.

When I try running it through a terminal window I get

Unable to set up pidfile /var/run//kismet_server.pid, couldn't open for writing: Permission denied[1] + Done(1)                    ${BIN}/kismet_server 

kismet_server.pid doesn't exist in that location so I assume there is a config somewhere that needs tweaking.

Running as root I get

FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.

The man file /usr/share/doc/kismet/README.gz says I should look for the config files in /usr/local/etc/ but they're not there.  Nothing else int here seems to offer a solution that jumps out to me.
 

Where should I be looking.

Dean Crawford

I have the same problem, anyone know how to fix it? Or what are we doing wrong?

---

### Post by x64Jimbo on 2007-08-10
You have to configure the kismet.conf file to use your interface. Check the kismet forums and readmes for more info on how to do this.

---

### Post by Alfred_McGee on 2007-09-30
Rather than using the apt-get command to install Kismet, I tried to compile it with Wireshark so as to be able to have Kismet's dump files used by Wireshark. After navigating to my unpacked Kismet folder, I used this command: 

./configure --with-wireshark=../wireshark-0.99.6

The error I get every time seems similar to the one encountered by many other wannabe Kismet users, however, regardless of how they try to install Kismet:
checking for gettimeofday... yes
checking for memset... yes
checking for select... yes
checking for socket... yes
checking for strcasecmp... yes
checking for strftime... yes
checking for strstr... yes
checking for system-level getopt_long()... yes
checking for stdint.h... (cached) yes
checking for accept() addrlen type... socklen_t
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for main in -luClibc++... no
checking for main in -lstdc++... yes
checking for group 'root'... yes
checking for group 'man'... checking for initscr in -lncurses... no
configure: WARNING: Unable to find libncurses
checking for initscr in -lcurses... no
configure: error: Unable to find libncurses or libcurses

I tried installing build essential files, and that command seems to have worked, but it didn't change what happens every time I try to install Kismet. How do you install libncurses and libcurses?

---

### Post by Alfred_McGee on 2007-09-30
Oops! Never mind! problem solved by Hans4958:

sudo apt-get install libncurses5-dev

---

### Post by tr1px on 2008-06-05
sudo apt-get install kismet

this installs the program with all the dependencies including wireshark.

the kismet.conf file is located in /etc/kismet/

cd /etc/kismet
ls

this will show you what is in there. to configure it do:

sudo gedit /etc/kismet/kismet.conf

there is no point to install it from source.

also for the n00bs who need help configuring kismet check out this link...

[http://securityforest.com/wiki/index.php/Kismet_-_How_to_Install_and_configure](http://securityforest.com/wiki/index.php/Kismet_-_How_to_Install_and_configure)

hope that helps

---

