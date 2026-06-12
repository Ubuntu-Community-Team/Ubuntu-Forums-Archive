---
title: "Help please! I am trying to install a game."
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by ssynesthesia on 2007-02-26
Hello I am trying to install a game called clanbomber. I cant find where to download this "Makeinfo" that is missing. I found everything else but where do I go for it?


synesthesia@Workflow:/usr/local/src/clanbomber2-0.9$ ./configure
loading cache ./config.cache
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking for c++... (cached) c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... (cached) yes
checking whether c++ accepts -g... (cached) yes
checking whether byte ordering is bigendian... (cached) no
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for DirectFB... found
checking for FusionSound... found
creating ./config.status
creating Makefile
creating clanbomber/Makefile
creating clanbomber/maps/Makefile
creating clanbomber/pics/Makefile
creating clanbomber/wavs/Makefile
creating debian/Makefile
creating debian/changelog
creating config.h
config.h is unchanged

---

### Post by Maestro23 on 2007-02-26
Do you have "build-essential" installed for compiling from source?

If not:

> sudo aptitude install build-essential

You might need to take care of other dependencies also.

*Take a look at the bottom of this link on "Installing from source".  Might help you as well.
[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

---

### Post by ssynesthesia on 2007-02-26
Yes I do.

I just figured it out! I used 

 sudo apt-get install texinfo

---

### Post by ssynesthesia on 2007-02-26
synesthesia@Workflow:/usr/local/src/clanbomber2-0.9$ ./configure
loading cache ./config.cache
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... found
checking for c++... (cached) c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... (cached) yes
checking whether c++ accepts -g... (cached) yes
checking whether byte ordering is bigendian... (cached) no
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for DirectFB... found
checking for FusionSound... found
creating ./config.status
creating Makefile
creating clanbomber/Makefile
creating clanbomber/maps/Makefile
creating clanbomber/pics/Makefile
creating clanbomber/wavs/Makefile
creating debian/Makefile
creating debian/changelog
creating config.h
config.h is unchanged

Does that look ok?

---

### Post by Maestro23 on 2007-02-26
A new person to Ubunut/linux should not be installing anything from source, until they are more familiar with commands and file structure.  You can really hose up your system if you don't know what you are doing. FYI: There is a README and INSTALL doc in the extracted directory that contains helpful info.

The game you are trying to install is already in the Ubuntu Repositories.  You can get it by:

> sudo aptitude install clanbomber

Good luck.

---

### Post by ssynesthesia on 2007-02-26
I tried to "make" but there seems to be some problems.. I can copy and paste it if the problems arnt evident in the last post I made.. It aparently wasnt "ok" haha

---

### Post by ssynesthesia on 2007-02-26
> **Maestro23 said:**
> A new person to Ubunut/linux should not be installing anything from source, until they are more familiar with commands and file structure.  You can really hose up your system if you don't know what you are doing. FYI: There is a README and INSTALL doc in the extracted directory that contains helpful info.


I have been going off of the readme and have got this problem from doing what it is telling me to do.

The version in the repositories is a old version. I was trying to install 2-0.9.

Would anyone be able to help me with the configureing?

---

### Post by ssynesthesia on 2007-02-26
If I shouldnt be installing from source.. Is there another way to install clanbomber 2-0.9? I am open for suggestions and would love to get this game going.

---

### Post by slayerboy on 2007-02-26
Like Maestro23 said, if you're new to Linux, you definitely don't want to be installing programs from source right now.  Your best bet is to do this:

When wanting to install a new program:
1.  Search in Synaptic ***first***! Try all or part of the name with the option of "Description and Name" selected in the search box.
2.  Search on the Ubuntu forums for that program, it is quite possible you are not alone in looking for that game and there might be a better way to install it.
3.  If after searching Synaptic and the Ubuntu forums you still have not found an answer, try posting a request in the forum for a possible solution other than compiling from source (an alternative, etc).
4.  If none of these options are fruitful, then either wait for the program to possibly end up in Synaptic or backup your important files and seek help with compiling from source.  ***THIS IS THE LAST RESORT! ***You should rarely ever have to reach this step!

---

### Post by slayerboy on 2007-02-26
> **ssynesthesia said:**
> If I shouldnt be installing from source.. Is there another way to install clanbomber 2-0.9? I am open for suggestions and would love to get this game going.
What is the difference between the versions?  chances are that it will be updated soon enough.

---

### Post by ssynesthesia on 2007-02-26
> **slayerboy said:**
> Like Maestro23 said, if you're new to Linux, you definitely don't want to be installing programs from source right now.  Your best bet is to do this:

When wanting to install a new program:
1.  Search in Synaptic ***first***! Try all or part of the name with the option of "Description and Name" selected in the search box.
2.  Search on the Ubuntu forums for that program, it is quite possible you are not alone in looking for that game and there might be a better way to install it.
3.  If after searching Synaptic and the Ubuntu forums you still have not found an answer, try posting a request in the forum for a possible solution other than compiling from source (an alternative, etc).
4.  If none of these options are fruitful, then either wait for the program to possibly end up in Synaptic or backup your important files and seek help with compiling from source.  ***THIS IS THE LAST RESORT! ***You should rarely ever have to reach this step!

Thank you for the concern. I have searched Synaptic, I have Searched the forums and google for installing clanbomber2-0.9, thats what I was doing by asking for help compiling from source...

> **slayerboy said:**
> What is the difference between the versions?  chances are that it will be updated soon enough.

If what I am asking is beyond help, or maybe more intensive than anyone is willing to help, then that is how it goes.. But I would really like to get help with this if these arnt the cases. I am sure it is possible, but I havnt been able to get any help on this as of yet.

---

### Post by ssynesthesia on 2007-02-26
Just in case someone wants to help. This was what I got when I tried to make

synesthesia@Workflow:/usr/local/src/clanbomber2-0.9$ make
make  all-recursive
make[1]: Entering directory `/usr/local/src/clanbomber2-0.9'
Making all in clanbomber
make[2]: Entering directory `/usr/local/src/clanbomber2-0.9/clanbomber'
Making all in maps
make[3]: Entering directory `/usr/local/src/clanbomber2-0.9/clanbomber/maps'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/local/src/clanbomber2-0.9/clanbomber/maps'
Making all in pics
make[3]: Entering directory `/usr/local/src/clanbomber2-0.9/clanbomber/pics'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/local/src/clanbomber2-0.9/clanbomber/pics'
Making all in wavs
make[3]: Entering directory `/usr/local/src/clanbomber2-0.9/clanbomber/wavs'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/local/src/clanbomber2-0.9/clanbomber/wavs'
make[3]: Entering directory `/usr/local/src/clanbomber2-0.9/clanbomber'
c++ -DHAVE_CONFIG_H -I. -I. -I.. -D_REENTRANT -D_GNU_SOURCE -I/usr/include/directfb   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/fusionsound -I/usr/include/directfb   -DDATADIR=\"/usr/local/share/clanbomber2/\"   -g -O2 -c Bomb.cpp
c++ -DHAVE_CONFIG_H -I. -I. -I.. -D_REENTRANT -D_GNU_SOURCE -I/usr/include/directfb   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/fusionsound -I/usr/include/directfb   -DDATADIR=\"/usr/local/share/clanbomber2/\"   -g -O2 -c Bomber.cpp
c++ -DHAVE_CONFIG_H -I. -I. -I.. -D_REENTRANT -D_GNU_SOURCE -I/usr/include/directfb   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/fusionsound -I/usr/include/directfb   -DDATADIR=\"/usr/local/share/clanbomber2/\"   -g -O2 -c Bomber_Corpse.cpp
c++ -DHAVE_CONFIG_H -I. -I. -I.. -D_REENTRANT -D_GNU_SOURCE -I/usr/include/directfb   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/fusionsound -I/usr/include/directfb   -DDATADIR=\"/usr/local/share/clanbomber2/\"   -g -O2 -c Chat.cpp
c++ -DHAVE_CONFIG_H -I. -I. -I.. -D_REENTRANT -D_GNU_SOURCE -I/usr/include/directfb   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/fusionsound -I/usr/include/directfb   -DDATADIR=\"/usr/local/share/clanbomber2/\"   -g -O2 -c ClanBomber.cpp
c++ -DHAVE_CONFIG_H -I. -I. -I.. -D_REENTRANT -D_GNU_SOURCE -I/usr/include/directfb   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/fusionsound -I/usr/include/directfb   -DDATADIR=\"/usr/local/share/clanbomber2/\"   -g -O2 -c Client.cpp
c++ -DHAVE_CONFIG_H -I. -I. -I.. -D_REENTRANT -D_GNU_SOURCE -I/usr/include/directfb   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/fusionsound -I/usr/include/directfb   -DDATADIR=\"/usr/local/share/clanbomber2/\"   -g -O2 -c ClientSetup.cpp
c++ -DHAVE_CONFIG_H -I. -I. -I.. -D_REENTRANT -D_GNU_SOURCE -I/usr/include/directfb   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/fusionsound -I/usr/include/directfb   -DDATADIR=\"/usr/local/share/clanbomber2/\"   -g -O2 -c Config.cpp
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/fstream.tcc: In member function &#8216;virtual typename std::basic_filebuf<_CharT, _Traits>::int_type std::basic_filebuf<_CharT, _Traits>::underflow()&#8217;:
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/fstream.tcc:289: error: expected unqualified-id before &#8216;(&#8217; token
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/fstream.tcc: In member function &#8216;virtual std::streamsize std::basic_filebuf<_CharT, _Traits>::xsputn(const _CharT*, std::streamsize)&#8217;:
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/fstream.tcc:612: error: expected unqualified-id before &#8216;(&#8217; token
make[3]: *** [Config.o] Error 1
make[3]: Leaving directory `/usr/local/src/clanbomber2-0.9/clanbomber'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/local/src/clanbomber2-0.9/clanbomber'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/clanbomber2-0.9'
make: *** [all-recursive-am] Error 2

---

### Post by slayerboy on 2007-02-26
> **ssynesthesia said:**
> Thank you for the concern. I have searched Synaptic, I have Searched the forums and google for installing clanbomber2-0.9, thats what I was doing by asking for help compiling from source...



If what I am asking is beyond help, or maybe more intensive than anyone is willing to help, then that is how it goes.. But I would really like to get help with this if these arnt the cases. I am sure it is possible, but I havnt been able to get any help on this as of yet.

Ok, I did a little research for you on this, not sure if it's going to help.  This is not the official clanbomber game.  It is called "Clanbomber2" version 0.9.

The error your getting when you try to do a make might be related to fusionsound.

Try:
```
sudo apt-get install fusionsound
```
and see what happens when you do this:
```
make clean
./configure
make
```

I take NO responsibility if this hoses your system or any adverse problems result out of this.  There is very little info about clanbomber2.  The latest release for Clanbomber is 1.0.5, which is in the repos.  Clanbomber2 supposedly adds a bunch of networking stuff.

Clanbomber2 freshmeat page: [http://freshmeat.net/projects/clanbomber2/](http://freshmeat.net/projects/clanbomber2/)
Clanbomber sourceforge page: [http://sourceforge.net/project/showfiles.php?group_id=12003](http://sourceforge.net/project/showfiles.php?group_id=12003)
Clanbomber homepage: [http://clanbomber.sourceforge.net/](http://clanbomber.sourceforge.net/)

Good Luck!

---

### Post by ssynesthesia on 2007-02-26
Thanks for the help thus far!
I tried the sudo apt-get install fusionsound and it gave this error msg

synesthesia@Workflow:/usr/local/src/clanbomber2-0.9$ sudo apt-get install fusionsound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package fusionsound


I did the make clean code and tried again and got the same error msg. Thanks for those links, I hadnt seen the fresh meat page before, but alas have seen the others.

I also looked up fusionshound on synaptic and libfusionsound0 is already installed along with libfusionsound-dev


edit: I am not holding anyone responsible for what happens.. I can reinstall if worse comes to worse.. I have a backup external hard drive and havnt installed much yet

---

### Post by Maestro23 on 2007-02-26
> **ssynesthesia said:**
> Thanks for the help thus far!
I tried the sudo apt-get install fusionsound and it gave this error msg

synesthesia@Workflow:/usr/local/src/clanbomber2-0.9$ sudo apt-get install fusionsound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package fusionsound


I did the make clean code and tried again and got the same error msg. Thanks for those links, I hadnt seen the fresh meat page before, but alas have seen the others.

I also looked up fusionshound on synaptic and libfusionsound0 is already installed along with libfusionsound-dev


edit: I am not holding anyone responsible for what happens.. I can reinstall if worse comes to worse.. I have a backup external hard drive and havnt installed much yet

fusionsound is in the repositories.  Do you have all your repositories enabled?

Two ways:

CommandLine: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

GUI: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by slayerboy on 2007-02-26
do you have universe enabled in your repos?  Go into synaptic and do a search for fusionsound.  If you don't see it, run over to [http://ubuntuguide.org](http://ubuntuguide.org) for info about adding the "universe" repos and all that.

**_EDIT:_**
*....errr...or just do what Maestro23 said LOL! :)*

---

### Post by ssynesthesia on 2007-02-26
Did you guys notice when I sent the first configure that it said 

"checking for FusionSound... found"

Just curious..

Ahh I did follow the ubuntuguide to add extra repositories. I just followed the psychocats one also. I am still getting the same message when I try to search for fusion sound in the repositories. 

I DID get a weird msg at the end when I was doing the first step in the psychocats way:

Fetched 5B in 4s (1B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache

I dont know what that means but would that have something to do with not finding fusion sound in the repositories? 

One other destressing thing.. When I was trying to follow the GUI metheod I realized I didn't have this "Software Properties" option. I am using version 6.10 edgy eft and have emerald and beryl installed if that makes a difference... There is a "software sources" option though..

---

### Post by Maestro23 on 2007-02-26
> Fetched 5B in 4s (1B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache


I see this when I have Synaptic(GUI) open in one workspace at the same time as I'm trying to install something via command line using aptitude install/apt-get install.  Also see this with Add/Remove open.  Can only have one access way to packages open at once.  Did this happen to you?

---

### Post by ssynesthesia on 2007-02-27
I didnt have synaptic open or anything else that locks /var/lib/dpkg

---

### Post by Adramelech on 2007-02-27
The update manager and automatix can lock this dir, close every window and try again and you will be able to install that

---

### Post by ssynesthesia on 2007-02-27
I am getting a new error and I havnt changed ANYTHING since the new error.. but here it is:

synesthesia@Workflow:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
mv: cannot stat `/etc/apt/sources.list': No such file or directory

Why is sources.list missing??

---

### Post by Adramelech on 2007-02-27
> **ssynesthesia said:**
> I am getting a new error and I havnt changed ANYTHING since the new error.. but here it is:

synesthesia@Workflow:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
mv: cannot stat `/etc/apt/sources.list': No such file or directory

Why is sources.list missing??

Because your moved it instead of copying it, mv = move, cp= copy
restore it with
sudo cp  /etc/apt/sources.list_backup /etc/apt/sources.list

---

### Post by ssynesthesia on 2007-02-28
That is weird that it tells you to move it instead of copying it.. Why wouldnt it create a new sources.list? It seems like that is what it was going for.. But anyway I got this following error when following the next step:

synesthesia@Workflow:~$ gksudo gedit /etc/apt/sources.list
(gedit:7031): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

It then opens up sources.list.. Should I just ignore that?

---

### Post by ssynesthesia on 2007-02-28
Anyway my sources.list looks like the one in the link, and I updated it like said.

> **Maestro23 said:**
> fusionsound is in the repositories.  Do you have all your repositories enabled?

Two ways:

CommandLine: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

GUI: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Yes, my sources.list is updated and the extra repositories are enabled. I tried the same thing again and again it didnt work

synesthesia@Workflow:~$ sudo apt-get install fusionsound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package fusionsound

Why can't it find fusionsound??

---

### Post by ssynesthesia on 2007-03-01
bump... Can someone help me?

---

### Post by slayerboy on 2007-03-01
what if you open up synaptic and search for fusionsound?

---

### Post by ssynesthesia on 2007-03-01
> **ssynesthesia said:**
> Thanks for the help thus far!
I also looked up fusionshound on synaptic and libfusionsound0 is already installed along with libfusionsound-dev


Yeah I tried that as you can see..  I tried it again and got the same thing. There wasnt anything else just fusionsound with lib in the front.

---

### Post by slayerboy on 2007-03-01
> **ssynesthesia said:**
> Yeah I tried that as you can see..  I tried it again and got the same thing. There wasnt anything else just fusionsound with lib in the front.
that's what you want to install -- libfusionsound

---

### Post by ssynesthesia on 2007-03-01
As I said beforfe:

"libfusionsound0 is already installed along with libfusionsound-dev"

They are already installed. So my next question is why am I getting this error when I try to "make"?


> **ssynesthesia said:**
> Just in case someone wants to help. This was what I got when I tried to make

synesthesia@Workflow:/usr/local/src/clanbomber2-0.9$ make
make  all-recursive
make[1]: Entering directory `/usr/local/src/clanbomber2-0.9'
Making all in clanbomber
make[2]: Entering directory `/usr/local/src/clanbomber2-0.9/clanbomber'
Making all in maps
make[3]: Entering directory `/usr/local/src/clanbomber2-0.9/clanbomber/maps'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/local/src/clanbomber2-0.9/clanbomber/maps'
Making all in pics
make[3]: Entering directory `/usr/local/src/clanbomber2-0.9/clanbomber/pics'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/local/src/clanbomber2-0.9/clanbomber/pics'
Making all in wavs
make[3]: Entering directory `/usr/local/src/clanbomber2-0.9/clanbomber/wavs'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/local/src/clanbomber2-0.9/clanbomber/wavs'
make[3]: Entering directory `/usr/local/src/clanbomber2-0.9/clanbomber'
c++ -DHAVE_CONFIG_H -I. -I. -I.. -D_REENTRANT -D_GNU_SOURCE -I/usr/include/directfb   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/fusionsound -I/usr/include/directfb   -DDATADIR=\"/usr/local/share/clanbomber2/\"   -g -O2 -c Bomb.cpp
c++ -DHAVE_CONFIG_H -I. -I. -I.. -D_REENTRANT -D_GNU_SOURCE -I/usr/include/directfb   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/fusionsound -I/usr/include/directfb   -DDATADIR=\"/usr/local/share/clanbomber2/\"   -g -O2 -c Bomber.cpp
c++ -DHAVE_CONFIG_H -I. -I. -I.. -D_REENTRANT -D_GNU_SOURCE -I/usr/include/directfb   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/fusionsound -I/usr/include/directfb   -DDATADIR=\"/usr/local/share/clanbomber2/\"   -g -O2 -c Bomber_Corpse.cpp
c++ -DHAVE_CONFIG_H -I. -I. -I.. -D_REENTRANT -D_GNU_SOURCE -I/usr/include/directfb   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/fusionsound -I/usr/include/directfb   -DDATADIR=\"/usr/local/share/clanbomber2/\"   -g -O2 -c Chat.cpp
c++ -DHAVE_CONFIG_H -I. -I. -I.. -D_REENTRANT -D_GNU_SOURCE -I/usr/include/directfb   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/fusionsound -I/usr/include/directfb   -DDATADIR=\"/usr/local/share/clanbomber2/\"   -g -O2 -c ClanBomber.cpp
c++ -DHAVE_CONFIG_H -I. -I. -I.. -D_REENTRANT -D_GNU_SOURCE -I/usr/include/directfb   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/fusionsound -I/usr/include/directfb   -DDATADIR=\"/usr/local/share/clanbomber2/\"   -g -O2 -c Client.cpp
c++ -DHAVE_CONFIG_H -I. -I. -I.. -D_REENTRANT -D_GNU_SOURCE -I/usr/include/directfb   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/fusionsound -I/usr/include/directfb   -DDATADIR=\"/usr/local/share/clanbomber2/\"   -g -O2 -c ClientSetup.cpp
c++ -DHAVE_CONFIG_H -I. -I. -I.. -D_REENTRANT -D_GNU_SOURCE -I/usr/include/directfb   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/fusionsound -I/usr/include/directfb   -DDATADIR=\"/usr/local/share/clanbomber2/\"   -g -O2 -c Config.cpp
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/fstream.tcc: In member function &#8216;virtual typename std::basic_filebuf<_CharT, _Traits>::int_type std::basic_filebuf<_CharT, _Traits>::underflow()&#8217;:
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/fstream.tcc:289: error: expected unqualified-id before &#8216;(&#8217; token
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/fstream.tcc: In member function &#8216;virtual std::streamsize std::basic_filebuf<_CharT, _Traits>::xsputn(const _CharT*, std::streamsize)&#8217;:
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/fstream.tcc:612: error: expected unqualified-id before &#8216;(&#8217; token
make[3]: *** [Config.o] Error 1
make[3]: Leaving directory `/usr/local/src/clanbomber2-0.9/clanbomber'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/local/src/clanbomber2-0.9/clanbomber'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/clanbomber2-0.9'
make: *** [all-recursive-am] Error 2

---

### Post by slayerboy on 2007-03-01
You can try reinstalling lbfusionsound and see if that will fix the issue.  If not I would venture to say that maybe there is some new stuff in fusionsound.  From the [fusionsound homepage]("http://www.directfb.org/index.php?path=Development%2FProjects%2FFusionSound"), it looks like it is up to version 0.9.25, while [Ubuntu's version is 0.9.23]("http://packages.ubuntu.com/edgy/source/fusionsound").  I'm thinking this might have something to do with it.  The next release of Ubuntu, Fiesty, [looks to have 0.9.25]("http://packages.ubuntu.com/feisty/source/fusionsound") in it.  You might have to wait for Fiesty to come out, as it looks like there are a couple extra dependencies for 0.9.25 vs 0.9.23.

---

### Post by ssynesthesia on 2007-03-01
Ok I found this on the forum! DUH I should have looked there... Oh well..

> Problem compiling clanbomber2
By: Paul Hunnisett (phunni) - 2004-07-30 11:03
When trying to install clanbomber2 I get the following error: 
 
make[3]: Entering directory `/var/abs/local/clanbomber2/src/clanbomber2-0.9/clanbomber' 
c++ -DHAVE_CONFIG_H -I. -I. -I.. -D_REENTRANT -I/usr/include/directfb -D_REENTRANT -I/usr/include/fusionsound -I/usr/include/directfb -DDATADIR=\"/usr/share/clanbomber2/\" -march=i686 -O2 -pipe -c Config.cpp 
In file included from /usr/lib/gcc/i686-pc-linux-gnu/3.4.1/../../../../include/c++/3.4.1/fstream:857, 
from Config.cpp:24: 
/usr/lib/gcc/i686-pc-linux-gnu/3.4.1/../../../../include/c++/3.4.1/bits/fstream.tcc: In member function `virtual typename std::basic_filebuf<_CharT, _Traits>::int_type std::basic_filebuf<_CharT, _Traits>::underflow()': 
/usr/lib/gcc/i686-pc-linux-gnu/3.4.1/../../../../include/c++/3.4.1/bits/fstream.tcc:277: error: expected unqualified-id before '(' token 
/usr/lib/gcc/i686-pc-linux-gnu/3.4.1/../../../../include/c++/3.4.1/bits/fstream.tcc: In member function `virtual std::streamsize std::basic_filebuf<_CharT, _Traits>::xsputn(const _CharT*, std::streamsize)': 
/usr/lib/gcc/i686-pc-linux-gnu/3.4.1/../../../../include/c++/3.4.1/bits/fstream.tcc:518: error: expected unqualified-id before '(' token 
make[3]: *** [Config.o] Error 1 
make[3]: Leaving directory `/var/abs/local/clanbomber2/src/clanbomber2-0.9/clanbomber' 
make[2]: *** [all-recursive] Error 1 
make[2]: Leaving directory `/var/abs/local/clanbomber2/src/clanbomber2-0.9/clanbomber' 
make[1]: *** [all-recursive] Error 1 
make[1]: Leaving directory `/var/abs/local/clanbomber2/src/clanbomber2-0.9' 
make: *** [all-recursive-am] Error 2 
==> ERROR: Build Failed. Aborting... 
 
I have no idea what this is about - can anyone help? 

I am unsure what the response meant though.. This requires changing some kind of script but what is it? How do I get to it?

> 
RE: Problem compiling clanbomber2
By: Benjamin Schindler (bschindler) - 2004-11-21 03:49
Here is a fix, that should fix the problem:  
 
--- clanbomber/Config.cpp 2004-11-21 10:19:16.303654776 +0100 
+++ clanbomber/Config.cpp.new 2004-11-21 10:20:33.042988624 +0100 
@@ -23,6 +23,12 @@ 
 
#include "Controller.h" 
 
+#ifdef min 
+#undef min 
+#endif 
+#ifdef max 
+#undef max 
+#endif 
#include <fstream> 
#include <cstdio> 


I dont think I need to worry about fusion sound. It was made in 2004 and I read "FusionSound 0.9.18 or newer is required." so I will reinstall just to be safe.. But what makes you think it has anything to do with fusion sound? 

My main question is what do I have to plug that code into?

---

### Post by ssynesthesia on 2007-03-01
Is there a better section for this question? I have a feeling I am not in the right one..

---

### Post by ssynesthesia on 2007-03-01
Any help would be appreciated...

---

### Post by ssynesthesia on 2007-03-01
Ok I was actually able to fix the error. I, make clean, then configure, then make, then make install, all without errors by doing that patch suggested.

       ---------------------- DirectFB v0.9.24 ---------------------
             (c) 2000-2002  convergence integrated media GmbH  
             (c) 2002-2004  convergence GmbH                   
        -----------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2006-10-13 15:40) 
(*) Direct/Memcpy: Using MMXEXT optimized memcpy()
(!) Direct/Util: opening '/dev/fb0' failed
    --> Permission denied
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
ClanBomber.cpp137
(#) DirectFBError [DirectFBCreate( &dfb )]: Initialization error!


I reinstalled DirectFB. Still got the error.

---

### Post by ssynesthesia on 2007-03-03
Come on people. PLEASE help.. Or at least tell me what section of this forum to go to.

---

### Post by ssynesthesia on 2007-03-05
wow... hello?????

---

### Post by ]Nbx*cmD[ on 2007-04-18
hi!

i just tried to compile clanbomber2, what you found in that topic means that you must modify the source code of the program in order to compile it.

i did it and i attach here the file so that you just need to unzip it and copy it to the directory clanbomber2-0.9/clanbomber

Hope it helps, it worked perfectly for me :P

---

