---
title: "Web Proxy with Windows Network"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by _Tilt_ on 2006-12-08
Hi everyone,

Ive setup an Ubuntu Server to provide for a specific role and am havind some difficulties in understanding elements that I need to achieve my goal.  My intention is to create an Ubuntu server that will act as a web proxy/content filter to my users and i would like it to work within the Windows Network that has already be setup here.  From what i have found, i will have to do the following:

Install Ubtuntu LTS 6.06 (Dapper Drake) Minimal Server Install.
Install OpenSSH, Kerberos, Squid and Samba (with winbind).
Added the machine as an AD member server to the domain (samba).
Enabled Username/Group lookups (winbind)
Get the machine working as a proxy via our LEA's proxy server (Squid)
Enabled NTLM authentication (Squid + Winbind)
Configure Dansguardian so it goes through squid (for the NTLM auth).
Updated the blacklists + phraselists and told Dansguardian to use them.

I know its alot so any help would be appreciated.  Installing the server is fine as there are no problems during install but the rest is difficult to get a grasp of.  For example I've installed OpenSSH but I havent configured it in anyway,it does work though, just that i dont know what to do if its not, another example is samba, kerberos, squid... have different packages that are associated to them but what are they and what do they do.

I have searched the forum and have found elements that relate to what i want to do but when if i get a problem, im stumped and i like to know exactly what a line of code is doing.  As i said any help is welcomed and if i need to do some reading in a certain area im fully willing to do that.

---

