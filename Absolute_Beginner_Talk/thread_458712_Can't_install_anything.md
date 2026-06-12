---
title: "Can't install anything"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-05-29
Hey. After having some problems with java... i reformatted my ubuntu drive and reinstalled.

after 2 days, my problem is back

basically, whenever i do anything to install or update ANYTHING (even sudo dpkg --configure -a)

i get this message

```

mykola@MykolaUbuntu:~$ sudo dpkg --configure -a
Setting up sun-java6-doc (6-00-2ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 



```

when i press return, it just loops. when i type no it gives me this

```

Abort installation of JDK documentation
dpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-doc

```

I've gone to the sun website and i've downloaded that file... i even extracted it into temp and changed the owner to root.


what else can I do?! 

it's driving me insane.

---

### Post by Tyke91 on 2007-05-29
so i guess there is nothing that i can do at all?

this has pretty much broken my computer...

---

### Post by Ek0nomik on 2007-05-29
Out of curiosity, what do you need the file for?

---

### Post by Tyke91 on 2007-05-29
that's the thing... i didn't really need it. 

the computer seems to want it after you install things with java6... i think its a bug that sun microsystems has yet to figure out..



the best solution that i have found is to use synaptic to un install everything to do with java 6 and just use java 5

---

### Post by zvacet on 2007-05-30
Install that application with synaptic.All you have to do is accept licence agreement.Because of that app refuse to install.

---

