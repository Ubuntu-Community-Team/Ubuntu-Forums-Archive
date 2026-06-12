---
title: "Kernel bug fix works for me! :-D"
date: 2008-10-20
forum: Arch and derivatives
---

### Post by handy on 2008-10-20
Having been hit by the kernel bug that interferes with internet access & having to downgrade the kernel to escape the bug.  I am happy to say that after reading a bug report on the subject here:

***_[http://bugzilla.kernel.org/show_bug.cgi?id=11721](http://bugzilla.kernel.org/show_bug.cgi?id=11721)_***

Courtesy of a link posted by Misfit138, 8-) I found deep down in the report dialogue that the following command as root, worked for the poster of the bug:

***echo 0 > /proc/sys/net/ipv4/tcp_timestamps***

So I did a yaourt -Syu & found amongst other packages a minor kernel update, which did not solve my internet problems, but after ***su***, & then entering the above command in the Terminal my internet works as it should! :-D 8-)

If this solution works for you, then (this is courtesy of Misfit138 also 8-)) add the following to your ***/etc/sysctl.conf***:

[B][I]#Temporary workaround for tcp issue with 2.6.27
net.ipv4.tcp_timestamps = 0[/I][/B]


I hope this solution works for all of the other bug bitten members of the Arch (& Linux) community!

---

