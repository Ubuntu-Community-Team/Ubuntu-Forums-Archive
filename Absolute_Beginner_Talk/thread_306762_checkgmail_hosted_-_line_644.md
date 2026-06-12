---
title: "checkgmail hosted - line 644"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by pompeyjohn on 2006-11-25
Hi there,

I am running Edgy, and have installed the checkgmail script from synaptic. I have a hosted email account. I have checked the man page and the howto, and I just cant get it to work.

The console is showing this error every second or so:

```
Use of uninitialized value in concatenation (.) or string at /usr/bin/checkgmail line 644.
```

my .profile prefs file looks like this:

```
<opt archive_as_read="0"
     delay="120000"
     gmail_command="firefox %http://mail.google.com/a/midfieldmaestro.com/"
     hosted="midfieldmaestro.com"
     language="English"
     nomail_command=""
     notify_command=""
     passwd="<my_pwd>"
     popup_delay="6000"
     save_passwd="1"
     show_popup_delay="250"
     time_24="0"
     use_custom_mail_icon="1"
     user="john@midfieldmaestro.com">
  <label_delay></label_delay>
</opt>
```

any ideas?? :D

Thanks in advance...

John

---

### Post by pawelgradziel on 2006-12-20
> **pompeyjohn said:**
> I am running Edgy, and have installed the checkgmail script from synaptic. I have a hosted email account. I have checked the man page and the howto, and I just cant get it to work.

Have you solved this problem?

Hi I've got the same problem with hosted domain at gmail... I think there is problem with getting authorization from gmail. 

Best regards,
--
Pawel Gradziel

---

### Post by ciscosurfer on 2006-12-20
I think you guys would be best served by contacting Google and explaining your situation to them.  I have a feeling they will be able to help you out (not with checkgmail specifically, but with getting 3rd party apps to check your hosted Gmail accounts properly).  This seems like it is due to the fact that your accounts are hosted account and not "Gmail proper" accounts.

---

### Post by pawelgradziel on 2006-12-20
@ciscosurfer: 
I think the problem is with checkgmail app, because the link using to get atom feeds for new mails is correct and after passing login and pass I get list of new mails... I know that there is slightly differences in normal gmail authorisation and hosted domail gmail authorization.

I thought someone else already solved this problem by his own. But I see that this is more complex. I will write to both google and checkgmail teams and will copy&paste replays here.

---

### Post by ciscosurfer on 2006-12-20
> **pawelgradziel said:**
> @ciscosurfer: 
I think the problem is with checkgmail app, because the link using to get atom feeds for new mails is correct and after passing login and pass I get list of new mails... I know that there is slightly differences in normal gmail authorisation and hosted domail gmail authorization.

I thought someone else already solved this problem by his own. But I see that this is more complex. I will write to both google and checkgmail teams and will copy&paste replays here.Perhaps it is an issue with how checkgmail parses authorization (I suspect it is).  Please post back with the replies that you get as I'm curious to know what their respective repsonses are. :D

---

### Post by pawelgradziel on 2006-12-20
> **ciscosurfer said:**
> Perhaps it is an issue with how checkgmail parses authorization (I suspect it is).  

Yes and no :)
There is two-level authorization process. First you are logging to your account and then something else is doing (don't have a time to analize all of it).

The problem may be in line 637 (first logging to account): 
 
$error = http_get("https://www.google.com/a/$hosted/LoginAction|at=null&continue=http%3A%2F%2Fmail.google.com%2Fhosted%2F$hosted&service=mail&userName=$URI_user&password=$URI_passwd", "POST"); 
 
This path is true for administrators only. If you are normal user, you should log in using this path: 
$error = http_get("https://mail.google.com/a/$hosted/LoginAction|at=null&continue=http%3A%2F%2Fmail.google.com%2Fhosted%2F$hosted&service=mail&userName=$URI_user&password=$URI_passwd", "POST"); 
 
When I'm trying to log in using [http://www.google](http://www.google)... url I get error in my browser, and when I log in using mail.google.... path I log in successfully. However I still have problem with getting checkgmail working. 

So you are right that getting authorization token is broken (also :)).

Any ideas what else can be done here?

--
Pawel Gradziel

---

### Post by pawelgradziel on 2006-12-20
I checked one more thing. After first logging in line 637, there is subroutine (scan_at) that should get authorization hash (HID). I check this subroutine (its getting HID value from cookies), but I have no such cookie in my gmail after log in... So, thats why its not working properly. 

Any ideas?

Maybe some Google guy can say something more? :)

--
Pawel Gradziel

---

### Post by pawelgradziel on 2006-12-21
Hi All,

I posted this problem on checkgmail project forum at sourceforge.net yesterday:
[http://sourceforge.net/forum/forum.php?thread_id=1635523&forum_id=463626](http://sourceforge.net/forum/forum.php?thread_id=1635523&forum_id=463626)

Owen Marshall wrote me back yesterday and today he uploaded new checkgmail version that solves this problem (1.10.2pre2):
[http://sourceforge.net/project/showfiles.php?group_id=137480](http://sourceforge.net/project/showfiles.php?group_id=137480)

It works for my domain. I think this should work with other hosted domains as well.

So, problem is solved! **Thank you Owen!**

Best regards,
--
Pawel Gradziel

---

### Post by ciscosurfer on 2006-12-21
> **pawelgradziel said:**
> Hi All,

I posted this problem on checkgmail project forum at sourceforge.net yesterday:
[http://sourceforge.net/forum/forum.php?thread_id=1635523&forum_id=463626](http://sourceforge.net/forum/forum.php?thread_id=1635523&forum_id=463626)

Owen Marshall wrote me back yesterday and today he uploaded new checkgmail version that solves this problem (1.10.2pre2):
[http://sourceforge.net/project/showfiles.php?group_id=137480](http://sourceforge.net/project/showfiles.php?group_id=137480)

It works for my domain. I think this should work with other hosted domains as well.

So, problem is solved! **Thank you Owen!**

Best regards,
--
Pawel GradzielThank you pawelgradziel and thank you Owen Marshall!!!  :D:D:D

---

