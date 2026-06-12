---
title: "can't browse the internet"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by ilanxp on 2007-09-09
hi all,

i'm new in ubuntu and i have a problem with firefox : i can't get internet web pages.
i didn't have this problem with other distros (using firefox) nor with internet explorer on windows.
i do connect to the Gaim messenger and all ping commands get good replies, traceroute too.

is there any ubuntu built-in firewall that could block ?

thanks for your help!

Narf

---

### Post by rickycodie on 2007-09-09
try opening the terminal and typeing "firefox" into it. post results here.

---

### Post by toasterofirony on 2007-09-09
Have you tried other web browsers? Opera, Epiphany et al?

---

### Post by samkline on 2007-09-09
> **ilanxp said:**
> hi all,

i'm new in ubuntu and i have a problem with firefox : i can't get internet web pages.
i didn't have this problem with other distros (using firefox) nor with internet explorer on windows.
i do connect to the Gaim messenger and all ping commands get good replies, traceroute too.

is there any ubuntu built-in firewall that could block ?

thanks for your help!

Narfcould it be a DNS problem?

run [FONT="Courier New"]nslookup ubuntu.com[/FONT] in the terminal and post the output here.

---

### Post by ilanxp on 2007-09-09
running firefox from a terminal didn't change anything and there are no dns problems as i mentionned before...

any other idea?

---

### Post by Sef on 2007-09-09
How are you connected to the internet?

---

### Post by &amp;wP*!) on 2007-09-09
Also, don't try the same web page you want to access. Maybe the web page is not accessible.

---

### Post by ilanxp on 2007-09-09
i'm in a lan behind a router, but i didn't have this pb with fedora nor mandriva, only with ubuntu so this a local problem... the same thing happens with other browsers. is there any built-in firewall in ubuntu? if yes how can i configure/disable it ?

thanks again

Narf

---

### Post by arai on 2007-09-09
go to firefox location bar and type 

```
about:config
```

there, I changed 

```
network.dns.disableIPv6
```to "true" and it worked for me.

---

### Post by Gone fishing on 2007-09-09
Do you connect through a proxy? If so you have to add these to Firefox (edit > preferences > advanced >network >settings) as well as in system preferences.

Sorry if this is so obvious and you've already done it.

---

### Post by toasterofirony on 2007-09-09
> **ilanxp said:**
> i'm in a lan behind a router, but i didn't have this pb with fedora nor mandriva, only with ubuntu so this a local problem... the same thing happens with other browsers. is there any built-in firewall in ubuntu? if yes how can i configure/disable it ?

thanks again

Narf

As far as firewalls go, theres nothing in a native set-up that would block port 80. 

Have you tried something else that accesses port 80? Like getting a new package from the repos?

---

### Post by ilanxp on 2007-09-10
well it still doesn't work. ipv6 is disabled in firefox and i'm not behind any proxy. it doesn't work with other browsers either.

another idea guys?

---

### Post by ilanxp on 2007-09-11
Hi all,

i installed again ubuntu and the problem persists...
still can't browse.

This is the error message i get :
[B]
The connection was reset[/B]

**The connection to the server was reset while the page was loading.**

blablabla...


Any idea ? i'm gettin' crazy!!:mad::mad::mad:

---

