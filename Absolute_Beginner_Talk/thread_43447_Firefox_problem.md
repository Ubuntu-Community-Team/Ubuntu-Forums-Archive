---
title: "Firefox problem"
date: 2005-06-22
forum: Absolute Beginner Talk
---

### Post by dbzsongoku on 2005-06-22
Hi,
I'm having some problems with mozilla firefox.  I'm trying to check my email at webmail.shaw.ca but i get an error message that says Firefox and webmail.shaw.ca  cannot communicae securely because they have no common encryption algorithms.  Another minor problem that I have is that I can't set my default start up page.  I went to edit->preferences and set my starting page to [http://www.google.ca](http://www.google.ca) but firefox still starts at [http://www.microsoft.com](http://www.microsoft.com). Any help would be great.  Thanks

---

### Post by dbzsongoku on 2005-06-22
[QUOTE=dbzsongoku]Hi,
I'm having some problems with mozilla firefox.  I'm trying to check my email at webmail.shaw.ca but i get an error message that says Firefox and webmail.shaw.ca  cannot communicae securely because they have no common encryption algorithms.  Another minor problem that I have is that I can't set my default start up page.  I went to edit->preferences and set my starting page to [http://www.google.ca](http://www.google.ca) but firefox still starts at [http://www.microsoft.com](http://www.microsoft.com). Any help would be great.  Thanks[/QUOTE]
 nvm my second problem.  Still can't get the webmail.shaw.ca site to work though.

---

### Post by ChrisTheGeek on 2005-06-22
Are you sure this is a problem with Firefox on Ubuntu?  It sounds like 'webmail.shaw.ca' does not comply to standards and may rely on Microsoft IE specific features.

Have you tried the site with Firefox on Windows?

---

### Post by dbzsongoku on 2005-06-22
[QUOTE=ChrisTheGeek]Are you sure this is a problem with Firefox on Ubuntu?  It sounds like 'webmail.shaw.ca' does not comply to standards and may rely on Microsoft IE specific features.

Have you tried the site with Firefox on Windows?[/QUOTE]
 Yeah.  I tried it with firefox on my desktop pc with windows and it works fine.  This started happening after I reinstalled ubuntu today to fix some problems

---

### Post by everklear on 2005-10-18
[QUOTE=dbzsongoku]Yeah.  I tried it with firefox on my desktop pc with windows and it works fine.  This started happening after I reinstalled ubuntu today to fix some problems[/QUOTE]
Having the same problem here after upgrading to 5.10 (Breezy).
Web mail interface complains about "no common encryption algorithms".
Firefox under Fedora Core 4 and Windows has no problem.

Anyone found a solution for this?

---

### Post by everklear on 2005-10-18
A little bit of more specific "googling" and I have the answer.

I found it on this helpful person's web page:

[URL="http://members.shaw.ca/Limulus/ubuntu.html"]
http://members.shaw.ca/Limulus/ubuntu.html[/URL]

In summary, to fix this specific issue, enter "about:config" in the url box of Firefox, find the setting "security.ssl3.rsa_rc4_40_md5" and double-click it to enable support for that type of ssl encryption.

---

