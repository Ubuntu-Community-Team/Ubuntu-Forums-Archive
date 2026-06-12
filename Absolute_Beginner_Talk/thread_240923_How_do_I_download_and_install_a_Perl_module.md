---
title: "How do I download and install a Perl module?"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by foxystoatyweasely on 2006-08-21
I'm installing Webmin on an Ubuntu 6.06 server and I keep getting "access denied" msgs. I checked the miniserv.error log and it says that Authen::PAM is required and not installed.

My 2 Qs are:

How do I get that from CPAN using the command line?

How do I then install it?

Any help much appreciated - thanks in advance folks.

---

### Post by TFX360 on 2006-08-21
foxystoatyweasely,


try installing libauthen-pam-perl


```
aptitude install libauthen-pam-perl
```


Kind regards,


TFX

---

### Post by foxystoatyweasely on 2006-08-21
> **TFX360 said:**
> foxystoatyweasely,


try installing libauthen-pam-perl


```
aptitude install libauthen-pam-perl
```


Kind regards,


TFX

Hi TFX, thx for the pointer, but when I try this I get the following errmsg: 'No candidate version found for libauthen-pam-perl'

Having no luck, I then tried cpan> install Authen:PAM which ended with the msg:

'C compiler cannot create executables'


Any ideas?

](*,)

---

### Post by TFX360 on 2006-08-22
Maybe a little update? Build essentials?

```
sudo aptitude update; sleep 10; sudo aptitude upgrade; sleep 10; sudo aptitude install build essentials
```

Then I'm at my wits end...


Kind regards,


TFX

---

### Post by kernelpanicked on 2006-08-22
First check to see if it can be installed with apt. If not run the following command.

sudo perl -MCPAN -e shell

Answer the setup questions, which are almost all perfectly fine accepting the defaults and when it's done type.

cpan> install Authen::PAM

EDIT: My bad, I didn't see that you tried this already. You're gonna need build-essential first.

---

### Post by foxystoatyweasely on 2006-08-22
> **kernelpanicked said:**
> First check to see if it can be installed with apt. If not run the following command.

sudo perl -MCPAN -e shell

Answer the setup questions, which are almost all perfectly fine accepting the defaults and when it's done type.

cpan> install Authen::PAM

EDIT: My bad, I didn't see that you tried this already. You're gonna need build-essential first.

Tried that too, now I'm getting "cannot find the pam_appl.h file" as an errmsg. Here's the output:

apt-get install build-essential

then

perl Makefile.PL && make && make test


Checking if your kit is complete...
Looks good
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for pam header files in... no
configure: error: cannot find the pam_appl.h file
Error in configuring the Authen::PAM module.

---

### Post by kernelpanicked on 2006-08-22
I got it working here on Xubuntu 6.06 with a little fiddling. First did an aptitude install build-essential, which got me to where you're at. Then I had to install libpam-dev to clear the pam_appl.h error. This gave me a brand new error.

```

checking for PAM_RADIO_TYPE... yes
checking for PAM_BINARY_PROMPT... yes
checking whether RTLD_GLOBAL is declared... yes
configure: creating ./config.status
config.status: creating pam.cfg
config.status: creating PAM.pm
config.status: creating PAM_config.h
Writing Makefile for Authen::PAM
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible

``` 
but who needs tests anyway, right? So 
```

cd .cpan/build/Authen-PAM-0.16/
make
sudo make install

``` 
Worked for me, hopefully it'll work for you :)

---

### Post by bdalzell on 2006-08-22
I think the critical thing to remember with Ubuntu and Perl modules is that you have to use sudo or su when launching mCPAN or the install will fail because of ownership problems.

---

### Post by foxystoatyweasely on 2006-08-22
> **kernelpanicked said:**
> I got it working here on Xubuntu 6.06 with a little fiddling. First did an aptitude install build-essential, which got me to where you're at. Then I had to install libpam-dev to clear the pam_appl.h error. This gave me a brand new error.

```

checking for PAM_RADIO_TYPE... yes
checking for PAM_BINARY_PROMPT... yes
checking whether RTLD_GLOBAL is declared... yes
configure: creating ./config.status
config.status: creating pam.cfg
config.status: creating PAM.pm
config.status: creating PAM_config.h
Writing Makefile for Authen::PAM
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible

``` 
but who needs tests anyway, right? So 
```

cd .cpan/build/Authen-PAM-0.16/
make
sudo make install

``` 
Worked for me, hopefully it'll work for you :)


Thank you Kernelpanicked that worked!! =D> 

I installed the libpam-dev as you advised,

then

cd .cpan/build/Authen-PAM-0.16/

then (I had to complete the next step as a single command for some reason)

perl Makefile.PL && make && make test

RESULT!! ThankyouThankyouThankyouThankyou - been banging my head on this one for a few days.

Onward to the next brick wall I guess ;)

Thanks to all for assistance and advice given.

---

### Post by kernelpanicked on 2006-08-22
Awesome. I'm glad it worked out for you.

---

### Post by kernelpanicked on 2006-08-23
> **bdalzell said:**
> I think the critical thing to remember with Ubuntu and Perl modules is that you have to use sudo or su when launching mCPAN or the install will fail because of ownership problems.

I just had to come back and address this, as this thread might be seen by others later on. I know it's typical around these forums to see "oh you have a problem doing something, just put sudo in front of it", but when compiling code, especially from CPAN, building as root is a bad idea. 

Here one little instance (there are other reasons but this is one of the most glaring). Say I compile Authen::PAM as root using the CPAN shell. The build takes place in .cpan/build/Authen-PAM-0.16/. Next week the author of this module finds a vulnerability in it and updates to 0.18. I update as well, and this gets built in cpan/build/Authen-PAM-0.18/. While I've updated the package, all the binaries are still there from the previous build, meaning I still have vulnerable code on my system with root ownership, and possibly setuid, as this is a PAM module.

---

### Post by foxystoatyweasely on 2006-08-25
edit: incorrect info posted - brb

---

### Post by floyd24 on 2006-08-28
Maybe I was just lucky, but this is how it worked for me on a debootstrapped base-install ubuntu-server 6.06:

Same Problem here, I wanted to get webmin (webmin-1.290-minimal.tar.gz) running which failed due to missing PAM perl module.

* Added universe repository by copying the "main" line in /etc/apt/sources.list and changing "main" to "universe"

* apt-get update

* apt-get install libauthen-pam-perl

* say yes to some 20 Megs (perl, perl-modules)

* /etc/init.d/webmin start

* /etc/init.d/webmin status
  webmin...running

HTH anyone...

cheerz, Floyd

PS: To activate SSL for webmin, just install libnet-ssleay-perl the same way. For me it worked instantly.

---

### Post by zoubidoo on 2006-08-31
Webmin should work without compiling and install perl modules outside of the same repository.  If its dependencies are not met it shouldn't be in the main repository.  For me this is a bug.

Z.

---

### Post by jerovich on 2008-04-18
I know this is an old one but its the first thing I got when googling my similar problem so I thought I'd share the solution that worked for me. 

It turned out that because I had run cpan before installing build-essentials my cpan config was incorrect. I deleted the .cpan directory and reran the cpan, went through the configuration and was able to install modules using cpan.

---

