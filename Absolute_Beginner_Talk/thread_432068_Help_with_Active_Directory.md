---
title: "Help with Active Directory"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Jenillaroma on 2007-05-03
I get a ticket and my computer name is in the ad list but it says it is disabled.  I come up with this error.
Failed to set servicePrincipalNames. Please ensure that
the DNS domain of this server matches the AD domain,
Or rejoin with using Domain Admin credentials.

The DNS domain and the AD domain are correct.  There is no miss spelling.

Please Help the Beginner!!!!!!!!!  Thank you in advanced

---

### Post by Churnd on 2007-05-03
I don't think this belongs in Beginner Talk.

What does your /etc/krb5.conf show?

---

### Post by Jenillaroma on 2007-05-03
What I am doing is I am following the How-To : Active Directory Authentication - Ubuntu Forums.
I am between Steps 5 - Steps 8.  I got through step 5 just fine.  Step 6 went just fine too.  Step 7 I can get a ticket.  Step 8 is where I come into a problem with net ads join -U [email]domainadminuser@DOMAIN.INTE[/email]RNAL.  That is where it gives me the error : Failed to set servicePrincipalNames. Please ensure that
the DNS domain of this server matches the AD domain,
Or rejoin with using Domain Admin credentials.
I hope this is better to understand my problem.  Thank you in advanced.

---

### Post by Jenillaroma on 2007-05-04
My /etc/krb5.conf  shows : 
[logging]
	default = FILE10000:/var/log/krb5lib.log
[libdefaults]
	ticket_lifetime = 24000
	default_realm = DOMAIN.INTERNAL
	default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc
	default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc
[realms]
	DOMAIN.INTERNAL = {
	  kdc = domainserver.domain.internal
          admin_server = domainserver.domain.internal
          default_domain = DOMAIN.INTERNAL
}
[domain_realm]
	.domain.internal = DOMAIN.INTERNAL
	domain.internal = DOMAIN.INTERNAL

# The following krb5.conf variables are only for MIT Kerberos.	krb4_config = /etc/krb.conf
	krb4_realms = /etc/krb.realms
	kdc_timesync = 1
	ccache_type = 4
	forwardable = true
	proxiable = true

# The following encryption type specification will be used by MIT Kerberos
# if uncommented.  In general, the defaults in the MIT Kerberos code are
# correct and overriding these specifications only serves to disable new
# encryption types as they are added, creating interoperability problems.

#	default_tgs_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-cbc-crc des-cbc-md5
#	default_tkt_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-cbc-crc des-cbc-md5
#	permitted_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-cbc-crc des-cbc-md5

# The following libdefaults parameters are only for Heimdal Kerberos.
	v4_instance_resolve = false
	v4_name_convert = {
		host = {
			rcmd = host
			ftp = ftp
		}
		plain = {
			something = something-else
		}
	}
	fcc-mit-ticketflags = true

[login]
	krb4_convert = true
	krb4_get_tickets = false

---

### Post by ziggie216 on 2007-05-15
you were suppose to change all the DOMAIN.INTERNAL and anything releated to that to your domain server info

---

### Post by teamanx on 2007-05-30
Hi. I had the same problem as you. I was trying to join a Feisty machine to my AD domain, and got the message "Failed to get servicePrincipalNames...". 
I tried to copy the smb.conf and krb5.conf files to a network disk, reinstall Ubuntu Dapper on the same machine using the same host name, and then copy the smb.conf and krb5.conf files form the Feisty installation to the Dapper. When I tried "net ads join", it worked perfectly, and now the host is a member of my AD.
So It seems like the problem is in Feisty. Anybody knows any solution? If this is a bug, has it been reported?

Regards.

BTW, the DNS suffix of my AD domain is "cfs.local". I have readed that Feisty has problems managing domain names ending with ".local", because of a bug in avahi. In the Feisty installation, I tried to join the domain with avahi enabled and disabled, and none of them worked.

---

### Post by teamanx on 2007-05-30
-

---

### Post by hellomatts on 2007-05-30
Jenillaroma,

I was having the exact same problem, and finally figured it out... one thing that isn't mentioned in the HOWTO are the following:

1: edit /etc/hosts 

There should be a line  with your hostname, you need to add your domain name to this:  127.0.1.1 hostname.DOMAIN.LOCAL hostname

2: ensure that  /etc/hostname also has your hostname (not the domain) included there as well...

This fixed it for me!

---

