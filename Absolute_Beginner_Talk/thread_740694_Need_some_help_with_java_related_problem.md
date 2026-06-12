---
title: "Need some help with java related problem"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by BossGreen on 2008-03-31
whenever i try to install or remove anything, I get this message.

```
Setting up sun-java6-doc (6-03-0ubuntu2) ...
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

how do i make it go away?

---

### Post by kpkeerthi on 2008-03-31
If you don't have a need for javadoc for sun java sdk 6, you can simply uninstall it using ```
sudo apt-get remove sun-java6-doc
```.

Otherwise, download the zip file, copy it to /tmp... basically follow the rest of the instructions.

---

### Post by BossGreen on 2008-03-31
i want to get rid of it and when i tried that command line, it spit this out.

```
root@Nicholas:~# sudo apt-get remove sun-java6-doc
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

when i type in 

```
dpkg --configure -a
```

i get the same error message i put in the first post.

---

### Post by Inxsible on 2008-03-31
Put a sudo in front of the dpkg command and try again

---

### Post by BossGreen on 2008-03-31
i tried putting sudo in front of the command and this is what i got

```
root@Nicholas:~# sudo dpkg --configure -a
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort
```

any further suggestions would be appreciated

---

### Post by BossGreen on 2008-03-31
anyone?

---

### Post by rkd on 2008-03-31
I haven't had that problem, but I did a little web searching and found something that might help:

```
sudo dpkg --remove --force-remove-reinstreq sun-java6-doc
```

Notice there are two hyphens before each of the keywords, not just one hyphen.

---

### Post by cozmicharlie on 2008-03-31
Did the suggestion by rkd work?  What is happening is you have a screwed up package that did not install correctly.  If the suggestion by rkd does not work go into Synaptic>edit>fix the broken package and run fix broken package.  After, that is completed you can go back in and uninstall the package from Synaptic.  I had a similar problem not too long ago and this worked for me.

---

### Post by BossGreen on 2008-03-31
i tried both of them, but the error message keeps popping up, but i can still install stuff.

---

### Post by Inxsible on 2008-03-31
Go to the Synaptic Package manager and click on Custom Filters on the bottom left corner. Then click on Broken on the top left and then it should show the java doc folder on the right. Right click on it and select MArk for complete removal. Hit apply and see if that works.

---

### Post by BossGreen on 2008-03-31
Awesome, you guys are great.

i no longer have that problem, and everything is as it should be.

kudos to all.  :D

---

### Post by Inxsible on 2008-03-31
> **BossGreen said:**
> Awesome, you guys are great.

i no longer have that problem, and everything is as it should be.

kudos to all.  :DGreat.  Please mark your thread solved.

---

