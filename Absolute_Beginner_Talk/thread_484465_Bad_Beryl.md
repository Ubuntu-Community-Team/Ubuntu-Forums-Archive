---
title: "Bad Beryl"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by drakeskywing on 2007-06-25
Hey, i am trying to install beryl on feisty fawn, and i am not installing off the ubuntu repositories because of issues i have had with it and compatibility, as well a friend of mine warned me against it. So i have been trying to install off beryl-projects website but found all the packages a little overwhelming. 
I downloaded the beryl - core - 0.2.1.tar.bz2, and i tried to run the configure file, though it  gives me this error when i install:

checking for xgettext... /usr/bin/xgettext
checking whether byte ordering is bigendian... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBBERYLDECORATION... configure: error: Package requirements (xrender >= 0.8.4) were not met:

No package 'xrender' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBBERYLDECORATION_CFLAGS
and LIBBERYLDECORATION_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

----------------------------------------------------------------------------------------------------------------------

The man page of the pkg-config command is also leaving me at a blank

---

### Post by cogadh on 2007-06-25
Why don't you download the .deb from the Beryl site instead? They already have a pre-configured package that is not the same as the one from the Ubuntu repositories:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

---

