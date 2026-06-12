---
title: "How to remove installed dictionaries from firefox?"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2008-04-21
Hello,

I've installed an automatic language recognition add-on in firefox. However, since I also got South African English installed it always says that is the one when I am writing in English (I don't know why).

I want to remove some dictionaries from firefox. How can I do this?

---

### Post by Kevbert on 2008-04-21
Just go to Tools, Add-ons, Languages, Click on the language you don't want and now select Disable.
You'll then need to close and then restart Firefox.  Hopefully when you click on the disabled language you'll now have the option to uninstall.

---

### Post by kramer65 on 2008-04-21
Yes I thought that as well. It contains several dozens of languages but the onese which I see under languages when I right click in a page are not there. The South African English for example is not there.

Is there any way of deinstalling and installing firefox again? How would I do that?

---

### Post by Kevbert on 2008-04-21
Hi again.  I assume you mean the dictionaries here: [https://addons.mozilla.org/en-US/firefox/browse/type:3]("https://addons.mozilla.org/en-US/firefox/browse/type:3")
Just for fun I installed the Welsh language and a German dictionary.  The language add-on is found under languages, and the dictionaries are stored under Extensions.  If you right click the dictionary you don't want there is an uninstall option in the pull down list.  A restart will remove it. 
Sorry if this doesn't help, you may have to perform a restart.
Best of luck.

---

### Post by kramer65 on 2008-04-22
Yes I had a look there as well. But it doesn't say South African English either. Just Spanish and Dutch whereas I can chose the following from my right click in the browser;

es-ES
nl
en_GB
en-GB
en_US
en-US
en_ZA

I just want to get rid of the American and South African English. Can't I uninstall and reinstall FF as a whole?

Any tipson this are more than welcome!

---

### Post by Kevbert on 2008-04-22
Sorry about that, but I meant that it looks like a re-install is your only option.  I believe that Firefox 3 beta will be coming out on the full release of Hardy Heron on Thursday.

---

### Post by lobner on 2008-05-30
> **Kevbert said:**
> Just go to Tools, Add-ons, **Languages**, Click on the language you don't want and now select Disable.
You'll then need to close and then restart Firefox.  Hopefully when you click on the disabled language you'll now have the option to uninstall.

Where do you find this 'Languages' option or button?

Inside my Add-ons dialog, there are only Extensions and Themes, no Languages... :confused:

---

### Post by finomeno on 2008-06-30
Make sure Firefox is not running. Go to /usr/lib/firefox-3.0/dictionaries or /usr/lib/firefox/dictionaries, whichever is your case, and remove the .dic and .aff files you do not need. Start Firefox. Enjoy (-:

---

