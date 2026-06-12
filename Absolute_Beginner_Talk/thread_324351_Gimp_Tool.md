---
title: "Gimp Tool"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by Brightrock on 2006-12-23
Hi,

I'm trying to install the great GIMP dcamnoise plugin and when I try to install the synaptic package that contains "gimptool" I get this error message.

libgimp2.0-dev:
  Depends: libgimp2.0 (=2.2.13-1ubuntu1) but 2.2.13-1ubuntu3 is to be installed
 Depends: libgtk2.0-dev but it is not going to be installed

Is there a way to work around this?  Anyone else already install dcam noise?

Thanks,

BR

---

### Post by riven0 on 2006-12-23
> **Brightrock said:**
> Hi,

I'm trying to install the great GIMP dcamnoise plugin and when I try to install the synaptic package that contains "gimptool" I get this error message.

libgimp2.0-dev:
  Depends: libgimp2.0 (=2.2.13-1ubuntu1) but 2.2.13-1ubuntu3 is to be installed
 Depends: libgtk2.0-dev but it is not going to be installed

Is there a way to work around this?  Anyone else already install dcam noise?

Thanks,

BR

Try this instead:

> sudo apt-get install libgtk2.0-dev libgimp2.0 libgimp2.0-dev

Then reinstall the plugin and see if it works.

---

### Post by Brightrock on 2006-12-23
Thanks for the quick response.  I'm afraid it didn't work.  Here's what I get this time.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgimp2.0 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgimp2.0-dev: Depends: libgimp2.0 (= 2.2.13-1ubuntu1) but 2.2.13-1ubuntu3 is to be installed
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.10.6-0ubuntu1) but 2.10.6-0ubuntu3 is to be installed
                 Depends: libpango1.0-dev (>= 1.12) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.2.0) but it is not going to be installed
E: Broken packages

Good news is that Ubuntu seems to have stopped freezing and crashing for me, at least for the moment.

BR

---

### Post by riven0 on 2006-12-23
> **Brightrock said:**
> Thanks for the quick response.  I'm afraid it didn't work.  Here's what I get this time.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgimp2.0 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgimp2.0-dev: Depends: libgimp2.0 (= 2.2.13-1ubuntu1) but 2.2.13-1ubuntu3 is to be installed
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.10.6-0ubuntu1) but 2.10.6-0ubuntu3 is to be installed
                 Depends: libpango1.0-dev (>= 1.12) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.2.0) but it is not going to be installed
E: Broken packages

Good news is that Ubuntu seems to have stopped freezing and crashing for me, at least for the moment.

BR

Alright, looks like you've got a dependency problem. Try going to System >> Administration >> Synaptic Package Manger

Once it loads go to Custom Filters and then check for packages listed under Broken. Try to repair them. 

If not we'll have to try something else.

---

### Post by Brightrock on 2006-12-23
I checked in Synaptic and there are no packages that are marked as broken.  Now what?

Thanks,

BR

---

### Post by lancerocke on 2008-03-10
bump

---

