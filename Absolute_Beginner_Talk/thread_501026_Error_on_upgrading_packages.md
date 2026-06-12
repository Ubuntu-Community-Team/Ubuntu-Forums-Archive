---
title: "Error on upgrading packages"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by ~cyrus~ on 2007-07-14
During the installation process of software updates my screen froze and I had to switch off my computer and restart.

My Synaptic package manager asked me to run this manually when I tried to open it on restart
```

sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0014' near line 7 package `ttf-opensymbol':
 field name `Architecture;' must be followed by colon

```

Kindly advise

---

### Post by starsky on 2007-07-14
hi there :)

$ sudo  dpkg --audit

should get you going.

HTH

---

### Post by tennvolsmb on 2007-07-14
have you been screwing around with some of your files? have you been logging on to the root account any?

---

### Post by ~cyrus~ on 2007-07-14
> **starsky said:**
> hi there :)

$ sudo  dpkg --audit

should get you going.

HTH

Thanks for the response.

The above command gave me the same response that I posted.

---

### Post by ~cyrus~ on 2007-07-14
> **tennvolsmb said:**
> have you been screwing around with some of your files? have you been logging on to the root account any?

No...haven't touched any files.

Only logging into my account that I created at the start.

---

### Post by starsky on 2007-07-14
ok try this 

$ sudo dpkg-query -l

and see if any errors comes ups

also if that doesn't work

$ sudo dpkg --forget-old-unavail

if still, then,
$ sudo dpkg --clear-avail

and also if still

$ sudo dpkg --reconfigure dpkg

post back :)

---

### Post by ~cyrus~ on 2007-07-14
cyrus@cyrus-desktop:~$ sudo dpkg-query -l
Password:
dpkg-query: parse error, in file `/var/lib/dpkg/updates/0014' near line 7 package `ttf-opensymbol':
 field name `Architecture;' must be followed by colon
cyrus@cyrus-desktop:~$ sudo dpkg -forget-old-unavail 
dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
cyrus@cyrus-desktop:~$ sudo dpkg --clear-avail
cyrus@cyrus-desktop:~$ sudo dpkg --reconfigure dpkg
dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by starsky on 2007-07-14
> **~cyrus~ said:**
> cyrus@cyrus-desktop:~$ sudo dpkg-query -l
Password:
dpkg-query: parse error, in file `/var/lib/dpkg/updates/0014' near line 7 package `ttf-opensymbol':
 field name `Architecture;' must be followed by colon
cyrus@cyrus-desktop:~$ sudo dpkg -forget-old-unavail 
dpkg: unknown option -o

it's
```
 "--forget-old-available" 
```

> 
cyrus@cyrus-desktop:~$ sudo dpkg --reconfigure dpkg
dpkg: unknown option --reconfigure


it's ```
 dpkg-reconfigure dpkg 
```


BTW, after doing all of them what happens if you do -

$ sudo mkdir /var/lib/dpkg.backup/
$ sudo cp -R /var/lib/dpkg /var/lib/dpkg.backup/
$ sudo rm -rf /var/lib/dpkg ?
$ sudo apt-get update
$ sudo apt-get install <whatever-you-were-installing-in-the-first-place>

Don't worry as we have already backed up the dpkg database. and if anything goes wrong, we can copy it back to /var/lib/dpkg/
 ;)

---

### Post by ~cyrus~ on 2007-07-15
cyrus@cyrus-desktop:~$ sudo dpkg --forget-old-available
dpkg: unknown option --forget-old-available

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
cyrus@cyrus-desktop:~$ sudo dpkg-reconfigure dpkg
dpkg-query: parse error, in file `/var/lib/dpkg/updates/0014' near line 7 package `ttf-opensymbol':
 field name `Architecture;' must be followed by colon
/usr/sbin/dpkg-reconfigure: dpkg is not installed

I only did this and did not continue as I did not understand the section where you said:
sudo rm -rf /var/lib/dpkg ?
and
sudo apt-get install <whatever-you-were-installing-in-the-first-place>

I was updating 90 packages that I was asked to by clicking the symbol on the top right of the screen....I think they downloaded but during the installation, my screen froze.

This is a new install on a clean hard drive made yesterday from a Live CD that I had, and the 90 packages was my first update.

When I now go to Synaptic package manager I am told that an error ocured and am asked to do the following:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I run 'dpkg --configure -a'
I am told about the parse error in update0014 that I mentioned in my first post in this thread.

Thanks for your time and attention.

---

### Post by ~cyrus~ on 2007-07-15
What I did was to gedit /var/lib/dpkg/updates/0014 and change the syntax after Architecture to a colon.

That sorted it out.

Thanks.

---

### Post by starsky on 2007-07-15
> **~cyrus~ said:**
> What I did was to gedit /var/lib/dpkg/updates/0014 and change the syntax after Architecture to a colon.

That sorted it out.

Thanks.

I was going to suggest you to edit /var/lib/dpkg/updates/0014 but didn't do so thinking that might break some other packages.
Glad you made it work :)

---

### Post by EricNutsch on 2007-07-15
Thanks to all. This blog was very helpful
I somehow derailed the Update manager. It wanted me to "dpkg configure -a" but that didn't work.

the code "dpkg-reconfigure dpkg"    worked like a charm

Thanks again :)

---

