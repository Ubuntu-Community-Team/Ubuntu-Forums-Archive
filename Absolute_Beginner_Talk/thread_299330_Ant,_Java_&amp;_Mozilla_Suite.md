---
title: "Ant, Java &amp; Mozilla Suite"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by cymoril on 2006-11-14
Hello everyone. I'm running Breezy and I'm trying to get a program called Metis to run.

[http://optusnet.dl.sourceforge.net/sourceforge/metis-rs/metis-3.0.1-linux.tar.gz](http://optusnet.dl.sourceforge.net/sourceforge/metis-rs/metis-3.0.1-linux.tar.gz)

The README file tells me that I have to build Metis from Source.

It goes on to say that I would need Ant Apache and Java JDK 1.5 installed.

I installed Ant using Synaptic and the JDK following the instructions given on the Ubuntu Java Wiki.

This is my problem:

When I switch to the directory where I've extracted the source code and type: 'ant all' as stated in the README file, I receive this error:

Buildfile: build.xml does not exist!
Build failed

How do I fix this?

The README file also states that:

"If you are attempting to run Metis from source using the above target and you are using Linux as your operating system, you must have the
MOZILLA_FIVE_HOME environment variable set.  This must be a valid
Mozilla Suite library path that contains the libxpcom.so file.  Note
that Firefox will not be compatible, you must have the Mozilla Suite
installed instead."

I don't have the Mozilla Suite yet ( I'm just using Firefox ) and I don't know how to set the five home environment. I don't know the path to libxpcom.so either ( Does this file come with the Java I've installed? )

How do I install the Mozilla Suite on Breezy and make the relevant changes as described in the README?

And how do I get "Ant all" to work?

Please help!

Thanks,
Cymoril.

---

### Post by polly1 on 2006-11-14
Hi

I have no idea how to help without trying to install myself, but a quick search on Synaptic for metis produced two results-  r-cran-matrix and xwnc- which appear similar to the software you are after.

Perhaps you may like to try these to see if they are what you want, because installing from source does appear to be overly complicated.

---

