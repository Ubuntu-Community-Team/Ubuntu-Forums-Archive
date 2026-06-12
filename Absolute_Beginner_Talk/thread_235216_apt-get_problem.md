---
title: "apt-get problem"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by mikkol on 2006-08-12
Hello,

I just installed the sun-java package using Synapitic. There was an error (net lag I suppose) during the download  of the documentation part of the install, and it failed. Since then, whenever i call "apt-get" or invoke Synaptic for whatever reason, I get this:

> 
Setting up sun-java5-doc (1.5.0-06-1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] dpkg: error processing sun-java5-doc (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Setting up jpeg2ps (1.9-1) ...


It happens now always. Whenever "apt-get" is called, or if I update something throug Synaptic.

How I*m supposed to correct the situation? Thank you for your concern.

[edit] Oh, just to be more precise, I have followed the instructions of the error message. It just seems that downloading the Japanise language doc zip file (I'm not Japanese and I never asked for the docs in Japanese language) 
 is impossible. So, how to circumvent the apt-get error message from now?

[edit2] Problem resolved. Managed to download the required file, put it in the required location, and did apt-get install something to invoke the remaining tasks. Now, everything wors as previously.

---

