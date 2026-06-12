---
title: "How long does it take for a package to migrate from Edgy Eft to Dapper?"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-08-08
Looking forward to install 'Zabbix' (system, networking monitoring tool aka Nagios) from the Dapper depository. However, it is only available for Edgy Eft atm. How long will for the Zabbix package (or any other package in Edgy) to migrate from Edgy Eft depository to Dapper depository?

Thanks !

---

### Post by Anduu on 2006-08-08
I don't know...you could always go to their website,download the source and see if it works...

---

### Post by Akhran on 2006-08-09
Is there an elegant way to handle installing from source with aptitude?

Thanks!

> **Anduu said:**
> I don't know...you could always go to their website,download the source and see if it works...

---

### Post by Anduu on 2006-08-09
> **Akhran said:**
> Is there an elegant way to handle installing from source with aptitude?

Thanks!

Source packages must be compile/installed manually...

See here
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

Note where it mentions using checkinstall...this will install the app so it is easily removed via Synaptic....

---

### Post by PlatinumPlus on 2006-08-11
Is migrating from Edgy to Dapper what they call Backports?

Smurfs turn purple when you choke 'em

---

### Post by djsroknrol on 2006-08-11
Don't 'yall mean "Dapper to Edgy"?...I mean we're not going backwards here...:o

---

### Post by RichJacot on 2006-08-11
Hello Akhran,

I'm very interested in getting ZABBIX working on Dapper also.  Please keep us in the loop as to your success.  I may have time this afternoon to try it from source.  I'll report back on my findings if I do.

---

### Post by Akhran on 2006-08-11
I got it working with Debian 'Testing' branch. (not sure how long it would take for the package to move on to Dapper from Edgy)

aptitude install apache2 
aptitude install php5
aptitude install mysql-server
aptitude install zabbix-server-mysql
aptitude install zabbix-frontend-php

Login to [http://yourmachine/zabbix](http://yourmachine/zabbix) for the admin page.

Download the agents and install them to your client machines if you're doing active checks.

That's all :)


> **RichJacot said:**
> Hello Akhran,

I'm very interested in getting ZABBIX working on Dapper also.  Please keep us in the loop as to your success.  I may have time this afternoon to try it from source.  I'll report back on my findings if I do.

---

### Post by powder on 2006-08-11
AFAIK, packages don't move from Edgy to Dapper as they do in Debian Sid to Debian Etch.  You will have to wait for Edgy to be released.

---

### Post by Akhran on 2006-08-11
What is the tentative release time frame for the release of Edgy?

> **powder said:**
> AFAIK, packages don't move from Edgy to Dapper as they do in Debian Sid to Debian Etch.  You will have to wait for Edgy to be released.

---

### Post by powder on 2006-08-11
October 1st.

---

### Post by RichJacot on 2006-08-14
Hello Akhran,

I downloaded Zabbix source and got it running Friday afternoon (on dapper).  It was pretty straight forward, the only hiccup I had was needing to download mysql.h.  I've had it monitoring two hosts all weekend and it appears to be working great.  Now to make some custom templates, as I will be monitoring approx. 380+ Solaris machines with it.

Rich

---

