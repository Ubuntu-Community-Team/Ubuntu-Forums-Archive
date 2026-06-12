---
title: "strange message on shutdown"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-03-10
I see this message on shutdown

etc/rc6.d/k20c lamav-freshclam line 163: log_demon_msg command not found


any ideas please

lex1;) ;)

---

### Post by mlind on 2006-03-10
I don't use ClamAV myself, but there seems to be some problem on its shutdown
script. You can check it out by opening the file that symlink
/etc/rc6.d/k20clamav-freshclam is pointing and looking on line 163.

Nothing too serious I guess.

---

### Post by rboss on 2006-03-10
The error message is created because the start/stop script  (/etc/rc6.d/k20c lamav-freshclam) does not find the log_demon_msg function.

This function should be from /lib/lsb/init-functions, (this file should be included right at the start of the start/stop script). 

You might want to check if you have the lsb-base package installed.

---

### Post by NoNo_231 on 2006-03-12
I had this problem too. I installed the new version of ClamAV and stopped. Added 
deb [http://dotdeb.pimpmylinux.org/](http://dotdeb.pimpmylinux.org/) stable all
deb-src [http://dotdeb.pimpmylinux.org/](http://dotdeb.pimpmylinux.org/) stable all
to the sources.list or in the synaptic repositories. Installed the new version and works fine. Ubuntu's version is the previous one and gives error messages.

---

