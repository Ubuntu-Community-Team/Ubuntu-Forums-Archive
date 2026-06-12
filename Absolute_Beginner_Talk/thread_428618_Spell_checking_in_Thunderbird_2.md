---
title: "Spell checking in Thunderbird 2"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by MrGreen on 2007-04-30
I have got T2 installed but noticed spell checking is not working.. wondered if it was a bug or I have missed something

TIA

Mr Green

---

### Post by starcraft.man on 2007-04-30
Hmmm, not sure. Maybe there was a problem installing the dictionary, try installing the dictionary you need again.

[Link.]("https://addons.mozilla.org/en-US/thunderbird/browse/type:3")

Then install [this,]("https://addons.mozilla.org/en-US/thunderbird/addon/3993") dictionary switcher.

I haven't heard any particular trouble with the spellchecker.

---

### Post by byronical on 2007-05-08
I had the same problem after upgrading to 2.0

See this link in Mozilla for information on installing the dictionaries.  Installing them directly from the webSite only installs them on Firefox and not Thunderbird

[http://kb.mozillazine.org/Dictionaries]("http://kb.mozillazine.org/Dictionaries")

this link might also be of interest.

[http://kb.mozillazine.org/Thunderbird_2.0_installation_issues]("http://kb.mozillazine.org/Thunderbird_2.0_installation_issues")

---

### Post by beech on 2007-05-09
It appears that the dictionaries from Thunderbird 1.x are not compatible with Thunderbird 2.0.  Also, Thunderbird 2.0 appears to have no dictionary as default.  You have to go to the website and manually download the dictionary you want to your hard drive from:

[https://addons.mozilla.org/en-US/thunderbird/browse/type:3](https://addons.mozilla.org/en-US/thunderbird/browse/type:3)

(right click and "Save Link As..." otherwise it will install it in Firefox)

Then in Thunderbird click on Tools/Add-ons and then install the file you have just downloaded.

Hope this helps!

William

---

### Post by mifi on 2007-06-06
> **beech said:**
> You have to go to the website and manually download the dictionary you want to your hard drive from:

[https://addons.mozilla.org/en-US/thunderbird/browse/type:3](https://addons.mozilla.org/en-US/thunderbird/browse/type:3)

(right click and "Save Link As..." otherwise it will install it in Firefox)

Then in Thunderbird click on Tools/Add-ons and then install the file you have just downloaded.

I have tried several directions, including this one. I have installed a language pack using synaptic, I have dropped a dictionary on the extension manager and I have manually downloaded and installed them.

I have looked in several faq and in the knowledge base of mozilla.

I still cannot get my %^&% thunderbird to offer my language as a choice in the  'preferences/composition/spelling/language'  box. :(

Please help.
mifi

---

### Post by tommie74 on 2007-06-18
Neither have I after having manually installed a dictionary the way described above..

---

### Post by mifi on 2007-06-19
> **tommie74 said:**
> Neither have I after having manually installed a dictionary the way described above..
Well, I have found the problem. It has to do with rights. You have to install with root priviledges.

Open a terminal window and execute:

sudo -H mozilla-thunderbird

Ignore first few setup screens and go straight into the extension manager. Install the languages and exit thunderbird.
Now it should work.

mifi

---

