---
title: "Installing Text::CSV_XS"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by bblackmore on 2007-06-21
I need to install Text::CSV_XS and Image::Size (and probably a few more before I am done) but have not been able to successfully do so. Runs for a bit then I get:
Checking if your kit is complete...
Looks good
Writing Makefile for Text::CSV_XS
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible

I have managed to install some stuff. When I needed LWP::Simple, I found I needed to install as:
apt-get install libwww-perl.

Perhaps there is something else I need to install to get Text::CSV_XS

Can anyone help?

---

### Post by jrib on 2007-06-27
libtext-csv-perl and libimage-size-perl are both in [universe]("https://help.ubuntu.com/community/Repositories")

---

### Post by bblackmore on 2007-07-07
My problem is not how to install something on Linux, I have installed several things on this server but some packages elude me. I did not reply to this thread before because I could not use the solution given and I found a way forward without installing Text::CSV_XS and Image::Size. However I have the same problem now with Mime::Lite.
I have been asked to set some stuff up on a server to which I have remora access via SSH. I do not know how to access the desktop from there to use the solution given. I have used apt-get to install Apache2, ftp, exim and other things successfully.I have discovered that some of the problem is the actual naming of packages, that is I found stuff in a forum yesterday that pointed out that ubuntu only uses lower case in package names. I tried apt-get install libtext-csv-perl but got the same response "Couldn't find package libtext-csv-perl"
So what I think I need is the name of the packages for apt-get or a way to access the desktop from the command line
Any more advise welcome

---

### Post by bblackmore on 2007-07-08
Since my previous post I have been researching and experimenting. Found that I could install libmime-perl but although that appeared to go okay I still get "Can't locate MIME/Lite.pm..." when I use MIME::Lite; in a perl program.

---

### Post by bblackmore on 2007-07-09
Eventually found that my problem was the apt was not looking in the universe for stuff. Found this article [http://www.us.debian.org/doc/manuals/apt-howto/ch-basico.en.html](http://www.us.debian.org/doc/manuals/apt-howto/ch-basico.en.html) and followed the instructions for editing the apt configuration file. Within minutes I had searched for and found all 3 packages I was missing.

---

### Post by jrib on 2007-07-10
Sorry, I mentioned Universe in my previous post, but I should have made it clearer that you may need to enable it.  There are plenty of good Ubuntu-specific docs at help.ubuntu.com.  For universe, see: [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories).  Glad you sorted it out though!

---

