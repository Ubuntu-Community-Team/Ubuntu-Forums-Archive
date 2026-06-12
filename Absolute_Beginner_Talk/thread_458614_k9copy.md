---
title: "k9copy"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by gaby PR on 2007-05-29
I am unable to start k9copy.  The following error show:

The application k9copy crashe and caused the signal 11 (SIGSEGV)
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1241904496 (LWP 6894)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0x00000000 in ?? ()
#7  0x08071a16 in ?? ()
#8  0x00000000 in ?? ()

---

### Post by kernel tom on 2007-05-30
what version of k9copy are you running, and are still using breezy?

---

### Post by gaby PR on 2007-06-02
I am using Festy 7.04.  In Breezy I had no problem.

k9copy version 1.1.0~beta2-0ubuntu1

---

### Post by gaby PR on 2007-06-10
Come on anybody using k9copy in Feisty that can help me.

---

### Post by p_quarles on 2007-06-10
[COLOR=Black]I'm using the same version of K9copy (under Gnome, no less), and haven't had any problems. Anyway, I have no idea what the problem is, but I did notice under the "about" section that the author asks people to contact him/her about bugs:

k9  copy  (at) free  (dot) fr  [no spaces]
[/COLOR]

---

### Post by gaby PR on 2007-06-12
Thanks for your respond.  Apparently the site is offline because nothing show.  Anybody that can help me?  I remove and install again but the same problem show and I have all the dependecies install also.

---

### Post by gaby PR on 2007-06-20
Come on anybody that can help me.

---

### Post by p_quarles on 2007-06-20
Still no luck, huh?

I don't know how you installed it, but if you used dpkg you might not have all the dependencies. If you're using Gnome (as it suggests in your profile) you need the KDE libraries. Installing it through synaptic would be best, but I'm guessing you've already tried that.

In any case, you could also try dvd95. Similar program designed for the Gnome libraries.  Sorry I can't be of more help, but I have no idea how to debug it.

---

### Post by SadaraX on 2007-06-24
I had some troubles using K9copy just recently. I tried a few things and I think one of them worked. I compiled the latest source files of DVDAuthor, which I think was the key to my problem, though it is not the same as yours. 

I know that k9copy requires all of the following to be compiled from source itself, therefore some of these might still be required to run it, even though downloading the program from APT is normally good at handling which dependencies you need. 

libdvdread3
libdvdnav
libhal (either libhal1 or libhal-storage1)
libdbus-qt-1
vamps

I was missing vamps for some reason, and like I said I compiled the latest DVDAuthor source files and now things seem to be working well.

---

