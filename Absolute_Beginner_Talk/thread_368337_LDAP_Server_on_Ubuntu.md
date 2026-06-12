---
title: "LDAP Server on Ubuntu"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by spallw on 2007-02-23
folks,
I need an LDAP server for a project I am undertaking. I have been introduced to ubuntu and think it's great, but this is all rather new to me.

I have installed Ubuntu 6.06 LTS via CD and LDAP (OPENldap I believe) via the command: sudo apt-get install slapd ldap-utils
I have configured using the command: sudo dpkg-reconfigure -plow slapd and/or set individual commands within the slapd.conf file itself.
I have also installed Directory Administrator to manage, however it continues to tell me that my directory appears emtpy or I have no organisational units. Yet after many a websites' suggestion for a ldif files I do not appear to be able to populate the directory. either there is "nothing to update" or "no global knowledge"

All in all I think I have seen one too many websites without one giving me a step-by-step approach.

Is there a singles "dummies guide" to setting up LDAP server and populating the directory? (only need username, password, company name as fields nothing flash !!

thanks in advance  :confused:

---

### Post by karls0 on 2007-02-26
Hi,
sorry, I can´t give you a step by step-guide. I´ve set one up more than a year ago and rember only very little. One thing is, that you have to set up a few things (the admins cn, your companys dc...) in the config-file. Test if you can connect to the server by using the ldap-tools (ldapsearch....).

After that you could use a graphical tool like
           phpLDAPadmin
to manage everything. 

hth
Karl

---

### Post by spallw on 2007-02-26
thanks for that Karl,

I decided to start again from scratch and looks like I might finally have it :)  Here's the drill..

* Downloaded 6.10
* installed LDAP:  sudo apt-get install slapd ldap-utils
* configured LDAP:  sudo dpkg-reconfigure -plow slapd
* made necessary changes to ldap.conf & slapd.conf 
* installed the LAT (LDAP Admin tool) from Applications - add/remove (not Directory Admin)
* set up groups etc from here

also another tool "softerra LDAP admin" was pretty useful on a windows box (but trial only)

WS..

---

### Post by kiko on 2007-02-28
> **spallw said:**
> thanks for that Karl,

I decided to start again from scratch and looks like I might finally have it :)  Here's the drill..

* Downloaded 6.10
* installed LDAP:  sudo apt-get install slapd ldap-utils
* configured LDAP:  sudo dpkg-reconfigure -plow slapd
* made necessary changes to ldap.conf & slapd.conf 
* installed the LAT (LDAP Admin tool) from Applications - add/remove (not Directory Admin)
* set up groups etc from here

also another tool "softerra LDAP admin" was pretty useful on a windows box (but trial only)

WS..


Hi!

I'm new in ubuntu. I've tried to install an LDAP server on Ubuntu 6.I followed the step by step configuration in the guide that ive found in the net. But it seems im lost in configuring,first is its telling me to configure ldap.conf then other is the ldif something.im kind the new in this kind of file.can anyone guide me step by step in configuring an ldap server.

Thanks you so much!

---

### Post by spallw on 2007-03-01
Hi Kiko

I'm probably not the best to ask this of, but here goes...

Firstly follow the procedure in my last posting - to date this seems to be working. Now, as for the LDAP.conf and the SALPD.conf there are only a couple of lines to "edit" in each - this I have gleened from numerous other sites:

LDAP.conf you will see lines like this hashed out, un-hash or add your own to reflect this:

BASE     dc=yourdomain,dc=com,dc=au
URI      ldap://localhost

SLAPD.conf is a little more difficult, the default file is a working basis, but it appears you should add the following two lines.

rootdn          "cn=admin,dc=yourdomain,dc=com,dc=au"
rootpw          secret

you should change 'secret' to something encrypted, use slappasswd at a terminal prompt, enter a password, then cut and paste the resultant {SSHA}........ in place of secret above.
 
and then for security

  access to *
        by dn="cn=admin,dc=yourdomain,dc=com,dc=au" write
        by peername.regex="^IP=127\.0\..+" read
        by peername.regex="^IP=192\.168\..+" read
        by users read
        by * none

Hope this gets you started  ;-)

Wayne..

---

### Post by kiko on 2007-03-07
Hi Spallw,

Thanks for your reply.

I think i have already run the ldap server, thanks to you. You see,I'm trying to setup a centralized address book, google says i should used ldap server. Last time im getting an error now i think its running fine, but how will i put some data on the server. Im a dummy on this and not a linux user. I've also configure an ldap client using outlook express and point to ldap server without hassle, but i cant see any data on the server.I think im enjoying using ubuntu as desktop. How can i put some data on the ldap server?

---

