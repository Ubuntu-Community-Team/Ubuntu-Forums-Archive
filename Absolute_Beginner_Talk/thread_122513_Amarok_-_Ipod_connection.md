---
title: "Amarok - Ipod connection"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by Kid G on 2006-01-27
Hi,

I am using the SVN version of Amarok, which allows me to play my Itunes Music Library but will not communicate with my (3G) Ipod. 

When I select "connect" from the Media Device menu a dialog window promts me to Configure Media Device with the option "Transcode before transferring to device" but the only option available is "Disable". The Manage Media Plugins Dialog box also only allows me to select "Do not handle".

Any ideas on how I can get the two to communicate correctly?

Thanks

---

### Post by Kid G on 2006-01-29
Bump

I've tried to install Libgpod but I get this message when I use the make command:

[I][INDENT]gary@ubuntu:~/libgpod-0.3.0$ make
make: *** No targets specified and no makefile found.  Stop.
gary@ubuntu:~/libgpod-0.3.0$ sudo checkinstall -D make install[/INDENT]
[/I]
The configure command seems to work up to this point:

*[INDENT]checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool[/INDENT]*

Any ideas?

Thanks

---

### Post by wondering_jew on 2006-02-06
[QUOTE=Kid G]
The configure command seems to work up to this point:

*[INDENT]checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool[/INDENT]*

[/QUOTE]
For the missing module do

```
sudo apt-get install libxml-parser-perl
```

Once you have this perl module go back to the libgpod directory and
```
./configure
make
sudo make install
```

It should work now...
On a side note I posted this solution in another thread a while back you prolly would have found it if you searched for libgpod...its currently on the 3rd page of  the 4th thread on the list when you search... just a reminder to search the forums before starting a new thread ;)

---

