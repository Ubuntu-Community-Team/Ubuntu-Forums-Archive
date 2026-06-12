---
title: "[SOLVED] All i wanted for Christmas was an Apache Server"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by TSRep13 on 2008-01-22
My buddy hooked me up w/ and old Dell Dimension 8200 w/ Xubuntu 7.10 on it.  I had told him that I wanted to try making a simple server so I could grab my homework files from anywhere in the world :-)

I have tried several times to install Apache, and I can get as far as Build, but when I try the Install [$ make install] I get the following script:

[INDENT]Making install in srclib
make[1]: Entering directory `/home/tsrep/Apache/httpd-2.2.8/srclib'
Making install in apr
make[2]: Entering directory `/home/tsrep/Apache/httpd-2.2.8/srclib/apr'
sed 's,^\(location=\).*$,\1installed,' < apr-1-config > apr-config.out
sed 's,^\(apr_build.*=\).*$,\1/usr/local/apache2/build,' < build/apr_rules.mk > build/apr_rules.out
make[3]: Entering directory `/home/tsrep/Apache/httpd-2.2.8/srclib/apr'
make[3]: Nothing to be done for `local-all'.
make[3]: Leaving directory `/home/tsrep/Apache/httpd-2.2.8/srclib/apr'
/home/tsrep/Apache/httpd-2.2.8/srclib/apr/build/mkdir.sh /usr/local/apache2/lib /usr/local/apache2/bin /usr/local/apache2/build \
                     /usr/local/apache2/lib/pkgconfig /usr/local/apache2/include
mkdir /usr/local/apache2
mkdir: cannot create directory `/usr/local/apache2': Permission denied
mkdir /usr/local/apache2/lib
mkdir: cannot create directory `/usr/local/apache2/lib': No such file or directory
mkdir /usr/local/apache2
mkdir: cannot create directory `/usr/local/apache2': Permission denied
mkdir /usr/local/apache2/bin
mkdir: cannot create directory `/usr/local/apache2/bin': No such file or directory
mkdir /usr/local/apache2
mkdir: cannot create directory `/usr/local/apache2': Permission denied
mkdir /usr/local/apache2/build
mkdir: cannot create directory `/usr/local/apache2/build': No such file or directory
mkdir /usr/local/apache2
mkdir: cannot create directory `/usr/local/apache2': Permission denied
mkdir /usr/local/apache2/lib
mkdir: cannot create directory `/usr/local/apache2/lib': No such file or directory
mkdir /usr/local/apache2/lib/pkgconfig
mkdir: cannot create directory `/usr/local/apache2/lib/pkgconfig': No such file or directory
mkdir /usr/local/apache2
mkdir: cannot create directory `/usr/local/apache2': Permission denied
mkdir /usr/local/apache2/include
mkdir: cannot create directory `/usr/local/apache2/include': No such file or directory
make[2]: *** [install] Error 1
make[2]: Leaving directory `/home/tsrep/Apache/httpd-2.2.8/srclib/apr'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/tsrep/Apache/httpd-2.2.8/srclib'
make: *** [install-recursive] Error 1
tsrep@tsrep-desktop:~/Apache/httpd-2.2.8$ /usr/local/apache2/conf/httpd.conf
bash: /usr/local/apache2/conf/httpd.conf: No such file or directory
[/INDENT]

I am really really new to all of this, so I am a little overwhelmed.  Any ideas, comments, or just plain words of encouragment for me?

---

### Post by nick_h on 2008-01-22
You need to run the install with sudo:
```
sudo make install
```

Is there a reason why you are not installing it from the repositories?

---

### Post by stump138 on 2008-01-22
Apache is available via apt and couldn't be easier to get going :)  No need for you to compile it yourself :)
```
sudo apt-get update && sudo apt-get install apache2
```

---

### Post by luisromangz on 2008-01-22
To install a program you need superuser privileges, that's why you get the "permission denied" error while make installin'. You can get those with the sudo command which will ask for your account's password.

For example: sudo make install

By the way, you shouldn't need to compile apache, because there are apache packages in the Ubuntu repositories.

---

### Post by jan quark on 2008-01-22
on my site is a short tutorial how I once set up an apache server on my desktop pc

perhps it will help
direct link is
[http://janquark.fatfreehost.com/tutorial2.html](http://janquark.fatfreehost.com/tutorial2.html)

---

### Post by Arwen on 2008-01-22
Apache installation isn't sth I'm familiar with but all those "permission denied"..Did you check the permissions you have in /usr/local?

---

### Post by TSRep13 on 2008-01-22
See i knew I was doing things the hard way :-) Thanks a lot everyone, it was all very helpful.    You have to love forums, people helping people... there is hope for society yet, lol.

So if I may, I have a follow up question.  If I have Apache installed, how do I configure it?  I guess I thought that there would be a program added to my "Applications" and I could just click a prefernces button or something.

Thanks again everyone.  I kind of feel a little silly now that the answer to the original was so simple.  I am hoping this one is the same.

---

### Post by fatality_uk on 2008-01-22
Or alternatively, from Synaptic Package Manager, choose edit->mark packages by task and select LAMP install :)

---

### Post by irish_flu on 2008-01-22
> **TSRep13 said:**
> See i knew I was doing things the hard way :-) Thanks a lot everyone, it was all very helpful.    You have to love forums, people helping people... there is hope for society yet, lol.

So if I may, I have a follow up question.  If I have Apache installed, how do I configure it?  I guess I thought that there would be a program added to my "Applications" and I could just click a prefernces button or something.

Thanks again everyone.  I kind of feel a little silly now that the answer to the original was so simple.  I am hoping this one is the same.

Apache is configured by editing "conf" files, and by adding files to the directory where it looks for pages (/var/www).

Here's a link to the apache documentation:
[http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/)

It's not as bad as it sounds, really.  You'll get used to it faster than you think.

EDIT: Oh yeah, and if you post your apache config questions in the ubuntu-server subforum here, I bet you'll get good answers.

---

### Post by ghpk on 2008-01-22
> **fatality_uk said:**
> Or alternatively, from Synaptic Package Manager, choose edit->mark packages by task and select LAMP install :)

exactly found this thread for my current problem

i dont see option for LAMP in mark packages by task ????

When i try to install apache from terminal i get the following errors:-
```
 manu@manu-laptop:~$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting apache2-mpm-itk instead of apache2
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation: 
```

then i tried :-

manu@manu-laptop:~$ sudo apt-get update && sudo apt-get install apache2
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                                                
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_IN
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_IN
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                                                                 
Fetched 2B in 9s (0B/s)                                                                                                 
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting apache2-mpm-itk instead of apache2
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  apache2-mpm-itk: Depends: apache2.2-common (= 2.2.4-3build1) but it is not installable
                   Depends: libapr1 but it is not installable
                   Depends: libaprutil1 but it is not installable
                   Depends: libpq5 but it is not installable
E: Broken packages
manu@manu-laptop:~$ 

Any suggestions would be kind help to me.

---

### Post by TSRep13 on 2008-01-22
I appreciate the words of encouragment.  I have found the forums to be very benifitial.  

I checked out the link to apache's doc site... WHOA! was all I could say.  I had better luck reading Miranda v. Arizona and understanding that then apache's site.  Too much information way too fast.  I am still weening off the bottle and that site was trying to shovel steak down my throat :-P

Maybe it wasn't as complex as it appeared, but it was overwhelming to say the least... at least right now.

I think I will take your advice and post something in the ubuntu-server subforum and see what kind of help I can get there too.  

Thanks, every little bit helps :-D

---

### Post by ghpk on 2008-01-22
I was not enabling all the sources so,

another thread solved my problem, Apache is installed, up and running now on my laptop.

System>administration>software sources>chek all boxes under Ubuntu software and under updates tab.Reload.

---

