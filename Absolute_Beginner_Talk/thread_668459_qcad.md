---
title: "qcad"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by amongo on 2008-01-15
I'm trying to install Qcad and am having trouble opening download am a complete  noob don't know any thing about running stuff on linux all help would be appreciated.

---

### Post by MrKlean on 2008-01-15
I would use the Synaptic Program Manager... go to System..Administration...Synaptic...and search for Qcad.and install from there ; )

---

### Post by OffAxis on 2008-01-15
> # The demo version terminates after 10 minutes.
# It can be restarted and used for 100 hours in total
so that's 60 dropped sessions and restarts. ouch.

There are alternatives out there to this program, especially in the 2D world of linux CAD. Just google it.


Otherwise, you just need to gunzip, untar
```
gunzip qcad-2.1.3.2-1-demo.linux.x86.tar.gz
tar -xvvf qcad-2.1.3.2-1-demo.linux.x86.tar

```

and then navigate into the folder you just created
```
cd qcad-2.1.3.2-1-demo.linux.x86/
```
and start the script with 
```
sh qcad_demo
```

There is a qcad in the repos, but I'm not sure if it's the same as this program (I'm guessing not).

---

### Post by VON_CAPO on 2008-01-15
QCAD "Community Edition" is not a demo= ---> qcad_2.0.5.0-1-2ubuntu1_i386.deb
---> [http://packages.ubuntu.com/gutsy/graphics/qcad](http://packages.ubuntu.com/gutsy/graphics/qcad)

Also you can download the addons:

1)  The "Documentation package" ---> qcad-doc_2.0.5.0-1-2ubuntu1_all.deb
---> [http://packages.ubuntu.com/gutsy/graphics/qcad-doc](http://packages.ubuntu.com/gutsy/graphics/qcad-doc)

2)  The "Parts library package" ---> partlibrary_2.0.1.2-1-2_all.deb
---> [http://packages.ubuntu.com/gutsy/graphics/partlibrary](http://packages.ubuntu.com/gutsy/graphics/partlibrary)

---

### Post by amongo on 2008-01-15
thanks, will try later, gotta go to work ,

---

