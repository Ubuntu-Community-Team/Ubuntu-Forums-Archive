---
title: "Amarok - Collection scan aborted"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by U5tabil on 2007-04-10
I got an error while the collection scan was going. It says:

Sorry, the Collection Scan was aborted, since too many problems were encountered.

Advice: A common source for this problem is a broken 'TagLib' package on your computer. Replacing this package may help fixing the issue.
The following files caused problems:

And then it just rams up some music files, but they work if i play them one by one.

Anyone know whats wrong? how i can fix this problem? know how to replace the "taglib" ?

Thanks

---

### Post by koshari on 2007-04-10
this was a bug in some of the earlier versions of amarok and generally occurs while scanning a collection from a remote drive via cifs or samba due to the asci coding of the filename. 

i suggest you upgrade amarok to 1.4.5 and you should have no problems ith it aborting, instead it will give you a list of the offending files, 

i are assuming you are running a version of amarok earlier than 1.4.5?

---

### Post by U5tabil on 2007-04-10
i am running amarok 1.4.3 :confused:

and when i install it with "sudo apt-get install amarok" it installs it with 1.4.3 :confused: 
I am not good with this. Do you know how i can get the newest version?

---

### Post by koshari on 2007-04-10
what version of ubuntu are you running?

---

### Post by U5tabil on 2007-04-10
i am running ubuntu 6.10 waiting for the new release 17 this month :)

---

### Post by koshari on 2007-04-11
ok , then all you need to do is add the jonathan riddel repo through synaptic,

deb [http://kubuntu.org/packages/amarok-145](http://kubuntu.org/packages/amarok-145) edgy main

and then enter the gpg key,

 ```
wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
sudo apt-key add kubuntu-packages-jriddell-key.gpg
```

 then auto updates should upgrade to 1.4.5.

below is a link with more info

[http://kubuntu.org/announcements/amarok-1.4.5.php](http://kubuntu.org/announcements/amarok-1.4.5.php)

---

### Post by U5tabil on 2007-04-11
> **koshari said:**
> ok , then all you need to do is add the jonathan riddel repo through synaptic,

deb [http://kubuntu.org/packages/amarok-145](http://kubuntu.org/packages/amarok-145) edgy main

and then enter the gpg key,

 ```
wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
sudo apt-key add kubuntu-packages-jriddell-key.gpg
```

 then auto updates should upgrade to 1.4.5.

below is a link with more info

[http://kubuntu.org/announcements/amarok-1.4.5.php](http://kubuntu.org/announcements/amarok-1.4.5.php)

Hey that worked! Thank you so much. i need to place this as a favorite for the next time...

---

