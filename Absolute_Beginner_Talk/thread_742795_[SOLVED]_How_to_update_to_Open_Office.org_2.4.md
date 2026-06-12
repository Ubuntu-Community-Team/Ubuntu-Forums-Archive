---
title: "[SOLVED] How to update to Open Office.org 2.4"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-04-02
hello

I'm on Ubuntu Gutsy 7.10. The current OpenOffice.org version I have is 2.3. I heard there's a new version, 2.4, and I'm wondering if anyone knows what I should do to upgrade. 

Many thanks.

---

### Post by housam on 2008-04-02
If it is released, it should be among the system updates. anyway try to add [[COLOR="Red"]_extra repositories _[/COLOR]]("http://www.psychocats.net/ubuntu/sources")to your system and search for new updates once more.

---

### Post by TheLions on 2008-04-02
if you realy need the OO 2.4 you can install new verson of Ubuntu or remove the old version and install this one (.deb):
[http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)

---

### Post by al.adab on 2008-04-02
Thanks for your reply.

I added the extra repositories, but see no trace of OO.org 2.4. I checked in Synaptics as well. Do you know if it's possible to run a command on terminal to update from 2.3 to 2.4? The 2.3 is good but has got an issue ("italics" button, see Poll: OpenOffice "Italic" button's annoying behaviour) and I'm hoping the 2.4 doesn't.

---

### Post by stchman on 2008-04-02
> **al.adab said:**
> hello

I'm on Ubuntu Gutsy 7.10. The current OpenOffice.org version I have is 2.3. I heard there's a new version, 2.4, and I'm wondering if anyone knows what I should do to upgrade. 

Many thanks.

You can download the Debian package from OO's website.  Use this link to download OO 2.4 for debian.

[http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.0](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.0)

The file is named:

OOo_2.4.0_LinuxIntel_install_en-US_deb.tar.gz

You MUST have a JRE installed for full OO functionality.

You will then need to uninstall the old OO.  To do this use this command in a terminal:

```
sudo apt-get -y remove openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer
```

After that remove the residual config in Synaptic.

Now lets assume you downloaded the deb tar.gz to your home folder.

In a terminal:
```

cd ~

tar -vxzf ~/OO*

cd O*

cd DEBS

sudo dpkg -i *.deb

cd desk*

sudo dpkg -i *.deb


```

You are now the proud owner of OO 2.4.

---

### Post by al.adab on 2008-04-02
many thanks stchman!!!

just a question before I do what you suggest...what's a JRE? Where can I find it / how can I install it (if I don't have it, and of course how can I verify if I have it)?

---

### Post by stchman on 2008-04-02
> **al.adab said:**
> many thanks stchman!!!

just a question before I do what you suggest...what's a JRE? Where can I find it / how can I install it (if I don't have it, and of course how can I verify if I have it)?

JRE = Java Runtime Environment.  To install Java on Ubuntu do the following:

```
sudo apt-get -y install sun-java5-bin sun-java5-fonts sun-java5-jdk sun-java5-jre sun-java5-plugin
```

The Java I choose is 1.5, now I know other forum members will yell at me that 1.6 is in the repos but I have had ZERO problems with the 1.5 JRE.  If you insist on the 1.6 substitute 6 for 5 in the apt-get statement.

To verify you have a working JRE type this in a terminal:

```
java -version
```

You should get a string back.

---

### Post by al.adab on 2008-04-02
*After that remove the residual config in Synaptic.*

Can you please confirm I should just check anything whose name begins with open office in Synaptics? Or should I take care of removing things under different names? 

Thanks stchman for your help!

---

### Post by stchman on 2008-04-02
> **al.adab said:**
> *After that remove the residual config in Synaptic.*

Can you please confirm I should just check anything whose name begins with open office in Synaptics? Or should I take care of removing things under different names? 

Thanks stchman for your help!

You can check this:

```
dpkg -l | grep open
```

This will give a list of all the installed packages that have the word open in them.  There should only be the hyphenation package.  The apt-get remove statement should take care of everything else.

Also make sure that all the openoffice.org-style- packages are removed.  They are icon packages and OO2.4 from the website does not need them.

---

### Post by al.adab on 2008-04-02
This is what I get after running the dpkg - I see more than one "open". What shall I do? 

~$ dpkg -l | grep open
ii  libltdl3                                   1.5.24-1ubuntu1                      A system independent dlopen wrapper for GNU 
ii  libmatroska0                               0.8.1-1                              extensible open standard audio/video contain
ii  libmeanwhile1                              1.0.2-3                              open implementation of the Lotus Sametime Co
ii  libopenal0a                                1:0.0.8-4ubuntu2                     OpenAL is a portable library for 3D spatiali
ii  libopencdk8                                0.5.13-2                             Open Crypto Development Kit (OpenCDK) (runti
ii  libopenexr2c2a                             1.2.2-4.3ubuntu2                     runtime files for the OpenEXR image library
ii  libopenspc0                                0.3.99a-2                            library for playing SPC files
ii  lsof                                       4.78.dfsg.1-2                        List open files
rc  openoffice.org-base                        1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - database
rc  openoffice.org-calc                        1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - spreadsheet
rc  openoffice.org-common                      1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite architecture ind
rc  openoffice.org-core                        1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite architecture dep
rc  openoffice.org-draw                        1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - drawing
ii  openoffice.org-hyphenation                 0.2                                  Hyphenation patterns for OpenOffice.org
rc  openoffice.org-impress                     1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - presentation
rc  openoffice.org-math                        1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - equation edito
rc  openoffice.org-thesaurus-en-us             1:2.2.0-2ubuntu1                     English Thesaurus for OpenOffice.org
rc  openoffice.org-writer                      1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - word processor
ii  openprinting-ppds                          20070919-0ubuntu3                    OpenPrinting printer support - PostScript PP
ii  openssh-client                             1:4.6p1-5ubuntu0.2                   secure shell client, an rlogin/rsh/rcp repla
ii  openssl                                    0.9.8e-5ubuntu3.1                    Secure Socket Layer (SSL) binary and related
ii  ssl-cert                                   1.0.14                               Simple debconf wrapper for openssl
ii  ttf-mgopen                                 1.1-2                                Magenta Open Truetype fonts
ii  ttf-opensymbol                             1:2.3.0-1ubuntu5.3                   The OpenSymbol TrueType font

---

### Post by stchman on 2008-04-02
> **al.adab said:**
> This is what I get after running the dpkg - I see more than one "open". What shall I do? 

~$ dpkg -l | grep open
ii  libltdl3                                   1.5.24-1ubuntu1                      A system independent dlopen wrapper for GNU 
ii  libmatroska0                               0.8.1-1                              extensible open standard audio/video contain
ii  libmeanwhile1                              1.0.2-3                              open implementation of the Lotus Sametime Co
ii  libopenal0a                                1:0.0.8-4ubuntu2                     OpenAL is a portable library for 3D spatiali
ii  libopencdk8                                0.5.13-2                             Open Crypto Development Kit (OpenCDK) (runti
ii  libopenexr2c2a                             1.2.2-4.3ubuntu2                     runtime files for the OpenEXR image library
ii  libopenspc0                                0.3.99a-2                            library for playing SPC files
ii  lsof                                       4.78.dfsg.1-2                        List open files
rc  openoffice.org-base                        1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - database
rc  openoffice.org-calc                        1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - spreadsheet
rc  openoffice.org-common                      1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite architecture ind
rc  openoffice.org-core                        1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite architecture dep
rc  openoffice.org-draw                        1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - drawing
ii  openoffice.org-hyphenation                 0.2                                  Hyphenation patterns for OpenOffice.org
rc  openoffice.org-impress                     1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - presentation
rc  openoffice.org-math                        1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - equation edito
rc  openoffice.org-thesaurus-en-us             1:2.2.0-2ubuntu1                     English Thesaurus for OpenOffice.org
rc  openoffice.org-writer                      1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - word processor
ii  openprinting-ppds                          20070919-0ubuntu3                    OpenPrinting printer support - PostScript PP
ii  openssh-client                             1:4.6p1-5ubuntu0.2                   secure shell client, an rlogin/rsh/rcp repla
ii  openssl                                    0.9.8e-5ubuntu3.1                    Secure Socket Layer (SSL) binary and related
ii  ssl-cert                                   1.0.14                               Simple debconf wrapper for openssl
ii  ttf-mgopen                                 1.1-2                                Magenta Open Truetype fonts
ii  ttf-opensymbol                             1:2.3.0-1ubuntu5.3                   The OpenSymbol TrueType font

Did you already run the apt-get remove statement from post #5?  If no then run it as it will remove all those openoffice.org packages.

---

### Post by al.adab on 2008-04-02
I did run it. I've just run it again. Here's what I get. Is it ok? Please also find what I get if I run * dpkg -l | grep open* again:

-------
~$ sudo apt-get -y remove openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openoffice.org is not installed, so not removed
Package openoffice.org-base is not installed, so not removed
Package openoffice.org-calc is not installed, so not removed
Package openoffice.org-common is not installed, so not removed
Package openoffice.org-core is not installed, so not removed
Package openoffice.org-draw is not installed, so not removed
Package openoffice.org-evolution is not installed, so not removed
Package openoffice.org-filter-mobiledev is not installed, so not removed
Package openoffice.org-gnome is not installed, so not removed
Package openoffice.org-gtk is not installed, so not removed
Package openoffice.org-help-en-us is not installed, so not removed
Package openoffice.org-impress is not installed, so not removed
Package openoffice.org-java-common is not installed, so not removed
Package openoffice.org-l10n-common is not installed, so not removed
Package openoffice.org-l10n-en-gb is not installed, so not removed
Package openoffice.org-l10n-en-za is not installed, so not removed
Package openoffice.org-math is not installed, so not removed
Package openoffice.org-style-human is not installed, so not removed
Package openoffice.org-writer is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
---------
~$ dpkg -l | grep open
ii  libltdl3                                   1.5.24-1ubuntu1                      A system independent dlopen wrapper for GNU 
ii  libmatroska0                               0.8.1-1                              extensible open standard audio/video contain
ii  libmeanwhile1                              1.0.2-3                              open implementation of the Lotus Sametime Co
ii  libopenal0a                                1:0.0.8-4ubuntu2                     OpenAL is a portable library for 3D spatiali
ii  libopencdk8                                0.5.13-2                             Open Crypto Development Kit (OpenCDK) (runti
ii  libopenexr2c2a                             1.2.2-4.3ubuntu2                     runtime files for the OpenEXR image library
ii  libopenspc0                                0.3.99a-2                            library for playing SPC files
ii  lsof                                       4.78.dfsg.1-2                        List open files
rc  openoffice.org-base                        1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - database
rc  openoffice.org-calc                        1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - spreadsheet
rc  openoffice.org-common                      1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite architecture ind
rc  openoffice.org-core                        1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite architecture dep
rc  openoffice.org-draw                        1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - drawing
ii  openoffice.org-hyphenation                 0.2                                  Hyphenation patterns for OpenOffice.org
rc  openoffice.org-impress                     1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - presentation
rc  openoffice.org-math                        1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - equation edito
rc  openoffice.org-thesaurus-en-us             1:2.2.0-2ubuntu1                     English Thesaurus for OpenOffice.org
rc  openoffice.org-writer                      1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - word processor
ii  openprinting-ppds                          20070919-0ubuntu3                    OpenPrinting printer support - PostScript PP
ii  openssh-client                             1:4.6p1-5ubuntu0.2                   secure shell client, an rlogin/rsh/rcp repla
ii  openssl                                    0.9.8e-5ubuntu3.1                    Secure Socket Layer (SSL) binary and related
ii  ssl-cert                                   1.0.14                               Simple debconf wrapper for openssl
ii  ttf-mgopen                                 1.1-2                                Magenta Open Truetype fonts
ii  ttf-opensymbol                             1:2.3.0-1ubuntu5.3                   The OpenSymbol TrueType font

---

### Post by stchman on 2008-04-02
> **al.adab said:**
> I did run it. I've just run it again. Here's what I get. Is it ok? Please also find what I get if I run * dpkg -l | grep open* again:

-------
~$ sudo apt-get -y remove openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openoffice.org is not installed, so not removed
Package openoffice.org-base is not installed, so not removed
Package openoffice.org-calc is not installed, so not removed
Package openoffice.org-common is not installed, so not removed
Package openoffice.org-core is not installed, so not removed
Package openoffice.org-draw is not installed, so not removed
Package openoffice.org-evolution is not installed, so not removed
Package openoffice.org-filter-mobiledev is not installed, so not removed
Package openoffice.org-gnome is not installed, so not removed
Package openoffice.org-gtk is not installed, so not removed
Package openoffice.org-help-en-us is not installed, so not removed
Package openoffice.org-impress is not installed, so not removed
Package openoffice.org-java-common is not installed, so not removed
Package openoffice.org-l10n-common is not installed, so not removed
Package openoffice.org-l10n-en-gb is not installed, so not removed
Package openoffice.org-l10n-en-za is not installed, so not removed
Package openoffice.org-math is not installed, so not removed
Package openoffice.org-style-human is not installed, so not removed
Package openoffice.org-writer is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
---------
~$ dpkg -l | grep open
ii  libltdl3                                   1.5.24-1ubuntu1                      A system independent dlopen wrapper for GNU 
ii  libmatroska0                               0.8.1-1                              extensible open standard audio/video contain
ii  libmeanwhile1                              1.0.2-3                              open implementation of the Lotus Sametime Co
ii  libopenal0a                                1:0.0.8-4ubuntu2                     OpenAL is a portable library for 3D spatiali
ii  libopencdk8                                0.5.13-2                             Open Crypto Development Kit (OpenCDK) (runti
ii  libopenexr2c2a                             1.2.2-4.3ubuntu2                     runtime files for the OpenEXR image library
ii  libopenspc0                                0.3.99a-2                            library for playing SPC files
ii  lsof                                       4.78.dfsg.1-2                        List open files
rc  openoffice.org-base                        1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - database
rc  openoffice.org-calc                        1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - spreadsheet
rc  openoffice.org-common                      1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite architecture ind
rc  openoffice.org-core                        1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite architecture dep
rc  openoffice.org-draw                        1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - drawing
ii  openoffice.org-hyphenation                 0.2                                  Hyphenation patterns for OpenOffice.org
rc  openoffice.org-impress                     1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - presentation
rc  openoffice.org-math                        1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - equation edito
rc  openoffice.org-thesaurus-en-us             1:2.2.0-2ubuntu1                     English Thesaurus for OpenOffice.org
rc  openoffice.org-writer                      1:2.3.0-1ubuntu5.3                   OpenOffice.org office suite - word processor
ii  openprinting-ppds                          20070919-0ubuntu3                    OpenPrinting printer support - PostScript PP
ii  openssh-client                             1:4.6p1-5ubuntu0.2                   secure shell client, an rlogin/rsh/rcp repla
ii  openssl                                    0.9.8e-5ubuntu3.1                    Secure Socket Layer (SSL) binary and related
ii  ssl-cert                                   1.0.14                               Simple debconf wrapper for openssl
ii  ttf-mgopen                                 1.1-2                                Magenta Open Truetype fonts
ii  ttf-opensymbol                             1:2.3.0-1ubuntu5.3                   The OpenSymbol TrueType font

Well, apt-get says it is not installed so it is not installed.  Make sure you remove the residual config from Synaptic.  Proceed.

---

### Post by jcro001 on 2008-04-03
Thanks a million. Those were definitely the best installation instructions that I have seen for any Ubuntu software.

---

### Post by tdmoore on 2008-04-30
I appreciate the help here with OOo and would like to ask for some help.

Updated from 7.10 to 8.04 and cannot for the life of me get OOo JRE to hold.  Have tried all sorts of different things from reinstalling java common to trying stchman's comment of loading JRE 1.5.
Nothing seems to work and will need it I believe in OOo 2.4.

Can anyone assist me?

Have toggled different versions in OOo tools>options>openoffice.org\java but it's almost as if they don't hold inside OOo.

Appreciate a reply...still learning Ubuntu although have been on it for close to a year it works so well I usually don't have to change anything!

Thanks in advance.

---

### Post by calc on 2008-05-03
> **tdmoore said:**
> I appreciate the help here with OOo and would like to ask for some help.

Updated from 7.10 to 8.04 and cannot for the life of me get OOo JRE to hold.  Have tried all sorts of different things from reinstalling java common to trying stchman's comment of loading JRE 1.5.
Nothing seems to work and will need it I believe in OOo 2.4.

Can anyone assist me?

Have toggled different versions in OOo tools>options>openoffice.org\java but it's almost as if they don't hold inside OOo.

Appreciate a reply...still learning Ubuntu although have been on it for close to a year it works so well I usually don't have to change anything!

Thanks in advance.

Remove ~/.openoffice.org2/user/config/javasettings_Linux_x86.xml

I'm not sure why it can't update the old version of the file, it points to an old version of java. If you remove the file and then switch versions of java later it updates properly, so for some reason it just refuses to update the old version of the file from < 2.4.0. :(

---

### Post by tdmoore on 2008-05-04
> **calc said:**
> Remove ~/.openoffice.org2/user/config/javasettings_Linux_x86.xml

I'm not sure why it can't update the old version of the file, it points to an old version of java. If you remove the file and then switch versions of java later it updates properly, so for some reason it just refuses to update the old version of the file from < 2.4.0. :(

Thanks Calc...
I believe the reason for the old file is that I tried following a post just above this that stated 1.5 was more solid.
I have not removed from Ubuntu before..do I just copy and paste the above in a terminal?
Also, I have tried downloading and installing the latest version (believe it is JRE6 Update 5) and having troubles with that too.
Any chance of having you send me the exact terminal instructions (I am really struggling with learning these..) to make it easier?
Not presently at my Linux computer so not a real rush.

Really appreciate the help.  I run Windows on my notebook for work and have been on OOo for over 5 years now (StarOffice before that) and know my way around it for Windows.  Obviously most of the issues for me are that I am not totally comfortable with Linux yet.

Thanks again...Ubuntu support comes through again!

---

### Post by calc on 2008-05-04
> **tdmoore said:**
> Thanks Calc...
I believe the reason for the old file is that I tried following a post just above this that stated 1.5 was more solid.
I have not removed from Ubuntu before..do I just copy and paste the above in a terminal?
Also, I have tried downloading and installing the latest version (believe it is JRE6 Update 5) and having troubles with that too.
Any chance of having you send me the exact terminal instructions (I am really struggling with learning these..) to make it easier?
Not presently at my Linux computer so not a real rush.

Really appreciate the help.  I run Windows on my notebook for work and have been on OOo for over 5 years now (StarOffice before that) and know my way around it for Windows.  Obviously most of the issues for me are that I am not totally comfortable with Linux yet.

Thanks again...Ubuntu support comes through again!

Ok the exact instructions to delete the file from a terminal window is:

```
rm ~/.openoffice.org2/user/config/javasettings_Linux_x86.xml
```

---

### Post by SonicSteve on 2008-05-14
> **stchman said:**
> You can download the Debian package from OO's website.  Use this link to download OO 2.4 for debian.

[http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.0](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.0)

The file is named:

OOo_2.4.0_LinuxIntel_install_en-US_deb.tar.gz

You MUST have a JRE installed for full OO functionality.

You will then need to uninstall the old OO.  To do this use this command in a terminal:

```
sudo apt-get -y remove openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer
```After that remove the residual config in Synaptic.

Now lets assume you downloaded the deb tar.gz to your home folder.

In a terminal:
```

cd ~

tar -vxzf ~/OO*

cd O*

cd DEBS

sudo dpkg -i *.deb

cd desk*

sudo dpkg -i *.deb


```You are now the proud owner of OO 2.4.

Thanks, worked perfectly and it means I can keep Gutsy Gibbon until (hopefully) Hardy has some of it's bugs ironed out.

---

