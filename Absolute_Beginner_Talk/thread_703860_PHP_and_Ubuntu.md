---
title: "PHP and Ubuntu"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by hungryOrb on 2008-02-21
I'm not sure about how it works in Linux. Can I install PHP and parse stuff straight away on localhost?

---

### Post by LaRoza on 2008-02-21
You can install Apache, MySQL, PHP and Perl with one command.

```

sudo tasksel

```

Select "LAMPP", don't unselect anything!

The directory for sites will be in /var/www

(You can change that)

You can install php-cli for working with desktop applications in PHP, if that is what you want.

---

### Post by PeterJS on 2008-02-21
Or you can graphically run tasksel from with in synaptic package manager with Mark Packages by Task in the edit menu.

---

### Post by Origin415 on 2008-02-21
PHP and Apache should automatically work together after installing mod_php, found in the package libapache2-mod-php5

---

### Post by hungryOrb on 2008-02-21
Thankyou! #:]

---

### Post by hungryOrb on 2008-02-22
Guys, I gots a problem. I tried to save a .php file in my www folder and it denied me saying I didnt have permission, but im using the account with admin access!
EEK :( tbh, it's a bit like Windows when Ubuntu says there is a problem and doesnt suggest a reason why, or hint to a fix :(

I just sit in corner self absorbed :(

---

### Post by indytim on 2008-02-22
You are going to need to change the ownership of /var/www to you.  Either change it through your favorite file manager or do the terminal thinger and run the chown and chgrp commands.   See the man pages for the exact protocol.

IndyTim

---

### Post by PeterJS on 2008-02-22
> **hungryOrb said:**
> Guys, I gots a problem. I tried to save a .php file in my www folder and it denied me saying I didnt have permission, but im using the account with admin access!


That's how the security system works, being admin doesn't give you elevated privileges, being admin gives you the right to request elevated privileges. To actually have privileges elevated beyond that of a normal user account you need to use sudo or one of it's graphical variants.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

