---
title: "Macports, need help cant install FOSS packages"
date: 2008-11-18
forum: Apple Hardware Users
---

### Post by ju2wheels on 2008-11-18
Not Ubuntu related, but still hoping you guys can help.

I recently installed MacPorts on my macbook (aluminum) running Leopard.

I installed Xcode, then Mac Ports using the dmg installer. I then couldnt run "port" from the command line so I created a .profile file with an updated PATH, MANPATH, and Display environment variables.

I was then able to run port and update it. However, I cant install any packages as there seems to be a configuration issue and im completely stuck as Im not too familiar with Mac at all.

I was originally trying to install emacs-app but just ended up trying to install ncursesw since it has no dependencies and I get the following:

```

sudo port install ncursesw
Password:
--->  Configuring ncursesw
Error: Target org.macports.configure returned: configure failure: shell command " cd "/opt/local/var/macports/build/_opt_local_var_macports_sources_rsync.macports.org_release_ports_devel_ncursesw/work/ncurses-5.7" && ./configure --prefix=/opt/local --enable-widec --disable-rpath --with-shared --without-debug --without-ada --enable-safe-sprintf --enable-sigwinch --mandir=/opt/local/share/man " returned error 1
Command output: sh: line 0: cd: /opt/local/var/macports/build/_opt_local_var_macports_sources_rsync.macports.org_release_ports_devel_ncursesw/work/ncurses-5.7: No such file or directory

Error: Status 1 encountered during processing.

```

---

### Post by cyberdork33 on 2008-11-18
If I had to guess, I'd say there was a permissions issue.

Since this is pretty specifically related to macports, it would probably be easiest to just contact the macports devs/maintainers or use the macports support information / tools here:
[http://www.macports.org/](http://www.macports.org/)

---

