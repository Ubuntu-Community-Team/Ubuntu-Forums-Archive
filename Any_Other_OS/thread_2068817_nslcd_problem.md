---
title: "nslcd problem"
date: 2012-10-09
forum: Any Other OS
---

### Post by AIREE.Shadow on 2012-10-09
So, I've installed ldap+samba on my test server and getting spammed into logs file:
```
==> daemon.log <==
Oct 10 10:20:13 arhat nslcd[2646]: [227194] ldap_result() failed: No such object

==> syslog <==
Oct 10 10:20:13 arhat nslcd[2646]: [797576] ldap_result() failed: No such object

==> daemon.log <==
Oct 10 10:20:13 arhat nslcd[2646]: [797576] ldap_result() failed: No such object

==> syslog <==
Oct 10 10:20:13 arhat nslcd[2646]: [1062d6] ldap_result() failed: No such object

==> daemon.log <==
Oct 10 10:20:13 arhat nslcd[2646]: [1062d6] ldap_result() failed: No such object

==> syslog <==
Oct 10 10:20:13 arhat nslcd[2646]: [ae1b05] ldap_result() failed: No such object

==> daemon.log <==
Oct 10 10:20:13 arhat nslcd[2646]: [ae1b05] ldap_result() failed: No such object

```

what is nslcd -d say to me:
```
root@arhat:/home/airee# nslcd -d
nslcd: DEBUG: add_uri(ldap://127.0.0.1/)
nslcd: daemon may already be active, cannot acquire lock (/var/run/nslcd/nslcd.pid): Permission denied

```

and this is my slapd.conf:
```
# Global Directives:
# Features to permit
#allow bind_v2
include /etc/ldap/schema/core.schema
include /etc/ldap/schema/collective.schema
include /etc/ldap/schema/corba.schema
include /etc/ldap/schema/cosine.schema
include /etc/ldap/schema/duaconf.schema
include /etc/ldap/schema/dyngroup.schema
include /etc/ldap/schema/inetorgperson.schema
include /etc/ldap/schema/java.schema
include /etc/ldap/schema/misc.schema
include /etc/ldap/schema/nis.schema
include /etc/ldap/schema/openldap.schema
include /etc/ldap/schema/ppolicy.schema
include /etc/ldap/schema/samba.schema

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile         /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile        /var/run/slapd/slapd.args

# Read slapd.conf(5) for possible values
loglevel        none

# Where the dynamically loaded modules are stored
modulepath /usr/lib/ldap
moduleload back_hdb

# The maximum number of entries that is returned for a search operation
sizelimit 500

# The tool-threads parameter sets the actual amount of cpu's that is used
# for indexing.
tool-threads 1

#######################################################################
# Specific Backend Directives for hdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend hdb

#######################################################################
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
#backend    <other>

#######################################################################
# Specific Directives for database #1, of type hdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        hdb

# The base of your directory in database #1
suffix          "dc=local"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
rootdn          "cn=admin,dc=local"
rootpw          {MD5}xMpCOKC5I4INzFCab3WEmw==

# Where the database file are physically stored for database #1
directory       "/var/lib/ldap"

# The dbconfig settings are used to generate a DB_CONFIG file the first
# time slapd starts.  They do NOT override existing an existing DB_CONFIG
# file.  You should therefore change these settings in DB_CONFIG directly
# or remove DB_CONFIG and restart slapd for changes to take effect.

# For the Debian package we use 2MB as default but be sure to update this
# value if you have plenty of RAM
dbconfig set_cachesize 0 2097152 0

# Sven Hartge reported that he had to set this value incredibly high
# to get slapd running at all. See http://bugs.debian.org/303057 for more
# information.

# Number of objects that can be locked at the same time.
dbconfig set_lk_max_objects 1500
# Number of locks (both requested and granted)
dbconfig set_lk_max_locks 1500
# Number of lockers
dbconfig set_lk_max_lockers 1500

# Indices to maintain for this database
index objectClass                       eq,pres
index ou,cn,sn,mail,givenname           eq,pres,sub
index uidNumber,gidNumber,memberUid     eq,pres
index loginShell                        eq,pres
## required to support pdb_getsampwnam
index uid                               pres,sub,eq
## required to support pdb_getsambapwrid()
index displayName                       pres,sub,eq
index nisMapName,nisMapEntry            eq,pres,sub
index sambaSID                          eq
index sambaPrimaryGroupSID              eq
index sambaDomainName                   eq
index default                           sub
index uniqueMember                      eq
index sambaGroupType                    eq
index sambaSIDList                      eq

# Save the time that the entry gets modified, for database #1
lastmod         on

# Checkpoint the BerkeleyDB database periodically in case of system
# failure and to speed slapd shutdown.
checkpoint      512 30

# Where to store the replica logs for database #1
# replogfile /var/lib/ldap/replog

# users can authenticate and change their password
    access to attrs=userPassword,sambaNTPassword,sambaLMPassword,sambaPwdMustChange,sambaPwdLastSet
    by self write
    by anonymous auth
    by * none

# those 2 parameters must be world readable for password aging to work correctly
# (or use a priviledge account in /etc/ldap.conf to bind to the directory)
    access to attrs=shadowLastChange,shadowMax
    by self write
    by * read

# all others attributes are readable to everybody
    access to *
    by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#        by dn="cn=admin,dc=example,dc=com" write
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be hdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix "dc=debian,dc=org"
```

Everything is working, but that spamming is annoying...
Thanks in advance!

---

