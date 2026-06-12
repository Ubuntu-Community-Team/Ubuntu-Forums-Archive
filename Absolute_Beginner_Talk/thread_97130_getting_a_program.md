---
title: "getting a program"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by natman on 2005-11-30
Hi, how do i install and get new programs for ubuntu, I am aware of synaptic but the program i want is not there. ( its called polymake )

---

### Post by ed_d on 2005-11-30
try this first:
sudo apt-cache search <packagename> (replace with what you are looking for)

if there:
sudo apt-get install <packagename> (replace with what you found)

---

### Post by natman on 2005-11-30
nope nothing there, I do know were to downlaod the package/program from > [http://www.math.tu-berlin.de/polymake/](http://www.math.tu-berlin.de/polymake/)
But there is loads of downlaod options there, i do not know what do to with them.

Can you help?

---

### Post by Sionide on 2005-11-30
Have you uncommented the Universe repositories in /etc/apt/sources.list ?

What program is it you're looking for??

---

### Post by natman on 2005-11-30
i have all the repositiories open and still nothing i am looking for " polymake"
I can find it at > [http://www.math.tu-berlin.de/polymake/](http://www.math.tu-berlin.de/polymake/)
But i dont know how to install it

---

### Post by ed_d on 2005-11-30
I would assume the bz file under the BSD heading. Unless someone could detail how to convert the rpm format to deb.

Make sure you get the prereqs first.

---

### Post by mishranurag on 2005-11-30
When you click on dowload poymake, a new page does open with detailed instructions for installing the polymake.
[http://www.math.tu-berlin.de/polymake/](http://www.math.tu-berlin.de/polymake/)
Try that
Anurag


[quote=natman]i have all the repositiories open and still nothing i am looking for " polymake"
I can find it at 
But i dont know how to install it[/quote]

---

### Post by nab on 2005-11-30
Hi,

you have to install first the program "alien"

Alien is package converter. You have to convert your rpm to debian package (dpkg). 

In the second step you have to install your programm on a terminal. Switch to the directory you stored your converted file and type:

sudo dpkg -i test.deb 

With test.deb being your converted file. Beware of any depencies they can cause problems.

Hope this helps.

Niko

---

### Post by natman on 2005-11-30
ok i got the alien package and installed it, and downloaded > polymake-2.1.0-2.i586.rpm
How to i run alien , i tried it an dit said something about run as root ?

---

### Post by ex` on 2005-11-30
[QUOTE=natman]ok i got the alien package and installed it, and downloaded 
How to i run alien , i tried it an dit said something about run as root ?[/QUOTE]
"sudo alien -d file.rpm"
This will create a new .deb file in the folder file.rpm is located, which you can then install with "sudo dpkg -i file.deb". :)

> Usage: alien [options] file [...]
  file [...]                Package file or files to convert.
**  -d, --to-deb              Generate a Debian deb package (default).**
     Enables these options:
       --patch=<patch>      Specify patch file to use instead of automatically
                            looking for patch in /var/lib/alien.
       --nopatch            Do not use patches.
       --anypatch           Use even old version os patches.
       --single             Like --generate, but do not create .orig
                            directory.
       --fixperms           Munge/fix permissions and owners.
       --test               Test generated packages with lintian.
  -r, --to-rpm              Generate a Red Hat rpm package.
      --to-slp              Generate a Stampede slp package.
  -l, --to-lsb              Generate a LSB package.
  -t, --to-tgz              Generate a Slackware tgz package.
     Enables these options:
       --description=<desc> Specify package description.
       --version=<version>  Specify package version.
  -p, --to-pkg              Generate a Solaris pkg package.
  -i, --install             Install generated package.
  -g, --generate            Unpack, but do not generate a new package.
  -c, --scripts             Include scripts in package.
  -v, --verbose             Display each command alien runs.
      --veryverbose         Be verbose, and also display output of run commands.  -k, --keep-version        Do not change version of generated package.
  -h, --help                Display this help message.
  -V, --version             Display alien's version number.

Don't worry if nothing happens for a minute, as it'll be busy with converting it.
I just tried it with this package, and it works flawlessly:
> robert@thor:~/polymake$ sudo alien -d polymake-2.1.0-2.i686.rpm
polymake_2.1.0-3_i386.deb generated
robert@thor:~/polymake$

---

### Post by natman on 2005-11-30
ok i did as above an got the following
> natman@bigb:~$ sudo dpkg -i /home/natman/polymake_2.1.0-3_i386.deb
Selecting previously deselected package polymake.
(Reading database ... 129057 files and directories currently installed.)
Unpacking polymake (from .../polymake_2.1.0-3_i386.deb) ...
Setting up polymake (2.1.0-3) ...
natman@bigb:~$ polymake
bash: polymake: command not found

Am i good to go, if so how do i run the program?

---

### Post by ex` on 2005-11-30
[QUOTE=natman]ok i did as above an got the following

Am i good to go, if so how do i run the program?[/QUOTE]
Yeap, good to go. I'm not entirely sure how you run polymake, but mostly there'll be a new icon in your applications list and you can run it from the terminal with "/usr/bin/<program> &", for example: /usr/bin/polymake &

---

### Post by natman on 2005-11-30
sorry to keep bugging you but i did as above
> natman@bigb:~$ /natman/bin/polymake &
bash: /natman/bin/polymake: No such file or directory
[1] 16029
[1]   Exit 127                /natman/bin/polymake
natman@bigb:~$ /usr/bin/polymake &
bash: /usr/bin/polymake: No such file or directory
[1] 16032
[1]   Exit 127                /usr/bin/polymake
natman@bigb:~$

and nothing, did i install it right?

---

### Post by ex` on 2005-11-30
[QUOTE=natman]sorry to keep bugging you but i did as above

and nothing, did i install it right?[/QUOTE]
As said, it can differ. "sudo updatedb" and "locate polymake" will list the location(s) of polymake, where you can pay special attention to any 'bin' folder as this will contain a polymake binary.

Just say so if you really can't find it and I'll check it on my system for you. :) (I don't have polymake installed myself)

---

### Post by natman on 2005-11-30
ok i have something  in the  /usr/local/polymake/
and that contains loads of files, i had a look around clicked loads of things , and nothing.
If its not to much bother could you help me out?
Thanks:

---

### Post by ex` on 2005-11-30
The binaries are in /usr/local/polymake/bin/, one called 'polymake'.
So you could call it with "/usr/local/polymake/bin/polymake"

note: If it returns a bunch of error message you probably forgot to install the required perl modules as well, which you can find on the polymake website as well.
Same thing going on there, just do an "alien -d file.rpm" and "dpkg -i file.deb"  and install those as well. :)

---

### Post by natman on 2005-11-30
ok did that and got the following
> natman@bigb:~$ /usr/local/polymake/bin/polymake
Can't locate loadable object for module Poly::Ext in @INC (@INC contains: /usr/local/polymake/perl /usr/local/polymake/perlx /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/local/polymake/perl/Poly.pm line 20
Compilation failed in require at /usr/local/polymake/perl/Poly.pm line 20.
BEGIN failed--compilation aborted at /usr/local/polymake/perl/Poly.pm line 20.
Compilation failed in require at /usr/local/polymake/perl/Switches.pm line 18.
BEGIN failed--compilation aborted at /usr/local/polymake/perl/Switches.pm line 18.
Compilation failed in require at /usr/local/polymake/bin/polymake line 41.
BEGIN failed--compilation aborted at /usr/local/polymake/bin/polymake line 41.


So i am guess ia m missing some sort of packages, any advice aon how to get them , if you dont never mind, you have been of tremendous help
Thanks:

---

### Post by ex` on 2005-11-30
[QUOTE=natman]ok did that and got the following


So i am guess ia m missing some sort of packages, any advice aon how to get them , if you dont never mind, you have been of tremendous help
Thanks:[/QUOTE]
I just included this bit in my earlier post:
> note: If it returns a bunch of error message you probably forgot to install the required perl modules as well, which you can find on the polymake website as well.
Same thing going on there, just do an "alien -d file.rpm" and "dpkg -i file.deb" and install those as well.

It are the 'gpm' files on the polymake website that you need. :)

---

### Post by natman on 2005-11-30
ok n, im off to rest , i will try again tmrw , may i send a private message to you if i get it working?
Once again thanx for all the help.

---

### Post by ex` on 2005-11-30
[QUOTE=natman]ok n, im off to rest , i will try again tmrw , may i send a private message to you if i get it working?
Once again thanx for all the help.[/QUOTE]
Ofcourse you may. But I don't have any experience with the program itself, if that's what you think.

---

