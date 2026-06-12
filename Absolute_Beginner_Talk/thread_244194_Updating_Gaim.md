---
title: "Updating Gaim"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by s1k3st on 2006-08-26
I'm still pretty new to linux, so try to take it easy on me.  I would like to update gaim to the newest version because I haven't been able to connect lately and I read somewhere that the new version fixes this.  The problem is that it's not updated in the apt repo's (I think this is the problem anyway).  So, how would I go about updating?  It would be nice if there is a .deb package available, but I haven't had any luck finding one.  I would also like to update azureus because of the stupid warnings that don't go away,  just thought I might aswell mention that since it's kinda related.  Any help will be greatly appreciated.

---

### Post by elettronicha on 2006-08-26
Which is the newer version you're talking about? Have you enabled the correct repos?
PS: try reading about synaptic and the repos on the official documentation. :)

---

### Post by s1k3st on 2006-08-26
The newest is Gaim 2.0.0beta3.1  I'm pretty sure that I got the right repos setup (using the ones on [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)).  I know how to use synaptic but the new version isn't shown.  I figured out how to update azureus so just ignore that.

---

### Post by masnevets on 2006-08-26
[http://sourceforge.net/project/showfiles.php?group_id=235](http://sourceforge.net/project/showfiles.php?group_id=235)

You can either download the .rpm and use alien to convert it to a .deb, or you can download the source and compile it yourself from the terminal:

./configure
make
sudo make install

The beta won't be in the repositories since only stable software gets in there.

---

### Post by s1k3st on 2006-08-26
I tried to install it from the .rpm but it doesn't work.  Says this "error: current build architecture i386 does not appear in package's list (amd64)".

---

### Post by nospam on 2006-08-27
I'm also trying to do the same thing.

I've downloaded the gaim source, got pkg-config and the gtk dev headers needed to compile.

After doing ./configure and make install successfully... the question now is, *drumroll for possibly the most noob question ever* where did the compiled file go? 8-[ 

I tried a locate gaim but after going through the long list (sidetrack: how to I make it grep only /gaim and ignore things like /gaim/ and /gaim.src?) I still only have the older versions of gaim, going by the date on the files.

Thanks for any suggestions!

---

