---
title: "Namecheap dynamic DNS with inadyn"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by Roman27 on 2007-10-02
I recently figured out how to get dynamic dns working with namecheap.com and wanted to share it here.  I use inadyn on Ubuntu 6.10.  Previously, I had it set to update my record with DynDNS.org.  I simply modified my /etc/inadyn.conf file with these settings to get it to work:> dyndns_system custom@http_svr_basic_auth
dyndns_server_name dynamicdns.park-your-domain.com
dyndns_server_url /update?domain=[domain.com]&password=[domain_password]&host=
alias [host_name]
update_period_sec [seconds]
backgroundReplace the items in brackets with your settings and you should be good to go.

---

