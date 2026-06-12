---
title: "[SOLVED] 421 Login Timeout (20 Seconds): Closing Control Connection proftpd"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by tenjin1 on 2008-02-24
I have setup proftpd by using this guide [http://ubuntuforums.org/showthread.php?t=79588]("http://ubuntuforums.org/showthread.php?t=79588"). I have used proftpd before by setting up with the same guide when I was on Breezy and used for over a year with no problems. Well, I'm going back to proftpd andcan't seem to get it to work. The syntax checks and debugs are ok but after I login it gives me the error: "421 Login Timeout (20 Seconds): Closing Control Connection" IMMEDIATELY after I login..not even 20 sec has passed! .I have never seen this error before, I have always got the 530 error and I havent found any answers about this.

Can any proftpd specialists help me out with this please? I need to get this ftp up and running. 
Thanks.

---

### Post by dcstar on 2008-02-24
> **tenjin1 said:**
> I have setup proftpd by using this guide [http://ubuntuforums.org/showthread.php?t=79588]("http://ubuntuforums.org/showthread.php?t=79588"). I have used proftpd before by setting up with the same guide when I was on Breezy and used for over a year with no problems. Well, I'm going back to proftpd andcan't seem to get it to work. The syntax checks and debugs are ok but after I login it gives me the error: "421 Login Timeout (20 Seconds): Closing Control Connection" IMMEDIATELY after I login..not even 20 sec has passed! .I have never seen this error before, I have always got the 530 error and I havent found any answers about this.

Can any proftpd specialists help me out with this please? I need to get this ftp up and running. 
Thanks.

Check your firewall/Passive FTP settings.

---

### Post by tenjin1 on 2008-02-24
Ok I think I have the Passive Ports opened on my firewall and router but not sure if it's listed in my proftpd.conf file.

Will check when I get home home today and report back my findings.

---

### Post by tenjin1 on 2008-02-24
Awesome! It's working!

I specified PassivePorts and forwarded them as so and voila! it's working.

Now what I really want to do is map my external USB drive as my FTP folder and have user chrooted in it.

Thanks again

---

