---
title: "maxwell render and ubuntu"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Scummy007 on 2007-05-28
ok, im trying to set up a render farm at work. 
want to use ubuntu and maxwell just released a linux version of the render
anyone know how to or has already installed this program and has a how-to on it?

cheers

---

### Post by antonyant11 on 2008-02-19
I just downloaded a trial version these are the instructions maxwell emailed me.

They seemed to work fine.

linux:
#  Maxwell64 comes packaged in a tar.gz package.

Installing tar.gz (This example assumes that you are going to install Maxwell64 in the /opt folder)

   1. Copy maxwell64-1.6.xxxx.tar.gz to /opt (where xxxx can be fc5, fc6 or co42)
   2. Type: gzip -d maxwell64-1.6.xxxx.tar.gz
   3. Type: tar xvf maxwell64-1.6.xxxx.tar
   4. Maxwell64 is now installed in /opt/maxwell64
   5. Update the PATH environment variable to point to the Maxwell installation folder. Depending on your shell, the procedure may differ slightly.

      For example, in Bash shell use:
      - export PATH=”/opt/maxwell64/:”

      In csh shell:
      - setenv PATH ”/opt/maxwell64:”

To start MXCL or MXST, use the scripts startmxcl and startmxst located in the Maxwell64 installation folder. These scripts set the environment for MXCL and MXST to run properly.

We provide 3 versions of Maxwell Render for Linux 64, depending on the glibc version of your system. Maxwell Render is available for glibc 2.3.4 (co42), glibc 2.4 (fc5) and glibc 2.5 (fc6). You can get your glibc version by typing this in a command line: strings  /lib/libc.so.6 | grep glibc
 
* We recommend that you uninstall any previous Maxwell Render version before you install Maxwell Render 1.6. If you have questions regarding the software installation please contact us at [http://www.nextlimit.com/contact_tech.php](http://www.nextlimit.com/contact_tech.php) For any sales queries, please feel free to contact us at [http://www.nextlimit.com/contact_sales.php](http://www.nextlimit.com/contact_sales.php)

---

