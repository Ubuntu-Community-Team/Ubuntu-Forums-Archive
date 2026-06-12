---
title: "Are we safe from this in Ubuntu?"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Officer Dibble on 2008-01-17
I've just been reading this on the BBC website, are we safe from it while using Ubuntu?

[http://news.bbc.co.uk/1/hi/technology/7193993.stm](http://news.bbc.co.uk/1/hi/technology/7193993.stm)

---

### Post by SOULRiDER on 2008-01-17
Yes

---

### Post by bodhi.zazen on 2008-01-17
I am not sure we are "safe" on Linux. It depends on the script, we could be vulerable it is a java script.

There is insufficient information on that link.

I advise you use noscript, block all sites, and allow only the sites you trust.

+1 on adblock extensions.

---

### Post by Hospadar on 2008-01-17
Judging by the:> The attack exploits loopholes in many Windows programs I'd say we probably arn't at rist =P

---

### Post by Ex-windows on 2008-01-17
> **bodhi.zazen said:**
> I am not sure we are "safe" on Linux. It depends on the script, we could be vulerable it is a java script.

There is insufficient information on that link.

I advise you use noscript, block all sites, and allow only the sites you trust.

+1 on adblock extensions.'

 How exactly do you do this?? ie use noscript and/or +1 on adblock ext.:confused:

---

### Post by MikeyXX on 2008-01-17
If a hole in opensource is what allows this vulnerability, it wouldn't be difficult to believe that a hole in opensource on our end could expose us as well.

Don't feel too safe, it could be your undoing.

---

### Post by PeterJS on 2008-01-17
Adblock:
[https://addons.mozilla.org/en-US/firefox/addon/10](https://addons.mozilla.org/en-US/firefox/addon/10)
Noscript:
[https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)

And to go all out set your cookies to: Ask Me everytime.

---

### Post by Ex-windows on 2008-01-17
> **PeterJS said:**
> Adblock:
[https://addons.mozilla.org/en-US/firefox/addon/10](https://addons.mozilla.org/en-US/firefox/addon/10)
Noscript:
[https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)

And to go all out set your cookies to: Ask Me everytime.
Thanks for this info I have both installed now and WOW I will have to use the Thanks button later cuz it won't let me lol:lolflag:

---

### Post by bodhi.zazen on 2008-01-17
For cookies : 

Firefox options -> Privacy tab

Copy the Ubuntu url from your browser : [http://ubuntuforums.org/](http://ubuntuforums.org/)

Go to "Cookies" -> click the "Exceptions" button -> paste ubuntu url -> click "Allow for session"

=========

For Java (to allow use of "thanks" and other features on Ubuntu)

Right click on the NoScript icon -> Allow Ubuntu.com

=========

Repeat for bank or other web sites (sometimes you need to allow multiple url , one for the main site and one for the log-in screen).

=========

Install Safe History

[https://addons.mozilla.org/en-US/firefox/addon/1502](https://addons.mozilla.org/en-US/firefox/addon/1502)

=========

Set a master password in password manager (password protects your passwords, otherwise anyone can click "View passwords"

=========

Welcome to a more secure Firefox. Yea , it takes a few minutes to whitelist your web sites, but once you are set up you are done & more secure.

---

### Post by SOULRiDER on 2008-01-18
Nice post bodhi, maybe you should write a Securing Firefox howto for the Tutorials and Tips forums :)

---

### Post by biohypnotix on 2008-01-18
Nothing is 100% safe from malware and social engineering no matter what others say. For Firefox these are my must have add-ons for security, privacy, and disabling annoying web "features."

NoScript - [https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)
CookieSafe - [https://addons.mozilla.org/en-US/firefox/addon/2497](https://addons.mozilla.org/en-US/firefox/addon/2497)
SafeHistory - [https://addons.mozilla.org/en-US/firefox/addon/1502](https://addons.mozilla.org/en-US/firefox/addon/1502)
Adblock Plus - [https://addons.mozilla.org/en-US/firefox/addon/1865](https://addons.mozilla.org/en-US/firefox/addon/1865)
Web Developer - [https://addons.mozilla.org/en-US/firefox/addon/60](https://addons.mozilla.org/en-US/firefox/addon/60)

---

### Post by g7kse on 2008-01-18
I read the same thing this lunchtime and had the saem question....Many thanks to all who have helped answer so quickly and concisely

Wheres the button for thank yous?

---

### Post by bodhi.zazen on 2008-01-18
> **SOULRiDER said:**
> Nice post bodhi, maybe you should write a Securing Firefox howto for the Tutorials and Tips forums :)

LOL, done :

[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

---

### Post by chach man on 2008-01-18
I believe you would be safe from this specific attack but if someone wrote one specifically for *nix users and could get in I think we could experience some problems.

---

### Post by st33med on 2008-01-18
Yes, we are protected. However, other people aren't, so, if you email them after you visit the poison ed site, they might get infected.

---

### Post by monte48lowes on 2008-01-18
Does anyone have a link to one of these sites... I'm curious what would happen.....

Mike

---

### Post by eolson on 2008-01-18
I visit SARC's site fairly regularly and this is the very first time in many years that I have seen Linux mentioned.  I think we're making the big time (unfortunately).


[http://www.symantec.com/norton/security_response/writeup.jsp?docid=2008-011517-3725-99](http://www.symantec.com/norton/security_response/writeup.jsp?docid=2008-011517-3725-99)

---

### Post by JoshuaRL on 2008-01-18
> **st33med said:**
> Yes, we are protected. However, other people aren't, so, if you email them after you visit the poison ed site, they might get infected.

Really?  I haven't found too much info on this yet, but I thought it would have to be able to infect you to be able to pass it on.  From that page on Symantec said it was an exploit of the browser to send you to an infected site.  But to get anything from the site, you would need to be exploitable other than the browser pointing you there.  So if I understand it right, we couldn't pass that on.

Please correct me if I understand that wrong.

---

### Post by eolson on 2008-01-19
It's easy to protect yourself from this one.   It needs javascript (not java,  but javascript) to run.  In Firefox

Edit > Preferences > Content

and uncheck the enable javascript box.

If your running another browser just hunt down javascript and disable it.

---

