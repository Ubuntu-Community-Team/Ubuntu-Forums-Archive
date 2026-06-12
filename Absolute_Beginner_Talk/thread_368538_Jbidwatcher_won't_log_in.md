---
title: "Jbidwatcher won't log in"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by BirdZerk on 2007-02-23
I've had tried to get Jbidwatcher to log in unsuccessfully, the threads I have read are dated last year, so something has changed with the way ebay logs in.  I found some information about updating java to 1.6, but the problem still persists.  I am running xubuntu 6.10.  Is there anyone currently using jbidwatcher that knows how to fix the log in problem.

---

### Post by stani on 2007-02-23
I am afraid the author of jBidwatcher is too angry about this story:
[http://www.jbidwatcher.com/snipeit.shtml](http://www.jbidwatcher.com/snipeit.shtml)

So unless someone familiar with java and the new login rules pick up the software, it won't work.

I haven't looked for a good alternative. Anyone knows?

Stani

---

### Post by BirdZerk on 2007-02-23
I have found esniper and bidwatcher, neither one will run at the moment, but I keep trying.  When I follow the install directions with esniper, it says to
 ```

./configure
make
make install

```
when I run ./configure I get the error
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether make sets $(MAKE)... (cached) yes
checking for curl-config... no
configure: error: curl-config not found.
cURL is available from http://curl.haxx.se/

```
I installed curl thru synaptic, anyone have an idea?

---

### Post by mbaker514 on 2007-05-02
Try this. It works for me just fine.

Go to [http://www.jbidwatcher.com/#news](http://www.jbidwatcher.com/#news)

Download the java binary to your home folder.

Use the command     java -Xmx512m -jar JBidWatcher-1.0.1.jar    in a terminal to see if it works for you.

If it doesn't, then you probably have a java problem. You could try reinstalling it, or completely uninstall and then reinstall it again.

The only thing I found that was a little strange was configuration of the browser. The test browser function didn't want to work properly. I just typed in firefox as my browser, marked override detected browser and saved it.
The test browser function says I had a problem, but when I right clicked on an item and clicked show in browser, it worked fine. Be sure you have configured your Ebay ID and password, also.

Hope this works for you. If it does, just create a launcher for it on the desktop, or add it to your taskbar or menu, whichever makes you smile.

---

### Post by BirdZerk on 2007-05-04
I thought Ebay changed some kinda of settings periodically which would disable Jbidwatcher since it has not been worked on in a while.

---

### Post by mbaker514 on 2007-05-04
The link I posted is to the newest version. Just sniped a laptop yesterday on Ebay using the current Jbidwatcher.

---

