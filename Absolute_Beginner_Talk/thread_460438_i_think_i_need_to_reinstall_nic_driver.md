---
title: "i think i need to reinstall nic driver"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by rziraschi on 2007-05-31
Hello all,
I am using ubunut 6.06 server edition (no GUI) I was able to setup the server and was able to share out directories with SAMBA. The motherboard died on the test box so I moved the hard drive to another test machine. The OS boots fine, but there is no network connection. I am assuming that I just need to install the correct nic dirver for the new computer and I should be up and running again.
Unfortunately I am a newbie and not sure how to do this from the command prompt. I tried a couple of searches but i did not see a match for my issue. Sorry if I overlooked something and this issue has been on the board before.
I should not need to reinstall the whole OS, any ideas?

Regards,
Ron

---

### Post by rziraschi on 2007-06-03
issue resolved, 
I ran 'ifconfig -a' and it found an eth1 for some reason (though 'ifup eth1' also had no effect) which had a MAC address in it. I hopped into '/etc/iftab', changed the MAC address on eth0 to the MAC that was attached to eth1 in ifconfig and rebooted. VOILA! Network up and running!

---

