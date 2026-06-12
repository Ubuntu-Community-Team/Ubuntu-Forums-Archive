---
title: "Can you please convert this for me? (rpm &gt; deb)"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by azharc on 2006-10-30
I can't connect to the internet on Ubuntu because my ISP uses the 24Online client. Being a newbie, after some googling I found that something called Linc lets me connect to the 24Online network. However, it is an rpm file. I read I need to convert it to a deb file using alien, but to download alien I need an internet connection, so I can't. I tried downloading all the dependencies and alien on Windows and then getting it into Linux but I'm running into trouble. Could somebody please convert the file to a .deb and either e-mail it to me (azharc-gmail) or put it on a server and host it here? I can't find the .deb for this anywhere.

[Download it here]("http://sourceforge.net/project/showfiles.php?group_id=55535&package_id=78690&release_id=151021")

I think I could use the source, but having used Linux only twice for a day, I really have no idea how to do anything like that.

Thanks you very much, and I'm happy to be joining such a cool community. I'm falling in love with Linux, it's just too classy :D

---

### Post by Perfect Storm on 2006-10-30
You can dind packages here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Just make sure you get their dependencies as well.

Which package(s) are you looking for to convert? The chance that there's a .deb instead is big.

---

### Post by azharc on 2006-10-30
> **Artificial Intelligence said:**
> You can dind packages here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Just make sure you get their dependencies as well.

Which package(s) are you looking for to convert? The chance that there's a .deb instead is big.

I was having problems. Even though a dependency was installed it would say it wasn't. Anyways thanks a ton to Ken Clark for sending over the deb!

Thanks for your fast response :) 

You see finding and downloading all of the packages with their dependencies got frustrating.

---

### Post by nUllSkillZ on 2006-10-30
You should try "alien" (package in Ubuntu available).

---

### Post by mips on 2006-10-30
Ok, I created a deb file.

Where must i upload it to or mail it to. Do NOT post your email address here, rather pm me.

To the rest of you people, read his post again. He does not have internet. He needs internet to install alien. Alien is required to create a deb of a packaged required to get internet. CATCH-22

Here is the output of alien:```

mips@obelix:~$ sudo alien -cdvk linc-daemon-1.2-1.i386.rpm
        LANG=C rpm -qp --queryformat %{SUMMARY} linc-daemon-1.2-1.i386.rpm
        LANG=C rpm -qp --queryformat %{POSTIN} linc-daemon-1.2-1.i386.rpm
        LANG=C rpm -qp --queryformat %{NAME} linc-daemon-1.2-1.i386.rpm
        LANG=C rpm -qp --queryformat %{POSTUN} linc-daemon-1.2-1.i386.rpm
        LANG=C rpm -qp --queryformat %{PREUN} linc-daemon-1.2-1.i386.rpm
        LANG=C rpm -qp --queryformat %{RELEASE} linc-daemon-1.2-1.i386.rpm
        LANG=C rpm -qp --queryformat %{PREFIXES} linc-daemon-1.2-1.i386.rpm
        LANG=C rpm -qp --queryformat %{CHANGELOGTEXT} linc-daemon-1.2-1.i386.rpm
        LANG=C rpm -qp --queryformat %{COPYRIGHT} linc-daemon-1.2-1.i386.rpm
        LANG=C rpm -qp --queryformat %{DESCRIPTION} linc-daemon-1.2-1.i386.rpm
        LANG=C rpm -qp --queryformat %{ARCH} linc-daemon-1.2-1.i386.rpm
        LANG=C rpm -qp --queryformat %{VERSION} linc-daemon-1.2-1.i386.rpm
        LANG=C rpm -qp --queryformat %{PREIN} linc-daemon-1.2-1.i386.rpm
        LANG=C rpm -qcp linc-daemon-1.2-1.i386.rpm
        rpm -qpi linc-daemon-1.2-1.i386.rpm
        LANG=C rpm -qpl linc-daemon-1.2-1.i386.rpm
        mkdir linc-daemon-1.2
        chmod 755 linc-daemon-1.2
        rpm2cpio linc-daemon-1.2-1.i386.rpm | (cd linc-daemon-1.2; cpio --extract --make-directories --no-absolute-filenames --preserve-modification-time) 2>&1
        chmod 755 linc-daemon-1.2/./
        chmod 755 linc-daemon-1.2/./etc
        chmod 755 linc-daemon-1.2/./etc/init.d
        chmod 755 linc-daemon-1.2/./usr
        chmod 755 linc-daemon-1.2/./usr/bin
        chmod 755 linc-daemon-1.2/./usr/man
        chmod 755 linc-daemon-1.2/./usr/man/man1
        chmod 755 linc-daemon-1.2/./usr/man/man5
        chmod 755 linc-daemon-1.2/./usr/share
        chmod 755 linc-daemon-1.2/./usr/share/doc
        chown 0:0 linc-daemon-1.2//etc/init.d/linc
        chmod 755 linc-daemon-1.2//etc/init.d/linc
        chown 0:0 linc-daemon-1.2//usr/bin/linc
        chmod 755 linc-daemon-1.2//usr/bin/linc
        chown 0:0 linc-daemon-1.2//usr/man/man1/linc.1.gz
        chmod 644 linc-daemon-1.2//usr/man/man1/linc.1.gz
        chown 0:0 linc-daemon-1.2//usr/man/man5/lincrc.5.gz
        chmod 644 linc-daemon-1.2//usr/man/man5/lincrc.5.gz
        chown 0:0 linc-daemon-1.2//usr/share/doc/linc-daemon-1.2
        chmod 755 linc-daemon-1.2//usr/share/doc/linc-daemon-1.2
        chown 0:0 linc-daemon-1.2//usr/share/doc/linc-daemon-1.2/AUTHORS
        chmod 644 linc-daemon-1.2//usr/share/doc/linc-daemon-1.2/AUTHORS
        chown 0:0 linc-daemon-1.2//usr/share/doc/linc-daemon-1.2/COPYING
        chmod 644 linc-daemon-1.2//usr/share/doc/linc-daemon-1.2/COPYING
        chown 0:0 linc-daemon-1.2//usr/share/doc/linc-daemon-1.2/ChangeLog
        chmod 644 linc-daemon-1.2//usr/share/doc/linc-daemon-1.2/ChangeLog
        chown 0:0 linc-daemon-1.2//usr/share/doc/linc-daemon-1.2/README
        chmod 644 linc-daemon-1.2//usr/share/doc/linc-daemon-1.2/README
        chown 0:0 linc-daemon-1.2//usr/share/doc/linc-daemon-1.2/TODO
        chmod 644 linc-daemon-1.2//usr/share/doc/linc-daemon-1.2/TODO
        chown 0:0 linc-daemon-1.2//usr/share/doc/linc-daemon-1.2/sample.lincrc
        chmod 644 linc-daemon-1.2//usr/share/doc/linc-daemon-1.2/sample.lincrc
        mkdir linc-daemon-1.2/debian
        hostname -f
        822-date
        hostname -f
        822-date
        chmod 755 linc-daemon-1.2/debian/rules
        install -d linc-daemon-1.2//usr/share
        mv linc-daemon-1.2//usr/man linc-daemon-1.2//usr/share/man
        debian/rules binary 2>&1
linc-daemon_1.2-1_i386.deb generated
        find linc-daemon-1.2 -type d -exec chmod 755 {} ;
        rm -rf linc-daemon-1.2
mips@obelix:~$
```

---

### Post by shuklasp on 2007-06-03
Can you please provide it to me? You can attach the file here in this forum itself.

Looking for an early reply.

Regards
Satya Prakash Shukla

---

### Post by shuklasp on 2007-06-03
I somehow managed to install alien on my system. After that, I converted this rpm file to deb. But on installing it, it gives an error that pkgconfig is not found.

When I build it without conserving configuration files, it installs. But on being run, it gives an error of libc++6 (Or something of that sort).

If anyone is able to install and run it properly, please post it here.

I am attaching this file made by me with this post.

Regards
Satya Prakash Shukla

---

