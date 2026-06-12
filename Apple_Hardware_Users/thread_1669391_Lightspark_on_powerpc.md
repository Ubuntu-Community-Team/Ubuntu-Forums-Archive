---
title: "Lightspark on powerpc"
date: 2011-01-17
forum: Apple Hardware Users
---

### Post by rsavage on 2011-01-17
Hi all,

Just wondering if anybody has tried lightspark (the new open source flash player) on a powerpc yet? 

I've managed to compile and install it on a late 2004 G4 ibook (1.2Ghz, 12" 9200 radeon mobility) running ubuntu 10.10 (maverick).  However, when I go to a website with flash the browser just closes.  When I try the standalone package (using the test suggested in [http://sourceforge.net/apps/trac/lightspark/wiki/Troubleshooting](http://sourceforge.net/apps/trac/lightspark/wiki/Troubleshooting)) I get the error "problem in t_src_class" and again the test window just closes.

A bit of googling and this error seems to be associated with the open source mesa drivers for radeon cards.  A bit more googling and it seems the radeon drivers have been problematic with lightspark.  The suggested fix is to use Mesa 7.8.2 or better.  I have 1.3 Mesa 7.9-devel courtesy of the update to maverick.  What I'd really like to know is if anybody has got lightspark working and what version of mesa they are using?  I'm wondering if people with 10.04 lucid will have more luck as graphics seemed seemed less troublesome in that version. 

For those interested in trying lightspark the web page you need is [http://sourceforge.net/apps/trac/lightspark](http://sourceforge.net/apps/trac/lightspark).  The release 0.4.5.1 is the version with ppc support.

I've only been using linux for 3 months and less than 1 month on my ibook (it was a recent ebay purchase) so I don't really know what I'm doing or understand it all.  I followed the instructions for installing from source which is on the page [http://sourceforge.net/apps/trac/lightspark/wiki/Building](http://sourceforge.net/apps/trac/lightspark/wiki/Building).  I'm currently trying to review if I did anything wrong.  My first query is should I have run "*git clone git://github.com/lightspark/lightspark.git lightspark*"?  It says it installs the "bleeding edge code for lightspark" and I'm wondering now if it is has installed an unstable version beyond 0.4.5.1.  I repeat I don't understand what things do!

I installed the list of packages on the bottom of the web page.  The command "*cmake -DCMAKE_BUILD_TYPE=Release -DCOMPILE_PLUGIN=1 -DCMAKE_INSTALL_PREFIX=/usr .. *" wanted more packages and I installed them to satisfy it.  I compiled and installed the latest version of libxml++2.6 from here [http://libxmlplusplus.sourceforge.net/](http://libxmlplusplus.sourceforge.net/) (following the instructions on the INSTALL file).  Other packages I remember needing are libboost-dev and libboost-filesystem-dev which I just did normally.

Experimenting a bit I can get lightspark to run by omitting "*radeon.modeset=0*" from the yaboot.conf.  This causes the software rasteriser to be used, but nothing sensible appears on a youtube video or on the test swf.  This is not surprising as performance generally is rubbish when ubuntu is run like this (i think most comments on this forum about ubuntu being slow can be tracked down to not having this option in their yaboot.conf). 

I'd encourage all powerpc users to try out lightspark and support its developers.  You may have better luck than I have!  Afterall, powerpc users are surely going to have the most to gain from the development of a modern open source flash player.  Flash is going to be around for a while yet!!!

One final thing though, since it isn't working for me I'd now like to know how to uninstall it!  Can anybody give me instructions??!!?!

Cheers 

Adam

---

