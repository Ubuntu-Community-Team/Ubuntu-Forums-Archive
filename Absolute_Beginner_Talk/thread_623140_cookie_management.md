---
title: "cookie management"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by buccaneere on 2007-11-25
In yer firefox browser cookie blocker, how do ya' block cookies from ads.doubleclicknfillyercomputerboxwithjam.com, that clog 'n' bog yer browser???

Thanks!

---

### Post by LaRoza on 2007-11-25
Edit->Preference->Security

You can block sites in that section, have cookies deleted when you close firefox, or not use them at all.

---

### Post by buccaneere on 2007-11-25
> **LaRoza said:**
> Edit->Preference->Security

You can block sites in that section, have cookies deleted when you close firefox, or not use them at all.

Yeah - I found 'exceptions' to allowed cookies, but what gets entered into the dialogue box, to block? The name of the cookie folder? Or the name of the cookie file *inside of *the cookie folder?

Thanks........

---

### Post by Taboo Mirage on 2007-11-25
If you read the dialogue, it states:

"You can specify which web sites are always or never allowed to use cookies.  Type the exact address of the site you want to manage and then click Block, Allow For Session, or Allow."

So, using Google as a pure example:

In the dialogue, enter:

google.com 

And click "Block".  Any pages from google.com will now not be able to set cookies on your machine.

You may wish to set the "Keep Until" box to "Ask Me Every Time", which will provide you absolute control of incoming cookies.  Every time you visit a site with this setting which tries to set a cookie, you can then choose whether to allow or deny it.  You have an option in that box to "always accept" or "always deny" cookies from the site in question.  It can take awhile to get this configured but after you've browsed to the main sites you visit and set them up you shouldn't get too many prompts from that moment forward.

---

### Post by buccaneere on 2007-11-25
> **Taboo Mirage said:**
> If you read the dialogue, it states:

"You can specify which web sites are always or never allowed to use cookies.  Type the exact address of the site you want to manage and then click Block, Allow For Session, or Allow."

So, using Google as a pure example:

In the dialogue, enter:

google.com 

And click "Block".  Any pages from google.com will now not be able to set cookies on your machine.

You may wish to set the "Keep Until" box to "Ask Me Every Time", which will provide you absolute control of incoming cookies.  Every time you visit a site with this setting which tries to set a cookie, you can then choose whether to allow or deny it.  You have an option in that box to "always accept" or "always deny" cookies from the site in question.  It can take awhile to get this configured but after you've browsed to the main sites you visit and set them up you shouldn't get too many prompts from that moment forward.

Understood... But most sites have cookies that MUST be loaded to view the page (1st party cookies), and they also have 3rd party cookies, which are NOT necessary to load, to view the page. Like cookies from ads.doubleclick.net.

In yer example, if ya' just put google.com on the block list, ya' can't view the page. Right?


EDIT: I just tried it with google.com. Block google.com. Seems like the page loads. Cool. I'm diggin' this.

---

### Post by Taboo Mirage on 2007-11-25
Well, you can view Google specifically without cookies but I can see what you're trying to get at here. 

If you specifically entered doubleclick.net as a "block" entry, then you'd be okay.  It would refuse the third party cookies loaded from the advertizers while still accepting the first party cookies that you need to view the page or retain user settings.  Third party cookies being blocked will not impact your ability to use the site, providing the first party cookies were permitted.

---

### Post by LaRoza on 2007-11-25
[https://addons.mozilla.org/en-US/firefox/addon/60](https://addons.mozilla.org/en-US/firefox/addon/60)

Under cookies, you can disable third party cookies.

---

