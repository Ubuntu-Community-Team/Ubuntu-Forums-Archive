---
title: "Hotmail on Linux? [Resolved]"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by bobtherocket on 2007-04-18
Is there a way to get Hotmail to work with Thunderbird? I've tried some of the tutorials here, and nothing worked, so was just wondering if there was something I was missing. I've tried hotway and  a few fixes with that so far...:P

---

### Post by aysiu on 2007-04-18
[There are a few packages in the repositories that might help](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=hotmail&searchon=name&subword=1&version=all&release=all):
[i]gotmail
hotsmtp
hotway[/i]

---

### Post by delphiguy on 2007-04-19
Wow, thanks did'nt thought that this is possible for non-outlook mail agents.
Is there a way for me to do the same in Yahoo Mail?

---

### Post by aysiu on 2007-04-19
I don't know, but you might want to look at *fetchyahoo* or YPops!,

---

### Post by Kevin Funnell on 2007-04-19
Bobtherocket,

Not sure if you are useing Mozilla Firefox as there is an extension that allows you to have all your mail feed in the one place works well with my dial-up services Bigpond & Gmail in my part of the world.   The extension is:  [COLOR="Blue"]Australian-Radio Toolbar  1.0.1.29,[/COLOR] (ver) there maybe other -Radio-Toolbars for your neck of the world.   I only use the Search, News feeds, Mail notification, Pricacy & Weather all parts work well.

Hope this helps,
Old Kevin

---

### Post by beameup on 2007-04-19
Right here:  [http://webmail.mozdev.org/index.html](http://webmail.mozdev.org/index.html)

---

### Post by bobtherocket on 2007-04-19
Ah, I used the webmail on Windows, but when I tried it here, never worked...Then I realized how...I never made the ports match up between WebMail and my account settings...Newbie mistake....Thank you!

---

### Post by beameup on 2007-04-19
Yea, I should have added "click the forum link for setup instructions" . Glad you got it working.

[http://forums.mozillazine.org/viewtopic.php?t=439333](http://forums.mozillazine.org/viewtopic.php?t=439333)

> This thread now replace the previous "Hotmail / Yahoo Extension" thread which has become unmanageable at 143 pages.


This extension will let thunderbird dowload email from hotmail/yahoo accounts.

You will need at least two of the following extensions
WebMail (required)
Hotmail (optional)
Yahoo (optional)
Lycos (optional)
Mail.Com (optional)
GMail (optional)
Libero (optional)
AOL (optional)


Mail account setup
servername : localhost
username : [email]username@yahoo.com[/email]


POP Setup
port : 110 (default)

SMTP Setup
port : 25 (default)



Setup Instructions - by WildcatRay

With your browser (I assume it is Firefox), go to this page, go to "Bookmarks > Bookmark This Page..." and save this so you can always get to the main WebMail page.

Click on "Downloads" on the left-hand side of the page. Download the WebMail, Hotmail and Yahoo extensions from this page. (Right-click the hyper links and then click on "Save Link As..." and save each of the extensions (the .xpi files) to a convenient folder. Desktop would be easiest for this.)

Open your Thunderbird and then "Tools > Extensions" to open your Extensions window. Click on the "Install" button and then "Desktop" on the left-hand side of the window that opens. Look for the WebMail extension. Click on it and then on the "Open" button. Follow any additional prompts to install the WebMail extension.

Repeat this same sequence for the Hotmail and Yahoo extensions you downloaded along with the WebMail extension.

Restart Thunderbird to complete the installation of these extensions.

With Firefox, go back to the WebMail site and click on "Account Setup" also on the left-hand side of the page. Follow the instructions to set up your Hotmail and Yahoo email accounts in Thunderbird.

I hope this helps you set up your accounts.



---

