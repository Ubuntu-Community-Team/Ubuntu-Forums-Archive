---
title: "Samba setup"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-03-16
Can anybody point me to links that explain in easy to understand, yet detailed setup instructions for Samba?

This would be setup for a home file server.

---

### Post by mbeach on 2008-03-16
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by mandrill on 2008-03-16
Unfortunately, there are a lot of different answers to that question. I've been asking, and getting different answers with varying degrees of success for 6 months.

---

### Post by paydaydaddy on 2008-03-16
The best guide that I have found. Works well for me.

[http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer](http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer)

---

### Post by BlizzofOZ on 2008-03-17
> **mandrill said:**
> Unfortunately, there are a lot of different answers to that question. I've been asking, and getting different answers with varying degrees of success for 6 months.

mandrill,

I just wanted to let you know that I followed stormbringer's guide, in paydaydaddy's link, and it worked!

I had one problem, but by removing/commenting out the force user and group in the smb.conf file, it worked fine.

---

### Post by mandrill on 2008-03-17
Blizz - thanks for the encouragement. But I have been using stormbringers method for some time now. Have you tried to connect to a remote printer yet? Hint: do it before you configure the network.......

                                      Regards & Peace, 

                                                                mandrill


By the way I noticed you're from Meriden. I'm from Windsor. Ciao!

---

### Post by BlizzofOZ on 2008-03-19
> **mandrill said:**
> Blizz - thanks for the encouragement. But I have been using stormbringers method for some time now. Have you tried to connect to a remote printer yet? Hint: do it before you configure the network.......

                                      Regards & Peace, 

                                                                mandrill


By the way I noticed you're from Meriden. I'm from Windsor. Ciao!

No I haven't done anything with printing... yet.  I took you to mean that you haven't got your Samba file serving to work.

I see your location is PHX... are originally from Windsor and now live in PHX?  Funny, I have a friend (from CT) who moved out to PHX for awhile... he always uses CIAO!

---

