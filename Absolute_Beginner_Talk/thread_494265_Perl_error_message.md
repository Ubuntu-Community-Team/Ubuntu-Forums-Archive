---
title: "Perl error message"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by B-777 on 2007-07-06
I am trying to compile some programs from the terminal in ubuntu 6.06 due to the program packages being unavailable in the repository.

When I attempt to compile the programs in the terminal the error messge below appears:

checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

Is there a work around this?

---

### Post by DBStevens on 2007-07-06
You are missing a perl module.

You can use cpan to install it.

sudu perl -MCPAN -e 'install Bundle::XML' 

Just might do it although it could be seperately packaged.

---

### Post by B-777 on 2007-07-06
> **DBStevens said:**
> You are missing a perl module.

You can use cpan to install it.

sudu perl -MCPAN -e 'install Bundle::XML' 

Just might do it although it could be seperately packaged.

Sorry, I am a newbie when it comes to Ubuntu. 

Could you please explain to me what to do step-by-step?

---

### Post by Rocket2DMn on 2007-07-06
DBStevens is suggesting that you open a Terminal and run the command:
```
sudo perl -MCPAN -e 'install Bundle::XML'
```
You will be prompted for your password (just type it in even though nothing appears), and you will download a bundle of XML stuff for perl, including the module you need to compile.
Good luck

---

### Post by B-777 on 2007-07-06
Thanks...that worked like a charm...not used to seeing CPAN...,.I am used to the word terminal :)

---

### Post by DBStevens on 2007-07-06
Open a terminal session and type the line I gave you and hit enter.

I don't run Gnome, on my system it is applications > accesories > terminal there should be something similar to that on your menus.

---

### Post by DBStevens on 2007-07-06
CPAN is a very large collection of perl modules.   It is very easy to install the modules using their system.

---

### Post by B-777 on 2007-07-06
Ok it almost worked...but it now comes up with an error message saying that it failed some tests and it could not be force installed.

Is there an alternative install?

---

### Post by Rocket2DMn on 2007-07-06
Can you please post the error (with the command you entered)?

---

### Post by B-777 on 2007-07-06
>   CPAN.pm: Going to build C/CO/COOPERCL/XML-Encoding-1.01.tar.gz

cp Encoding.pm blib/lib/XML/Encoding.pm
cp bin/make_encmap blib/script/make_encmap
/usr/bin/perl "-MExtUtils::MY" -e "MY->fixin(shift)" blib/script/make_encmap
cp bin/compile_encoding blib/script/compile_encoding
/usr/bin/perl "-MExtUtils::MY" -e "MY->fixin(shift)" blib/script/compile_encoding
Manifying blib/man3/XML::Encoding.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-Iblib/lib" "-Iblib/arch" test.pl
1..7
Can't locate XML/Parser.pm in @INC (@INC contains: blib/lib blib/arch /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at blib/lib/XML/Encoding.pm line 15.
BEGIN failed--compilation aborted at blib/lib/XML/Encoding.pm line 15.
Compilation failed in require at test.pl line 11.
BEGIN failed--compilation aborted at test.pl line 11.
not ok 1
make: *** [test_dynamic] Error 2
  /usr/bin/make test -- NOT OK
Running make install
  make test had returned bad status, won't install without force

This is what came up, I cannot get the command I entered before this, as it has scrolled off the top of the screen.

---

### Post by DBStevens on 2007-07-06
There is always the possibility there is other stuff missing.

You might also tell us exactly what you are trying to install.

---

### Post by B-777 on 2007-07-06
>   CPAN.pm: Going to build C/CO/COOPERCL/XML-Encoding-1.01.tar.gz

cp Encoding.pm blib/lib/XML/Encoding.pm
cp bin/make_encmap blib/script/make_encmap
/usr/bin/perl "-MExtUtils::MY" -e "MY->fixin(shift)" blib/script/make_encmap
cp bin/compile_encoding blib/script/compile_encoding
/usr/bin/perl "-MExtUtils::MY" -e "MY->fixin(shift)" blib/script/compile_encoding
Manifying blib/man3/XML::Encoding.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-Iblib/lib" "-Iblib/arch" test.pl
1..7
Can't locate XML/Parser.pm in @INC (@INC contains: blib/lib blib/arch /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at blib/lib/XML/Encoding.pm line 15.
BEGIN failed--compilation aborted at blib/lib/XML/Encoding.pm line 15.
Compilation failed in require at test.pl line 11.
BEGIN failed--compilation aborted at test.pl line 11.
not ok 1
make: *** [test_dynamic] Error 2
  /usr/bin/make test -- NOT OK
Running make install
  make test had returned bad status, won't install without force

This is what came up, I cannot get the command I entered before this, as it has scrolled off the top of the screen.

---

### Post by DBStevens on 2007-07-06
Use synaptic to install all of the libxml-  packages there are 15 of them total showing in my version.

---

### Post by B-777 on 2007-07-06
Installed all the libxml packages as requested, but then this comes up...

> E: libxml-sax-perl: subprocess post-installation script returned error exit status 255
E: libxml-libxml-perl: dependency problems - leaving unconfigured
E: libxml-sax-expat-perl: dependency problems - leaving unconfigured
E: libxml-simple-perl: dependency problems - leaving unconfigured

---

### Post by DBStevens on 2007-07-06
Great just great, try your original compile again.

---

### Post by DBStevens on 2007-07-06
BTW what are you trying to install?

---

### Post by B-777 on 2007-07-06
Pidgin 2.0.2.

---

### Post by B-777 on 2007-07-06
Almost got it working now...just need to find a package called glib.

I am sure I can find it out there somewhere. Thanks for the help.

---

### Post by B-777 on 2007-07-06
Ok I found a .deb package for pidgin and installed it, but now I can't find it...how do I go about finding a program I just installed?

---

### Post by Rocket2DMn on 2007-07-06
Applications->Internet->Pidgin Internet Messenger
If it's not there you can just run "pidgin" from terminal and/or create a launcher.

---

### Post by B-777 on 2007-07-06
> **Rocket2DMn said:**
> Applications->Internet->Pidgin Internet Messenger
If it's not there you can just run "pidgin" from terminal and/or create a launcher.

How do I run it from the terminal and create a launcher.

Sorry about asking these questions, but I am new to the world of ubuntu.

---

### Post by DBStevens on 2007-07-06
You can ask synaptic where it put things you highlight  the package and select properties and click on installed files.

It also could be under Applications > Network that is where the IM like chat clients go on my system.

---

### Post by Rocket2DMn on 2007-07-07
The terminal can be found under the Applications->Accessories menu.
You can create a launcher on your desktop by just right clicking and selecting Create Launcher
   give it whatever name you want and the command would just be "pidgin", just like you would put into the terminal.  You can leave the Comment portion empty.
You can add a launcher to the panel (top or bottom) by right clicking on empty space and hitting Add To Panel then choosing Custom Appliaction Launcher and proceeding like above.

---

