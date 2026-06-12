---
title: "Problems installing Beryl on iMac G5 w/ Edgy"
date: 2007-03-28
forum: Apple PPC Users
---

### Post by Snake2582 on 2007-03-28
I can't get Beryl installed for the life of me. When I go through the steps on Beryl's Wiki, it all works fine until I have to apt-get install beryl. It doesn't want to install.
This is what I get:
```
root@matt:~# apt-get install beryl

Reading package lists... Done

Building dependency tree Reading state information... Done

Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against that package should be filed. The following information may help to resolve the situation:

The following packages have unmet dependencies:

    beryl: Depends: beryl-core but it is not going to be installed

        Depends: libberylsettings0 but it is not going to be installed

        Depends: beryl-plugins but it is not going to be installed

        Depends: beryl-settings but it is not going to be installed

        Depends: emerald but it is not going to be installed or

            aquamarine but it is not going to be installed or heliodor but it is not going to be installed or compiz-gtk but it is not installable

        Depends: beryl-manager but it is not going to be installed

E: Broken packages 
```

I have already apt-get updated and apt-get upgraded prior to installing Beryl.

This is what I get when I try to install just Beryl-Core

```
root@matt:~# apt-get install beryl-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  beryl-core: Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is to be installed
E: Broken packages
```

It won't let me upgrade libc6 and it's getting very frustrating. Can somebody please help me?

---

### Post by ssam on 2007-03-29
beryl is not in the official repos for edgy, so i guess you must be using a 3rd party repo. does it have powerpc packages?

you might want to wait a few weeks for feisty which has beryl in the official repos. (or you can try the feisty beta, but you should probably not install it on a production machine yet)

---

### Post by stmiller on 2007-03-29
There are no real stable 3D drivers for PPC Linux. 3D support is unstable, at best. If you can get it working. So no 3D effects. No 'stable' 3D effects, that is.

Nvidia and ATI have never made any PPC Linux drivers, nor released hardware info to the community so open source drivers could be made.

:(

---

