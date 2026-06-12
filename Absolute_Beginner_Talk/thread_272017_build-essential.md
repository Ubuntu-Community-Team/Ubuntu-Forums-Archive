---
title: "build-essential"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by jcrnan on 2006-10-05
Is there any way of installing buildessential without internet acsess? Like downloading a deb file or such? I have internet on the windows partion but I need ndiswrapper on the other and therefor also build-essential. Any ideas?

---

### Post by SoggyCornflake on 2006-10-05
You can download the individual packages you need, and then install them using dpkg from the command line.

First goto [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") and search for build-essential.  It's entry will include the required packages you need.  compare that list to what you've installed already, and download the individual packages you need.

Install them from a command line with to the following command:

[INDENT]sudo dpkg -i foo.deb[/INDENT]

You will need to do this to each package you download and make sure to do the ones that required for other packages you're installing first.

Hope that helps.

---

### Post by cstudent on 2006-10-05
build-essential is on the dapper cd. If you pop it in and search the disk, you'll see it.

---

### Post by ronmarley1 on 2006-10-05
EDIT: Beat to the punch again.  Sorry for the duplicate.

Isn't build-essential and ndiswrapper on the install cd?  I might be wrong, but I thought they were.  You can enable Synaptic to use the CD to install stuff by opening Synaptic and then clicking on Settings >Repositories.  Click the button that reads "Add Cdrom" and the search for build-essential and ndiswrapper and install them.

---

### Post by aysiu on 2006-10-05
*build-essential* and *ndiswrapper-utils* are on both the Desktop CD and the Alternate CD.

---

### Post by Nhatz on 2006-10-06
yo... you can install ot via your live cd.....
put the live cd in your drive then open synaptic...
hope this help.....:D

---

