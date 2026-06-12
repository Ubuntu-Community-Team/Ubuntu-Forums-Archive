---
title: "Can't login to Ebay site with Firefox"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-03-01
Hi I don't understand why but i can't seem to log into the Ebay site. Doesn't matter wether I try through the main page, MyEbay or after viewing an item that I am interested in. I have also contacted Ebay about this as over 80% of the time for the past week I can't get in and there error in firefox is:
Unexpected response from server

Firefox doesn't know how to communicate with the server.

    *   Check to make sure your system has the Personal Security Manager
          installed.

    *   This might be due to a non-standard configuration on the server.

In the error console of Firefox there is this:

---

### Post by roon on 2007-03-01
Reinstall firefox and then try maybe it will help.

---

### Post by rapattack1 on 2007-03-01
OK might do that if this continues but it is the only site I have problems with. Anyway I got into the Ebay 5 minutes ago so all is cool for now.

---

### Post by mengox on 2007-03-02
i guess you can't connect to any site that require https.
If you have Dapper, the cause is the upgrade to the last version (1.5.0.10-0ubuntu0.6.06.2) of Firefox, and the problem is probably the libnss3 package.

I hope they wil fix this soon.

In the meantime, use Epiphany instead! :)

---

### Post by rapattack1 on 2007-03-02
Well I am able to get into many other http sites. I have Edgy. I got into Ebay first go today which is odd. I dunno Ebay was having some other trouble this week too even on days when I could login. Maybe it is just Ebay. If this goes on another week then I will get that other browser you mentioned. Thanks so much!

---

### Post by epa611 on 2007-03-02
> **mengox said:**
> i guess you can't connect to any site that require https.
If you have Dapper, the cause is the upgrade to the last version (1.5.0.10-0ubuntu0.6.06.2) of Firefox, and the problem is probably the libnss3 package.

I hope they wil fix this soon.

In the meantime, use Epiphany instead! :)

I'm having the same problem - I updated Firefox as part of the recommended updates this mornign and now can't access any https site:confused: 

How can I roll back this installation to the previous version?

---

### Post by rblyth on 2007-03-02
> **epa611 said:**
> How can I roll back this installation to the previous version?

In Synaptic, select the package you want to downgrade, then select "Force version" from the "Package" menu. Choose an older version.

BTW, Epiphany gives me the same error message, but mozilla is fine.

I couldn't find a bug report on this, so I just posted one.

Rebecca

---

### Post by mgmiller on 2007-03-02
In Firefox address bar, type about:config and scroll down to the security area.  Mine is set as security.enable_ssl2 value is false and security.enable_ssl3 value is true.  I am able to access any https sites without problems.  I am running Firefox 2.0.0.2.

---

### Post by sdkamm on 2007-03-02
> **epa611 said:**
> I'm having the same problem - I updated Firefox as part of the recommended updates this mornign and now can't access any https site:confused: 

How can I roll back this installation to the previous version?

This is a known bug 

[https://launchpad.net/bugs/89023](https://launchpad.net/bugs/89023) 

(use epiphany to view https)

Unfortunately, the maintainer appears to think 1.5.0.10-0ubuntu0.6.06.2 is the fix.

I partially restored function by Synaptic "Completely Remove" firefox, then installed firefox, latest version.  I assume the latest version, when working, is the most secure.

Https still doesn't work for me when firefox is called from a link embedded in e-mail.

Those of you having problems with 1.5.0.10-0ubuntu0.6.06.2, it might help to open a new bug, since 89023 refers to 1.5.0.10-0ubuntu0.6.06.1.

I'll see if I can contact the maintainer and refer him to this thread.

sdk

PS I have since brought this thread to the maintaner's attention.

It appears that my specific e-mail issue is discussed in [https://launchpad.net/bugs/57923](https://launchpad.net/bugs/57923)

---

### Post by rapattack1 on 2007-03-03
Thanks will try that!

---

### Post by notrublw on 2007-03-03
Applications
Add/Remove
Advanced

Search for Personal Security Manager. Install it (it will also install the mozilla browser, but
I have a lot of space on my hard drive). 

This solved a similar problem with Yahoo email that popped up today (3/3/2007) for the
first time.

---

### Post by rlandrum on 2007-03-05
> **notrublw said:**
> Applications
Add/Remove
Advanced

Search for Personal Security Manager. Install it (it will also install the mozilla browser, but
I have a lot of space on my hard drive). 

This solved a similar problem with Yahoo email that popped up today (3/3/2007) for the
first time.

mozilla-psm is the package name.  I found it, installed it, and restarted my browser.  Access to https restored.

Definitely related to the most recent firefox update.  This needs to be fixed asap, as 6.06LTS is officially broken without this, IMHO.

---

### Post by mdsmedia on 2007-03-12
I couldn't even access the Launchpad site when I clicked on "find help online" within Firefox.
Loading the psm package now.

---

