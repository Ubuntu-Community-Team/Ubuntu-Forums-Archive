---
title: "Cache problem?"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by blasteryui on 2008-03-10
After having a BS problem with Java I think I finally got Java to work, so I went to runscape, and tried it out, and I looked at the left corner it said, Applet loading, applet loaded, then this came up.
What should I do?

Error_loader_nocache - Unable to create cache directory.
Runescape was unable to find a suitable place to store its temporary files. To solve this please either:

# Login to your computer as an 'administator' user, and then try loading RuneScape again. This should give it sufficient access to create its temporary cache.

# Or, create a new directory called c:/rscache or /rscache. If possible, set that directory to have full read+write permissions so that all users can write to it. Runescape should then detect that directory and use it for its files.

# If you are unable to do either of the above, then as a last resort you can tell RuneScape not to store any files on the harddisk. When entering the site and choosing between high-detail/low-detail also select 'Unsigned Applet Using Default Java' from the dropdown scroll at the bottom of the detail select page. You will need to do this everytime you load the game. The disadvantage of this is the game will load slower, so if possible use one of the top two solutions instead.

If problems persist then please refer to our technical FAQ which can be found in the FAQ section of our website.

---

### Post by handydan918 on 2008-03-10
Looks like a really inelligent error message. It tells you how to fix it.

> # Or, create a new directory called ... /rscache. If possible, set that directory to have full read+write permissions so that all users can write to it. Runescape should then detect that directory and use it for its files.

In other words....
```

mkdir rscache
chmod 666 rscache 
```

---

### Post by blasteryui on 2008-03-11
> **handydan918 said:**
> Looks like a really inelligent error message. It tells you how to fix it.



In other words....
```

mkdir rscache
chmod 666 rscache 
```

Sorry I am a little new, what do I do with the code that you provided me?

---

### Post by handydan918 on 2008-03-11
Open a terminal and either type it in or copy and paste it in.The terminal is one of your menu items, sorry  I don't remember which...I'm in KDE ATM.

---

### Post by rakzor on 2008-03-11
I have the same problem and I mkdir'd /rscache and set full read write permissions but it still gives me the error.

---

### Post by StR34k on 2008-04-14
Same problem here, I've created the 'rscache' (under / and /home/$USER/) making sure that both are chmod 666, and still getting the error.


****UPDATE****

Selecting the unsigned version using default java works.... but this doesn't seem to do any caching, as both rscache directories are empty....

---

### Post by theWrkncacnter on 2008-04-18
Ugh this happens for me too. I am wondering whether it is a Java issue...

---

### Post by codeslicer on 2008-04-19
Yep, this started happening recently after some updates I did... I might purge and reinstall Java.

---

### Post by codeslicer on 2008-04-19
I solved the problem! Don't know if this will work with firefox64 though, but after reading this thread: [http://ubuntuforums.org/showthread.php?p=4746060](http://ubuntuforums.org/showthread.php?p=4746060) the post by wyrless2002, it appears that the IcedTea and GCJ Plugins don't seem to work correctly with RuneScape. To solve this I removed the icedtea-* and gcjwebplugin* packages. Then I had the sun-java6-plugin and its dependencies installed. This solved the problem, and hopefully it will solve yours!

---

### Post by theWrkncacnter on 2008-04-19
Darn -- amd 64 doesn't have the sun java binaries. I can try reinstalling the ones I have though, I don't think it will work.

---

