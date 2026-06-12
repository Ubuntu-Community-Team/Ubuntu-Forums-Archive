---
title: "How do I file a bug against module-init-tools?"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by rfmonk on 2005-12-23
Hi,

This is my first post. please be patient, if I missed something just point me to a link, I would be very grateful.

My current issues are multifold however on the rabbit trail to understand and fix my 80211 connection I came to the conclusion that I needed to abandon ipv6.

(background info. installed 5.04 on Sony VAIO VGNT350P
              iwconfig
              .....eth1 unassociated  ESSID:"2ndRenaissance"
                   mode:managed channel:0 Access Point: 00:00:00:00:00:00
                   ok everything is either off or 0

              ifconfig
                   eth1 Link encap:Ethernet HWaddr  00:13:CE:37:A9:A3
                   inet 6 addr: xx80::xxxxxxxxxx etc scope link
                   UP BROADCAST MULTICAST MTU:1500
                   RX packets: 299691 errors:286 dropped:286

              dmesg
                   briefly... WEP  decryption failed ICV mismatch
                               decryption failed (SA=00:14:bf:ae:59:40) res=2
 this about a hundred times or so, last night I was associated but recieved a line in the dmesg that said
                   disabled privacy extensions on device... and IPv6 over IPv4 tunneling driver   and another line of note was no IPv6 routers present.)

So anyway, I had heard in the past that IPv6 was problematic and thought I would start there disabling it, I found on the wiki [http://wiki.ubuntu.com/FindPage](http://wiki.ubuntu.com/FindPage)      someone telling this guy how to disable IPv6 by editing /etc/modprobe.d   alias net-pf-10 ipv6 **off** , however
not only is it a read only file, and I cant figure how to get root permissions to change this file, but in the comments it says 
"Please file a bug against module-init-tools if a package needs a entry"
could someone spell out how to do this, assume I know nothing, and be very concise. also could you point me to a tutorial on how to add, edit, and change files in Ubuntu. I have tons of oreilly books, e-books, etc but sometimes the info overload just becomes so agrevateing. I had this computer recognizing my WRT54G access point initially after install, but I went around the neighborhood casually espresso shop wardinning and must have screwed something up.

thank you

---

### Post by DevilsAdvocate on 2005-12-23
There's an Ubuntu Bugzilla site w/ the link at the top right of this page.  I don't know anything about your problem, so I don't know if it's an Ubuntu problem or upstream.  You could file the bug (search for similar ones first) and they will tell you if it's upstream and what you should do.

---

### Post by rfmonk on 2005-12-23
Thank you for your reply, however,  Bug 2102 was all I was able to find on module-init-tools and the bug reports filed seemed very unrelated to my issue.
It seems to me like the comment really is asking to edit something, taken in the context, and being unaware of what or how to edit this is my real question I guess. 

Unless someone knows directly how to fix wireless issues I will continue to take advice on how to disable ipv6.

---

### Post by deNoobius on 2005-12-23
In terms of editing a file, did you try to open the file you're trying to edit using sudo?  I.e:, for example, sudo nano [name of file]?  Try it and see if you still have a permissions problem.

---

### Post by rfmonk on 2005-12-23
thanks, apparently the missing ingredient was gedit between sudo and the filename. so simple ;-)

   1.

       sudo gedit /etc/modprobe.d/aliases 
   2.

      Find the line:  alias net-pf-10 ipv6 
   3.

      Replace it with:  alias net-pf-10 off 
   4.

      Save the file and restart your computer

You must reboot for changes to take effect. 

Ok, so at least I got that issue resolved of how to edit the file. Thank You. However my bigger issue of not being able to connect fully with my router is still at large, so it's back once again to the rabbit path. Next stop, why is WEP decryption failing and giving a ICV mismatch?

---

