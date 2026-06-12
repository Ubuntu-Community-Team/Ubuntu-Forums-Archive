---
title: "Need Help with Configure"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Darko Beta on 2007-01-24
I'm following the gnucash wiki to set up direct connect, but I need help with the first step.  It says:

*GnuCash must be configured using --enable-hbci and --enable-ofx in order for OFXDirectConnect to be available.*

What does that mean?  How do I configure the program?

---

### Post by bodhi.zazen on 2007-01-24
First gnucash is in the repositories, in Universe:

[http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

Second, to install you need build-essential :

```
sudo aptitude install build-essential checkinstall
./configure --enable-hbci --enable-ofx
make
sudo checkinstall
```

---

### Post by ComplexNumber on 2007-01-24
i assume you have the source code. the source codes comes in a package that usually ends in something like "tar.gz" or "tar.bzip2". place that somewhere in your home directory, then right click and select 'extract here'. that will then extract into its own directory. now fire up the terminal (you'll find it in main menu -> accessories) and go into that directory. right, now that you're there......

to compile source code, one usually types something like this on the commandine:
./configure --prefix=/usr

that means that its going to be configured so that it ends up being installed in the /usr directory. the binary that you execute will be installed in /usr/bin, various libraries may be stored in /usr/lib, and things like documentation and icons etc are installed in /usr/share. it tend to be good practice to set the prefix as being /usr/local instead just in case in may conflict with anything in /usr, but thats rare when it happens. 
now getting to onto making sense of your second sentence in your post. if you type "./configure --help", this will give you some options. as well as "--prefix= path", there will also be the option for "--enable-ofx[I]".

[/I]to cut a long story short, i suggest that you type in the following:

**./configure ****--enable-hbci **[B]--enable-ofx
[/B]
after that, type in:[B]

make

[/B]
when thats finished (hopefuly without producing any errors), type in:[B]

sudo make install
[/B]

---

### Post by Darko Beta on 2007-01-24
I installed build-essential, and with the configure line I'm getting this error:

bash: ./configure: No such file or directory

---

### Post by ComplexNumber on 2007-01-24
> **Darko Beta said:**
> I installed build-essential, and with the configure line I'm getting this error:

bash: ./configure: No such file or directory
i'm just downloading the source for gnucash now so that i can help you. in the meantime, what location are you typing in the configure command in the terminal? do you do as i suggest and go to where you unzipped the source? use the command "cd". for example, if you unzipped the source into /home/<your-username>/gnucash, the type "cd /home/<your-username>/gnucash" on the commandline.

---

### Post by Darko Beta on 2007-01-24
Ooops.  Following directions forthwith.

---

### Post by Darko Beta on 2007-01-24
OK thanks!  I'm taking a look right now.

---

### Post by Darko Beta on 2007-01-24
The gnucash files are all in /usr/bin.  Should I try the ./configure on that directory like:

./configure /usr/bin/gnucash

or

cd /usr/bin/gnucash

---

### Post by ComplexNumber on 2007-01-24
i've just editied the last line in post 3. that used to read "make install", but it should read "**sudo** make install"


> **Darko Beta said:**
> The gnucash files are all in /usr/bin.  Should I try the ./configure on that directory like:

./configure /usr/bin/gnucash

or

cd /usr/bin/gnucash
what do you mean they're all in  /usr/bin/gnuccash?? extract the source files into your home directory BEFORE you type in ./configure.....

---

### Post by Darko Beta on 2007-01-24
Maybe I should have been more clear: I have already installed gnucash--and I am now trying to enable ofx direct connect.  Do I need to uninstall and start over to configure?

---

### Post by ComplexNumber on 2007-01-24
> **Darko Beta said:**
> Maybe I should have been more clear: I have already installed gnucash--and I am now trying to enable ofx direct connect.  Do I need to uninstall and start over to configure?
when you did the configure command, did you type the following?
**./configure ****--enable-hbci **[B]--enable-ofx --prefix=/usr

[/B]
otherwise, what did you type?

---

### Post by Darko Beta on 2007-01-24
I have tried several different commands... and they all end up telling me:

bash: ./configure: No such file or directory

Including the one you noted above...  The commands in bold are **exactly** what I should type, correct?

---

### Post by ComplexNumber on 2007-01-24
> The commands in bold are **exactly** what I should type, correct?
yes.



there is DEFINITELY a configure file in there because the screenshot shows what the contents of the unzipped source is. the configure file that is circled in red is what you are running when you type in "./configure....."




btw what is the EXACT name of the gnucash file that you are trying to install? i'm wondering if you have downloaded a binary file instead rather than a source file. the one that i've recently downloaded is called **gnucash-2.0.4.tar.bz2**.

---

### Post by Darko Beta on 2007-01-24
I must have installed with synaptic or automatix.  and the files are mixed in with a million other files in /usr/bin.  I think I'll uninstall and download the tarball you referenced a bit later in the evening.  Thanks very much for your help this far, it is helping me learn.  I appreciate it.

---

### Post by ComplexNumber on 2007-01-24
d'oh!! i should have asked that to begin with :mrgreen:. its no wonder why we seem to have crossed-wires.

well, i'm really not to sure if those 2 features(ie -enable-hbci --enable-ofx) are enabled or not when you install it via synaptic.
i think what you should do now is to try out the installed gnucash to see if it has those features. if not, download the gnucash source from [here]("http://sourceforge.net/project/downloading.php?group_id=192&use_mirror=switch&filename=gnucash-2.0.4.tar.bz2&95265534"), then follow my steps above. since post 3, i've been assuming that you were compiling from source. i didn't realise that you already installed it via synaptic.

---

### Post by Darko Beta on 2007-01-25
OK, I'm back at it.  I uninstalled the automatix version of gnucash (now I see why automatix can be a pain sometimes), and downloaded and extracted the version from sourceforge.  I cd'ed to the gnucash folder and entered:

./configure --enable-hbci --enable-ofx

Everything cruises along until there is an error:

```
checking ltdl.h usability... no
checking ltdl.h presence... no
checking for ltdl.h... no
configure: error: Cannot find ltdl.h -- libtool-devel (or libtool-ltdl-devel) not installed?
```

I checked in synaptic and i don't see a libtool-devel, only a libtool which I did install but I still get the same error.

Any advice?

---

### Post by jackrobinson on 2007-01-26
> **Darko Beta said:**
> I uninstalled the automatix version of gnucash (now I see why automatix can be a pain sometimes), and downloaded and extracted the version from sourceforge.  I cd'ed to the gnucash folder and entered:

./configure --enable-hbci --enable-ofx

Everything cruises along until there is an error:

```
checking ltdl.h usability... no
checking ltdl.h presence... no
checking for ltdl.h... no
configure: error: Cannot find ltdl.h -- libtool-devel (or libtool-ltdl-devel) not installed?
```

I checked in synaptic and i don't see a libtool-devel, only a libtool which I did install but I still get the same error.

Any advice?
no you still do not see it. Be it apt, synaptic or automatix, its always advisable to uninstall precompiled (official) binary packages before attempting to install a self-compiled higher version. 
try the following:
```
sudo apt-get install libltdl3-dev
```
and try to run configure again.

---

### Post by Darko Beta on 2007-01-26
JR - Thanks, I'll try this when I get home.

---

### Post by ComplexNumber on 2007-01-26
install libtool as well because i think it helps with the configure process. its not a dependency as such. i suspect it will be installed anyway....but just in case.

---

### Post by lamego on 2007-01-26
> install libtool as well because i think it helps with the configure process. its not a dependency as such. i suspect it will be installed anyway....but just in case.
When needed it will complain about it ;)

---

### Post by rparker on 2007-01-28
I would appreciate any thoughts on how to resolve the following error message. I complied Gnucash 2.0.4 with --enable-hbci --enable-ofx. All went fine and the program loads properly. When I go to Tools > HBCI Setup > Start AqHBCI Wizard the following error is reported:

X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
4:2007/01/28 10-02-24:(null)(22652):qt3_wizard.cpp:   47: Internationalisation is not available for your language
6:2007/01/28 10-02-24:(null)(22652):qbanking.cpp:  863: Internationalisation is not available for your language en_US.UTF-8
6:2007/01/28 10-02-24:(null)(22652):qbanking.cpp:  911: Registering cfg module plugin manager
on_aqhbci_button: Oops, aqhbci wizard return nonzero value: -8. The called program was "/usr/lib/aqbanking/plugins/16/wizards/qt3-wizard".

Thank you for any suggestions

---

### Post by theProf on 2007-02-23
I'm getting the same error and it's driving me nuts.  I tried to take it a step further and run qt3-wizard directly, and I got the following.

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
4:2007/02/23 10-01-25:(null)(6188):qt3_wizard.cpp:   47: Internationalisation is not available for your language
6:2007/02/23 10-01-25:(null)(6188):qbanking.cpp:  863: Internationalisation is not available for your language en_US.UTF-8
6:2007/02/23 10-01-25:(null)(6188):qbanking.cpp:  911: Registering cfg module plugin manager
Segmentation fault

If anyone has an idea about how to get this working, I would really appreciate it.  Enabling direct connection to my banks through gnucash will lessen my dependency on windows by 1 more "thing".  Only 2 others to go :)

---

### Post by rparker on 2007-02-23
I finally did get 2.0.4 configured only to find I had problems with banks and credit cards when configuring ofx direct.

Some dependencies I did not see in my original build was libgwenhyfar38, libgwenhyfar38-dev and libgwenhyfar-data.

I also followed more of the directions from the following site:

[http://www.ubuntuforums.org/showthread.php?t=345764&highlight=gnucash](http://www.ubuntuforums.org/showthread.php?t=345764&highlight=gnucash)

rather than the wiki:

[http://wiki.gnucash.org/wiki/Debian](http://wiki.gnucash.org/wiki/Debian)

---

