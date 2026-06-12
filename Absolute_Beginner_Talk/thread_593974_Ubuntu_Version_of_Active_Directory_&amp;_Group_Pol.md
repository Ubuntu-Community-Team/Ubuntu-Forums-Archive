---
title: "Ubuntu Version of Active Directory &amp; Group Policy"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by robinlennox on 2007-10-27
I'm looking to roll out ubuntu to a number of Non-profit organizations... However as the companies are quite large we would need to manage users and computers.

I was wondering if there was an Ubuntu "Active Directory" & "Group Policy" alternative, where i can apply policies to objects and manage them.

Any Ideas?

---

### Post by ddoctor on 2007-10-27
If you're looking specifically for an Active Directory & Group Policy implementation in Linux, the Samba 4 project is looking at exactly that. They have an alpha available from somewhere in [www.samba.org](www.samba.org).

Samba 3 can act as a windows login server, but its quite painful to set up... I've tried with little luck. Easier to shell out for a cheap windows 2k/2k3 license on eBay, then run it on vmware.

If you're in a Linux-only environment, try OpenLDAP for sign-on.

---

### Post by robinlennox on 2007-10-28
What i'm looking for is a system where I can add a computer to a domain controller. Than the domain controller could manager DHCP / DNS. I would also like to have an LDAP/Active Directory Login for computer and user to authenticate with

Once they have authenticated, they will have policy's applied and possible software install when the authentication process has been completed.

I was hoping that a Linux Variant might be available for this very Micro$oft suite of tools.

---

### Post by robinlennox on 2007-10-28
*bump*

Any Ideas????

---

### Post by robinlennox on 2007-10-28
*bump*

Any Ideas???? :confused:

---

